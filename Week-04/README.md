# Mediroza Hospital — Web Application Penetration Testing Assessment

This repository contains the full methodology, technical walkthrough, vulnerability analysis, and proof-of-concept evidence for an authorized **Black-Box Web Application Penetration Test** conducted on the Mediroza General Hospital patient portal.

---

## Executive Summary

As part of the **NETWORKWALKS Cybersecurity Training (Batch B082 - Week 4)**, an end-to-end security assessment was performed against the Mediroza General Hospital web infrastructure (`https://medirozahospital.com`). 

The primary goal was to evaluate the application's attack surface, bypass authentication controls via input manipulation, crack document encryption keys, analyze hidden file metadata, and identify critical database exposures.

---

## Authorization & Disclaimer

> **Notice:** This security assessment was conducted within a strictly authorized and controlled lab environment provided by **NETWORKWALKS**. All testing procedures follow ethical hacking principles. Unethical or unauthorized application of these techniques is illegal.

---

## Assessment Objectives & Scope

* **Reconnaissance:** Uncover hidden endpoints and restricted directories via web application crawlers and robot instructions.
* **Authentication Testing:** Assess login interfaces for user enumeration and SQL Injection (SQLi) vulnerabilities.
* **Document Security Analysis:** Evaluate PDF encryption algorithms and execute dictionary attacks on protected lab reports.
* **Deep Reconnaissance:** Extract file metadata to locate legacy backups and sensitive database dumps.
* **Risk Reporting:** Document findings with severity ratings and actionable mitigation strategies.

---

## Technical Methodology & Execution Phase

### Phase 1: Reconnaissance & Initial Access

#### 1. Endpoint Discovery via `robots.txt`
Inspecting the application's `/robots.txt` file revealed hidden directories disallowed for web crawlers, exposing `/patient/`, `/staff/`, and `/old/`.

![Robots.txt Reconnaissance](01_recon_robots_txt.png.png)

#### 2. Username Enumeration Vulnerability
The login endpoint (`/patient/login.php`) provided explicit and inconsistent error responses, allowing an attacker to enumerate valid accounts.

* **Invalid Username Attempt:** Displays `Username not found`.
  ![Invalid Username Testing](02_user_enum_invalid_username.png.png)

* **Testing Valid Account:**
  ![Testing Admin User](03_user_enum_testing_admin.png.png)

* **Valid Account Confirmation:** Entering `admin` with a dummy password returns `Incorrect password`, confirming `admin` is a registered user.
  ![Incorrect Password Error](04_user_enum_incorrect_password.png.png)

#### 3. SQL Injection Login Bypass
Inputting a single quote (`admin'`) in the username field broke the backend database query, confirming SQL injection. Supplying `admin'` as the username bypassed authentication completely, granting full access to the patient portal and revealing encrypted reports (`patient_report_1.pdf`, `patient_report_2.pdf`, `patient_report_3.pdf`).

---

### Phase 2: PDF Encryption & Hash Recovery

The downloaded patient lab reports were protected with 128-bit encryption. Password hashes were extracted (`$pdf$...`) and subjected to dictionary attacks using custom and built-in wordlists.

#### 1. Report 1 Password Recovery
* **Password:** `123456`
  ![Report 1 Cracked](05_crack_report1_password.png.png)

#### 2. Report 2 Password Recovery
* **Password:** `password`
  ![Report 2 Cracked](06_crack_report2_password.png.png)

#### 3. Report 3 Password Recovery (Extended Dictionary Attack)
Default wordlists failed on the third report. Switching to the specialized **JTR wordlist** successfully recovered the complex key string.
* **Password:** `!@#$%^&`
  ![Report 3 Cracked](07_crack_report3_custom_wordlist.png.png)

---

### Phase 3: Deep Reconnaissance & Exploit Chaining

1. **Decryption:** The protected PDF was decrypted using `qpdf`:
   ```bash
   qpdf --password='!@#$%^&' --decrypt patient_report_3.pdf report3_open.pdf
