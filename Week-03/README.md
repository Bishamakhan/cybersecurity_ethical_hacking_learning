# 🔒 Password Auditing & Cracking - Practical Lab Write-ups

Comprehensive documentation covering practical modules from the **NetworkWalks Academy Cybersecurity & Ethical Hacking** training program. This repository details offline and online dictionary attack methodologies against password-protected PDF files using industry-standard tools and web-based applications.

---

> ⚠️ **Disclaimer & Ethics Note:**  
> All activities documented in this repository were executed in an isolated lab/VM environment using sample training files provided directly by NetworkWalks Academy (`My Locked PDF1.pdf` / `networkwalks_flag1.pdf`). Password cracking tools should **ONLY** be executed on files, systems, or assets that you own or have explicit written permission to test.

---

## 📌 Technical Overview

Password cracking involves recovering plaintext credentials from encrypted data or hashes. In secured documents (such as PDF, ZIP, or Office files), passwords are converted into cryptographic hashes. Security auditors extract these hashes and perform offline dictionary or brute-force attacks to evaluate password strength.

* **Target Artifact:** `My Locked PDF1.pdf` (`networkwalks_flag1.pdf`)
* **File Size:** ~65.2 KB
* **Encryption Scheme:** PDF Encryption Revision 4 (V4) / 128-bit key length
* **Primary Objective:** Extract the document hash, conduct a dictionary-based attack, and verify document unlocking to capture the flag.

---

## 🛠️ Lab 1: Offline Hash Cracking with John the Ripper (JTR) & Johnny GUI

### Objective
Extract the cryptographic hash from the target document and perform an offline dictionary attack using **John the Ripper** and its graphical user interface, **Johnny**, on a Windows host environment.

### Tools Used
* **John the Ripper (Jumbo Build - Windows x64)**
* **Johnny** (GUI Wrapper for John the Ripper)
* **OnlineHashCrack / pdf2john** (PDF Hash Extraction Service)

### Execution Steps
1. **Tool Setup & Path Configuration:**  
   Downloaded John the Ripper (jumbo build) and installed Johnny GUI, pointing Johnny's configuration path to `john.exe` executable inside the extracted run directory.

![johnny_settings_path_config](johnny_settings_path_config.png)

2. **Hash Extraction & Setup:**  
   Uploaded `My Locked PDF1.pdf` to the online extraction service to convert document password protection into a crackable `$pdf$4*...` hash, saved locally as `hash1.txt`.

3. **Loading Hash into Johnny:**  
   Opened Johnny GUI, loaded `hash1.txt`, and confirmed the tool automatically recognized the format as **PDF**.

4. **Executing Attack:**  
   Started the dictionary attack session. John the Ripper tested candidates against the hash and cracked the password.

![johnny_cracked_password](johnny_cracked_password.png)

5. **Verification & Flag Capture:**  
   Opened `My Locked PDF1.pdf`, entered the recovered key `1qaz2wsx`, and successfully unlocked the document to capture the secret flag.

![unlocked_pdf_flag](unlocked_pdf_flag.jpg)

### Findings & Results
* **Recovered Key:** `1qaz2wsx`
* **Captured Flag:** `nw{networkwalks_flag1_jtr_270521_1}`
* **Status:** Success (Access granted)
* **Key Takeaway:** Keyboard pattern passwords like `1qaz2wsx` are vulnerable to rapid dictionary attacks. Utilizing non-pattern, complex passwords is required for robust document security.

---

## 🛠️ Lab 2: Client-Side Web Cracking via NetworkWalks Toolkit

### Objective
Perform hash extraction and dictionary cracking entirely within a web browser using client-side Web Crypto API utilities provided by NetworkWalks.

### Tools Used
* **NetworkWalks Hash Calculator (Browser-based PDF Module)**
* **NetworkWalks Password Cracker (Browser-based Engine)**

### Execution Steps
1. **File Ingestion & Parsing:**  
   Navigated to the PDF tab on the NetworkWalks Hash Calculator and uploaded `My Locked PDF1.pdf`. The tool parsed the document structure locally to output the crackable `$pdf$` hash.

![pdf_hash_extraction](pdf_hash_extraction.png)

2. **Executing Browser Dictionary Attack:**  
   Pasted the hash into the NetworkWalks Password Cracker interface and initiated the attack using the wordlist.

3. **Live Execution Output:**  
   Monitored the console output as candidates were checked sequentially until `1qaz2wsx` matched.

![networkwalks_web_cracker](networkwalks_web_cracker.jpg)

4. **Verification:**  
   Applied the recovered string `1qaz2wsx` to unlock the PDF file and confirm document access.

### Findings & Results
* **Matched Password:** `1qaz2wsx`
* **Recovered Flag:** `nw{networkwalks_flag1_jtr_270521_1}`
* **Key Takeaway:** Modern browser-based tools leveraging Web Crypto APIs can perform efficient offline attacks client-side without sending sensitive hashes or files to remote servers.

---

## 🔗 References & Learning Resources
* NetworkWalks Academy Official Portal: [networkwalks.com](https://www.networkwalks.com)
* John the Ripper Core Documentation & Repositories
