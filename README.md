# cybersecurity_ethical_hacking_learning

Practical cybersecurity and ethical hacking learning environment built for
learning, testing, network configuration, and authorized security exercises.

# Cybersecurity & Ethical Hacking learning Environment

## Overview

This repository documents my hands-on cybersecurity and ethical hacking
learning environment. It includes practical work related to virtualization,
Kali Linux, networking, reconnaissance, vulnerability assessment,
web security, and security testing.

The purpose of this lab is to develop practical cybersecurity skills
in an isolated and authorized environment.

## Lab Objectives

- Build an isolated cybersecurity practice environment
- Configure virtual machines for security testing
- Install and configure Kali Linux
- Configure virtual networking
- Understand IP addressing and connectivity
- Practice reconnaissance and enumeration
- Perform vulnerability assessment in authorized labs
- Study web application security
- Document practical security findings
- Create snapshots for safe experimentation and rollback

## Lab Environment & Specifications

### Virtualization

- Hypervisor: Oracle VirtualBox
- Host Operating System: Windows
- Security Testing OS: Kali Linux
- Network Type: NAT / Host-Only Network
- Purpose: Isolated cybersecurity laboratory

### Tools

- Kali Linux
- Nmap
- Wireshark
- Burp Suite
- Metasploit Framework
- Gobuster
- Netcat
- Python

## Network Configuration

Example private laboratory network:

| Machine | Example IP |
|--------|------------|
| Kali Linux | 10.0.0.2 |
| Target VM | 10.0.0.10 |
| Test VM | 10.0.0.11 |

> These addresses are examples for an isolated lab environment.

## Phase 1 — Kali Linux Setup

### Step 1: Install VirtualBox

Oracle VirtualBox was installed and configured as the virtualization
platform for the cybersecurity laboratory.
![NAT Network Configuration](NAT-work.png)

### Step 2: Install Kali Linux

Kali Linux was installed inside a virtual machine and configured for
security testing and cybersecurity practice.
![Kali Linux Network Configuration](KALI-linux-vm.png)

### Step 3: Configure Network Connection

The virtual machine network adapter was configured using an isolated
laboratory network.
![IP Interface Verification](ip-verification.png)

### Step 4: Verify Network Configuration

Network configuration was verified using standard Linux networking
commands.

Example:

```bash
ip addr
````

The assigned IP address and network interface were checked to confirm
that the virtual machine was connected correctly.
![Connectivity Test](KALI-LINUX-NETWORK.PNG)

### Step 5: Test Connectivity

Connectivity between authorized laboratory machines was tested.

Example:

```bash
ping 10.0.0.10
```

The test was used to verify communication between machines inside the
controlled lab environment.


## Virtual Machine Snapshots

Snapshots were created after major configuration stages.

Recommended snapshots:

* Fresh OS installation
* Network configuration completed
* Kali Linux configured
* Target machine configured
* Pre-testing state

Snapshots allow the laboratory environment to be restored to a known
working state after experiments.

## Reconnaissance & Enumeration

Authorized laboratory systems can be examined using tools such as Nmap.

Example:

```bash
nmap -sV 10.0.0.10
```

The purpose of this activity is to understand network discovery,
service enumeration, and basic security assessment techniques.

## Web Security

The laboratory can also be used to study common web application
security concepts, including:

* Authentication security
* Input validation
* SQL Injection concepts
* Cross-Site Scripting (XSS)
* Access control
* Security headers

All testing is performed only against intentionally vulnerable
applications or systems for which authorization has been provided.

## Practical Work

This repository will contain documentation, screenshots, commands,
lab results, and security observations from my cybersecurity learning.

Future practical projects will be added as separate sections.

## Learning Outcomes

Through this laboratory I aim to develop practical skills in:

* Linux
* Networking
* Cybersecurity
* Ethical Hacking
* Vulnerability Assessment
* Web Security
* Network Security
* Security Tools
* Technical Documentation

## Disclaimer

This repository is intended for educational and authorized cybersecurity
testing only.

All security testing must be performed against systems, applications,
networks, CTFs, or laboratories where explicit permission has been
provided.

I do not support unauthorized access, disruption, data theft, or illegal
activity.

## Author

**Bishamakhan**

Cybersecurity Enthusiast | Interested in Cybersecurity, Ethical Hacking,
Networking and Security Research

## References

* OWASP Web Security Resources
* Kali Linux Documentation
* Nmap Documentation
* Wireshark Documentation
* VirtualBox Documentation

````
