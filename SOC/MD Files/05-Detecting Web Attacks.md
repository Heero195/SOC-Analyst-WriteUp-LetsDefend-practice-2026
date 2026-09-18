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
---

## 4) How Web Applications Work
# Web Application Architecture & The HTTP Protocol

## Overview of the HTTP Protocol
- **Communication Model:** Client-Server architecture; the client sends an HTTP request, and the web server returns an HTTP response.
- **Network Layer:** Operates at the application layer (**Layer 7 - Application**) of the OSI model, on top of underlying protocols such as Ethernet, IP, TCP, and SSL/TLS.

<img width="528" height="368" alt="image" src="https://github.com/user-attachments/assets/cf4b3cb2-288d-4eb8-b6f5-2d1cc295a3e1" />


---

## HTTP Request Structure
Consists of three main components, with an empty line separating the headers from the body:

<img width="817" height="173" alt="image" src="https://github.com/user-attachments/assets/568f299a-373d-48e6-be63-151c1d6ebd49" />


### Request Line
- **HTTP Method:** Standard methods such as GET, POST, etc.
- **Requested Resource:** The path to the requested resource (e.g., `/` indicates the root/homepage).

### Key Request Headers
- `Host`: Specifies the domain name of the target web server.
- `User-Agent`: Details the client browser and operating system (frequently examined to identify automated vulnerability scanners).
- `Cookie`: Stores session state data, allowing users to remain logged in without re-authenticating.
- `Upgrade-Insecure-Requests`: Indicates client preference for an encrypted connection via SSL/HTTPS.
- `Accept`: Content types the client can process.
- `Accept-Encoding`: Compression algorithms supported by the client.
- `Accept-Language`: Preferred display language of the client.
- `Connection`: TCP connection management (`keep-alive` to maintain persistence or `close` to terminate after delivery).

### Request Message Body
- Contains payload data sent to the server (e.g., authentication credentials, form inputs, or upload parameters via POST).

---

## HTTP Response Structure
Composed of three core elements:

<img width="581" height="373" alt="image" src="https://github.com/user-attachments/assets/5a1ce59e-ada1-4d9d-9aef-3c254a04653c" />


### Status Line
Includes the HTTP protocol version and the response code (**Status Code**):
- `100 - 199`: Informational responses.
- `200 - 299`: Successful operations (e.g., `200 OK`).
- `300 - 399`: Redirection messages.
- `400 - 499`: Client errors (e.g., `403 Forbidden`, `404 Not Found`).
- `500 - 599`: Server errors (e.g., `500 Internal Server Error`).

### Common Response Headers
- `Date`: Timestamp indicating when the response was generated and sent.
- `Server`: Web server software version and underlying operating system (useful for reconnaissance analysis).
- `Last-Modified`: Last modification timestamp of the resource (utilized by caching mechanisms).
- `Content-Type`: MIME type of the returned payload (HTML, JSON, media streams, etc.).
- `Content-Length`: Size of the response payload in bytes.
- `Connection`: Network connection status directives.

### Response Body
- The actual resource returned by the server based on client demand (e.g., HTML source to render, API response datasets, raw files).
<img width="528" height="154" alt="image" src="https://github.com/user-attachments/assets/95a060df-f233-4bdb-802f-a5f9f7b9cae7" />

