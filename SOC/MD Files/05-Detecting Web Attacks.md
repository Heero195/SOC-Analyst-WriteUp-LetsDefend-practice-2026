# 📘 Lecture 5: Detecting Web Attacks

---

## 1) Introduction

## 📌 Overview

What Are Web Attacks?
- **Concept:** Web applications provide services to users through a web browser interface (e.g., Google, Facebook, and YouTube web versions).
- **Significance:** They serve as the direct interface to the internet for most organizations.
- **Key Statistic:** An Acunetix study shows that **75% of all cyber attacks** target the web application layer.
- **Consequences:** Attackers can exploit them to gain device access, steal sensitive personal data, disrupt services, and cause severe financial damage.

---

## Core Types of Web Attacks
- **SQL Injection (SQLi):** Injecting malicious SQL queries to manipulate, modify, or extract data from the database.
- **Cross-Site Scripting (XSS):** Injecting malicious scripts (predominantly JavaScript) that execute in the victim's browser.
- **Command Injection:** Injecting arbitrary operating system commands through the web app to be executed on the host server.
- **IDOR (Insecure Direct Object References):** An access control vulnerability allowing unauthorized access to objects by modifying user-supplied identifiers (IDs).
- **RFI & LFI (Remote/Local File Inclusion):** Exploiting dynamic file inclusion functions to read local system files (LFI) or execute remote malicious files (RFI).
- **File Upload (Web Shell):** Uploading unauthorized malicious executable files to compromise and gain remote administrative control of the server.

---

## Course Learning Objectives
- Master the underlying mechanisms and classifications of major web vulnerabilities (SQL Injection, Command Injection, IDOR, etc.).
- Understand the technical reasoning and motivation behind why attackers select specific attack methods.
- Develop practical skills to recognize, analyze, and detect web attack indicators in real-world environments.

  ---

## 2) Why Detecting Web Attacks Important

```
If we examine the anatomy of an attack, we can clearly see that 
the best scenario is to prevent the attack in its first phase. This is why there are various 
security measures aimed at preventing and detecting threats 
against web applications (WAF, IPS, SIEM rules...).
```
---


## 3) OWASP Overview

- **Definition:** The Open Worldwide Application Security Project (OWASP) is a non-profit foundation dedicated to improving software security.
- **Significance:** It serves as one of the world's most reputable and authoritative resources for web application security.

---

## OWASP Top 10
- Periodically every few years, OWASP releases a list identifying the ten most critical security risks facing web applications.
- The 2021 OWASP Top 10 list includes:
  1. **Broken Access Control:** Failures in enforcing permissions, allowing unauthorized access or privilege escalation.
  2. **Cryptographic Failures:** Flaws related to cryptography, exposing sensitive data due to weak or missing encryption.
  3. **Injection:** Injection flaws where hostile data is sent to an interpreter (e.g., SQLi, Command Injection, LDAP Injection).
  4. **Insecure Design:** Flaws resulting from missing or ineffective security design and architectural patterns.
  5. **Security Misconfiguration:** Improperly configured security controls, default passwords, or overly permissive settings.
  6. **Vulnerable and Outdated Components:** Risks from using unpatched, unsupported, or legacy third-party libraries and dependencies.
  7. **Identification and Authentication Failures:** Flaws in validating user identity, authentication mechanisms, or session management.
  8. **Software and Data Integrity Failures:** Code and infrastructure that do not protect against integrity violations (e.g., untrusted plugins or unverified CI/CD pipelines).
  9. **Security Logging and Monitoring Failures:** Insufficient logging, monitoring, and alerting, leaving attacks undetected in real time.
  10. **Server-Side Request Forgery (SSRF):** A vulnerability that allows an attacker to induce the server-side application to make HTTP requests to an unintended destination.
