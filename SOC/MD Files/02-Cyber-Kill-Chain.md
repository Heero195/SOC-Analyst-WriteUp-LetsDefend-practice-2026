# 📘 Lecture 2: Cyber Kill Chain
---
## 1) Introduction to Cyber Kill Chain

## 📌 Overview
The **Cyber Kill Chain** framework, developed by Lockheed Martin, breaks down a cyber attack into 7 distinct phases. Understanding these phases allows SOC analysts to identify where an attack was detected and stop it before completion.


### Which organization was the Cyber Kill Chain model developed by?
> **ANSWER: Lockheed Martin**
### In what year was the organization that developed the Cyber Kill Chain model founded?
> **ANSWER: 1995**
### In what year was the Cyber Kill Chain model developed?
> **ANSWER: 2011**



## 2) Cyber Kill Chain Steps

```
There are several actions that an attacker can take before, during, and after a successful cyber attack. These actions are sequential, and if the attacker fails at one stage, it is not possible to execute the next step of the cyber attack. The Cyber Kill Chain model divides these stages of attackers into 7 steps. The steps of cyber attacks are depicted in the visual  below:

1.Reconnaissance
2.Weaponization
3.Delivery
4.Exploitation
5.Installation
6.Command & Control (C2)
7.Actions on Objectives

```
## 3) Reconnaissance

## 🔍 Phase 1: Reconnaissance

### 1. Core Concept
* **Definition**: The initial phase (Step 1) of the Cyber Kill Chain focused on gathering target intelligence to map out the attack surface and identify viable entry vectors.
* **Primary Reconnaissance Techniques**:
  * 🕵️ **Passive Reconnaissance**: Indirect intelligence gathering conducted without direct packet interaction with the target's infrastructure (e.g., querying OSINT repositories, Wayback Machine / Web Archives, WHOIS domain data, and social media platforms). The target organization cannot detect passive reconnaissance through connection logs.
  * 🛰️ **Active Reconnaissance**: Direct probing of target assets by transmitting network packets or HTTP requests (e.g., Nmap port scanning, Web Server banner grabbing, directory enumeration). Active reconnaissance leaves observable log footprints on firewalls, WAFs, and IDS/IPS sensors.

---

### 2. Attacker Behaviors vs. Defender (Blue Team) Strategies

| Role | Primary Activities |
|---|---|
| 🥷 **Attacker** | • Fingerprinting operating systems, web servers, and application stack versions.<br>• Scanning public IP ranges, internet-facing assets, and searching for unpatched vulnerabilities.<br>• Harvesting employee emails and org structures from social media for Spear Phishing.<br>• Mapping third-party vendors and supply chain partners. |
| 🛡️ **Defender (Blue Team / SOC)** | • Performing external Penetration Testing and OSINT audits to fix information disclosures.<br>• Monitoring Threat Intelligence feeds for leaked credentials and corporate data dumps.<br>• Tearing down sensitive internal documents accidentally indexed on public search engines.<br>• Deploying Firewall, WAF, and IDS rules to monitor, alert, and rate-limit scanning traffic.<br>• Implementing rigorous vulnerability management and timely patch deployment (Zero-day / N-day). |

---

### 📝 Quiz Answers & Explanations

* **Question 1**: What is the step in the Cyber Kill Chain model where the information gathering takes place?
  * **Answer**: `Reconnaissance`
* **Question 2**: What is the number of distinct actions taken during the "Reconnaissance" phase in the scenario?
  * **Answer**: `2`
  * **Explanation**: In the APT38 real-world attack scenario, only the first 2 actions occur in the Reconnaissance phase: **(1)** Gathering target intelligence over several days via website reconnaissance, and **(2)** Discovering vulnerability CVE-2019-0604 on Microsoft SharePoint. (Action 3 corresponds to Exploitation, and Action 4 corresponds to Installation).

### What is the step in the Cyber Kill Chain model where the information gathering takes place?
> **ANSWER: Reconnaissance**

###  The Real-life attack Scenario items above explain an aspect of an actual cyber attack. Based solely on this information, what is the number of distinct actions taken during the "Reconnaissance" phase, which is the first step of the Cyber Kill Chain?
> **ANSWER: 3**


## 4) Weaponization

## ⚔️ Phase 2: Weaponization

### 1. Core Concept
* **Definition**: The second phase (Step 2) of the Cyber Kill Chain. Adversaries utilize intelligence gathered during Reconnaissance to craft, customize, or select appropriate exploits, malware payloads, and malicious delivery scripts.
* **Key Characteristic**: **No activity occurs on the victim's infrastructure yet.** All preparation and weaponization activities take place entirely on adversary-owned infrastructure, making this phase invisible to victim monitoring tools and logs.

---

### 2. Attacker Behaviors vs. Defender (Blue Team) Strategies

| Role | Primary Activities |
|---|---|
| 🥷 **Attacker** | • Writing or customizing malware payloads (Ransomware, Trojans, Infostealers).<br>• Developing exploit payloads targeting specific unpatched software vulnerabilities.<br>• Crafting social engineering assets (Phishing email templates, weaponized Office docs with malicious macros).<br>• Selecting and packing optimal tooling to bypass anticipated security controls. |
| 🛡️ **Defender (Blue Team / SOC)** | • *Cannot directly block* payload creation on adversary infrastructure.<br>• Conducting routine vulnerability assessments to eliminate exploitable entry points.<br>• Enforcing rapid software and OS security patching.<br>• Utilizing Threat Intelligence feeds to study emerging attack tools and proactively write YARA/Sigma detection rules. |

---

### 📝 Quiz Answers & Scenario Breakdown

* **Question**: How many separate activities were performed in the "Weaponization" phase in the scenario?
  * **Answer**: `2`

#### 🔬 Complete Scenario Activity Mapping

| Activity # | Scenario Event Description | Cyber Kill Chain Phase |
|---|---|---|
| **1** | Target employee email addresses were collected. | **Reconnaissance** |
| **2** | A phishing email template was generated. | **Weaponization** |
| **3** | A Word document titled `Salaries.docx` containing malicious macro code was created. | **Weaponization** |
| **4** | The prepared phishing email was transmitted to victims. | **Delivery** |
| **5** | The email was viewed and the attachment was downloaded by the user. | **Delivery** |
| **6** | The document was opened and macro code execution occurred. | **Exploitation** |
| **7** | Ransomware payload was installed and executed on the host. | **Installation** |



## 5) Delivery
## 📦 Phase 3: Delivery

### 1. Core Concept
* **Definition**: The third phase (Step 3) of the Cyber Kill Chain. This phase marks the **very first interaction** between the adversary and the victim environment.
* **Adversary Objective**: Successfully transmit weaponized artifacts (malware payloads, malicious links, exploit files) to the target endpoint or corporate network.

---

### 2. Attacker Vectors vs. Defender (Blue Team) Controls

| Role | Delivery Vectors / Defensive Controls |
|---|---|
| 🥷 **Attacker** | • Transmitting emails with weaponized attachments or credential phishing URLs.<br>• Distributing malicious links and payloads over social media / messaging apps.<br>• Hosting drive-by download sites or executing Water-Hole attacks on industry websites.<br>• Direct file uploads to exposed web servers or cloud storage repositories.<br>• Physical Delivery: Dropping weaponized USB drives in corporate parking lots or office areas (USB Drop Attack). |
| 🛡️ **Defender (Blue Team / SOC)** | • Deploying Email Security Gateways (enforcing SPF, DKIM, DMARC, anti-phishing filters).<br>• Automated attachment inspection using Antivirus engines and Cloud Sandboxes.<br>• Conducting regular Security Awareness Training for organization staff.<br>• Restricting removable storage devices via Group Policy Objects (GPO USB restriction).<br>• Monitoring Firewall, Web Proxy logs, and behavioral network anomaly detection. |

---

### 📝 Quiz Answers & Scenario Analysis

* **Question 1**: According to the Attack Scenario items above, how many different actions were performed in the "Delivery" phase?
  * **Answer**: `2`
  * **Explanation**: **Action 6** (Dropping malicious USB drives on the sidewalk near company premises) and **Action 7** (Employee picking up and plugging the USB into an internal corporate host).
* **Question 2**: How many separate activities were performed in the "Weaponization" phase in this scenario?
  * **Answer**: `2`
  * **Explanation**: **Action 4** (Using Metasploit to backdoor a legitimate `putty.exe` binary) and **Action 5** (Copying the generated backdoor to multiple USB drives).

---

#### 🔬 Complete USB Attack Scenario Breakdown

| Activity # | Scenario Event Description | Cyber Kill Chain Phase |
|---|---|---|
| **2, 3** | Shodan infrastructure scanning and OSINT Windows OS enumeration. | **Reconnaissance** |
| **4, 5** | Embedding payload into `putty.exe` and loading onto multiple USB drives. | **Weaponization** |
| **6, 7** | Dropping USBs near corporate offices and employee plugging USB into company PC. | **Delivery** |
| **8, 9** | Executing backdoored `putty.exe` and triggering a reverse shell connection. | **Exploitation** |
| **10** | Creating a Windows Scheduled Task for persistent system access. | **Installation** |
| **11, 12, 13** | EDR alert triggered, SOC analyst triaged incident and successfully contained host. | **Detection & Response (Defensive)** |


## 6) Exploitation
## ⚡ Phase 4: Exploitation

### 1. Core Concept
* **Definition**: The fourth phase (Step 4) of the Cyber Kill Chain. This stage marks the **activation of malicious code** or the execution of **exploit payloads** targeting hardware, operating system, or software vulnerabilities on the victim device.
* **Critical Importance**: Exploitation is the **first stage of direct code execution** on the target system. If exploit execution fails or the malware payload crashes (due to architecture mismatch, missing dependencies, or defensive intervention), all downstream attack stages are effectively halted.

---

### 2. Attacker Actions vs. Defender (Blue Team) Mitigation Strategies

| Role | Actions / Defensive Controls |
|---|---|
| 🥷 **Attacker** | • Executing exploit code against software, OS, or hardware vulnerabilities.<br>• Triggering malware payload execution after a user opens a weaponized document or installer.<br>• Deploying Zero-day exploits to bypass traditional signature-based security products. |
| 🛡️ **Defender (Blue Team / SOC)** | • **Endpoint Monitoring**: Leveraging EDR agents to detect abnormal child process trees (e.g., `winword.exe` spawning `cmd.exe` or `powershell.exe`).<br>• **Patch Management**: Rapidly deploying operating system and application security patches.<br>• **Detection Engineering**: Monitoring emerging CVEs and updating SIEM/EDR behavioral rules.<br>• **Least Privilege Enforcement**: Restricting user privileges to minimize blast radius upon exploitation.<br>• **Vulnerability Auditing & Pentesting**: Conducting routine automated scans and penetration tests to remediate flaws.<br>• **Secure Coding Practices**: Training software developers in secure coding standards to prevent application vulnerabilities. |

---

### 💡 Core SOC Interview & Operational Takeaways

> [!IMPORTANT]
> **Why is Exploitation the hardest phase for Blue Teams to defend against?**
> Adversaries frequently leverage novel, unseen malware payloads or unpatched **Zero-day vulnerabilities**. Traditional signature-based security solutions (like conventional Antivirus) are completely ineffective against zero-day exploits because no signature yet exists.

> [!TIP]
> **Prerequisite for Attack Success**: The exploit payload must perfectly match the victim host's underlying architecture and software version. If the adversary failed to gather accurate reconnaissance data in Step 1, the exploit will fail or crash the application.


## 7) Installation
## 🏰 Phase 5: Installation

### 1. Core Concept
* **Definition**: The fifth phase (Step 5) of the Cyber Kill Chain. The primary objective of the adversary in this stage is establishing **Persistence** on the victim host.
* **Rationale**: The initial vulnerability exploited in Step 4 could be patched by administrators, or the victim device might be rebooted. To prevent losing control, the adversary installs a covert **Backdoor** to guarantee continuous, long-term access.

---

### 2. Attacker Techniques vs. Defender (Blue Team) Controls

| Role | Primary Activities / Defensive Controls |
|---|---|
| 🥷 **Attacker** | • Installing persistent malware artifacts, Trojans, Remote Access Tools (RATs), or droppers.<br>• Uploading WebShells to compromised web application servers.<br>• Establishing **Persistence Mechanics**: Adding Scheduled Tasks, creating new Windows Services, modifying Registry Run keys, or injecting local Firewall bypass rules.<br>• Executing **Privilege Escalation** (gaining SYSTEM / Root privileges) to entrench deeper into the OS and wipe audit logs. |
| 🛡️ **Defender (Blue Team / SOC)** | • Operating with an **"Assume Breach"** Threat Hunting mindset.<br>• Utilizing EDR solutions to monitor unauthorized configuration modifications, registry key edits, and scheduled tasks.<br>• Enforcing strict Administrative Privilege boundaries (Privileged Access Management / PAM).<br>• Enforcing **Application Whitelisting / Code Signing** (restricting execution to digitally signed, authorized binaries).<br>• Auditing and restricting access to sensitive system paths (`System32`, Startup folders, Task Scheduler). |

---

### 📝 Quiz Answers & Scenario Analysis

* **Scenario**: EDR detected a malicious payload file on an endpoint, but the SOC Analyst verified that the file **had not been executed** (`not executed`) and no malicious process activity occurred.
* **Question**: In which step of the Cyber Kill Chain did the attacker fail, leading to the detection of the attack?
  * **Answer**: `4` (Exploitation)
* **Explanation**:
  * The adversary successfully delivered the file to the host (completing **Step 3: Delivery**).
  * However, because the malware **was never executed**, code execution failed at **Step 4: Exploitation**.
  * Consequently, the EDR solution flagged the dormant artifact before the adversary could compromise system control or establish persistence (**Step 5: Installation**).

## 8) Command and Control (C2)
  * ## 📡 Phase 6: Command and Control (C2)

### 1. Core Concept
* **Definition**: The sixth phase (Step 6) of the Cyber Kill Chain. In this stage, the adversary establishes a **covert, two-way communication channel** between the compromised endpoint and a remote Command and Control (C2) Server.
* **Objective**: Allows adversaries to issue interactive remote commands and receive data responses from the compromised host, laying the groundwork for final objective execution.
* **Key Distinguishing Note**: This phase is strictly limited to **establishing and maintaining communication lines**. It does *not* encompass the execution of final destructive objectives (e.g., data exfiltration, ransomware encryption).

---

### 2. Attacker Tactics vs. Defender (Blue Team) Controls

| Role | Primary Activities / Defensive Controls |
|---|---|
| 🥷 **Attacker** | • Deploying C2 infrastructure to listen for inbound agent callback requests (utilizing frameworks like Cobalt Strike, Metasploit, Sliver, or PowerShell Empire).<br>• Configuring victim malware to initiate callbacks (*beaconing* or *reverse shells*) over protocols such as DNS, HTTPS, or HTTP. |
| 🛡️ **Defender (Blue Team / SOC)** | • **Network Security Monitoring (NSM)**: Detecting periodic, automated outbound connection spikes (*beaconing traffic*), DNS tunneling requests, or non-standard outbound port usage.<br>• **Threat Intelligence Enrichment**: Ingesting known C2 IP and Domain blocklists into Firewalls, Web Proxies, and EDR platforms for automated blocking.<br>• **C2 Agent Artifact Hunting**: Scanning endpoints for known C2 agent signatures, named pipes, and memory artifacts. |

---

### 📝 Quiz Answers & Scenario Analysis

* **Scenario**: A SOC Analyst detected an internal Windows workstation **successfully establishing an outbound connection to a suspicious external IP**, confirming the adversary gained **remote command execution capability**.
* **Question**: According to the scenario above, what is the final Cyber Kill Chain step in which the attacker succeeded?
  * **Answer**: `6` (Command and Control)
* **Explanation**:
  * Successfully establishing an outbound channel that grants interactive remote control proves the adversary fully completed **Step 6 (Command and Control)**.
  * The adversary had not yet executed final destructive actions (**Step 7: Actions on Objectives**).
