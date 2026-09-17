# Lecture 3: MITRE ATT&CK Framework

---

## 1) Introduction

> **ANSWER: CHECK**

---

## 2) Introduction to MITRE

```text
What is MITRE ATT&CK Framework?
MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) is a knowledge base and framework introduced by MITRE in 2013. It is continuously updated to reflect evolving technology and threat landscapes. 

The framework enables systematic analysis of cyber attacks by categorizing them into distinct operational stages and examining the specific methods used within each phase. MITRE ATT&CK serves as an essential resource for all cybersecurity professionals.
```

### In what year was MITRE founded?
> **ANSWER: 1958**

### In what year did the development of the MITRE ATT&CK Framework begin?
> **ANSWER: 2013**

---

## 3) Matrix

```text
What is MITRE ATT&CK Matrix?
The MITRE ATT&CK Matrix is a visual framework used to classify and map cyber attack methodologies. MITRE designed matrices to provide granular visibility into attacker behavior across different environments.

Three distinct matrices exist within the MITRE ATT&CK Framework based on platform categories:

1. Enterprise Matrix: The initial and most comprehensive matrix, covering widely deployed enterprise digital systems. It is primarily used to analyze attacks targeting corporate networks and infrastructure.
   Sub-matrices include:
   -- PRE (Pre-ATT&CK)
   -- Windows
   -- macOS
   -- Linux
   -- Cloud
   -- Network
   -- Containers

2. Mobile Matrix: Focused on mobile device security (smartphones, tablets) for both individual and enterprise environments.
   Sub-matrices include:
   -- Android
   -- iOS

3. ICS (Industrial Control Systems) Matrix: Tailored for Operational Technology (OT) and industrial control environments (SCADA, PLCs) to support cybersecurity analysis of industrial systems.
```

### What are the visual representations depicting tactics and techniques in the MITRE ATT&CK Framework called?
> **ANSWER: Matrix**

### Which matrix covers information about the cybersecurity of Windows, Linux, macOS, Azure AD, and Office 365 platforms?
> **ANSWER: Enterprise**

### Which matrix covers cybersecurity information for Android and iOS platforms?
> **ANSWER: mobile**

---

## 4) Tactics

Tactics represent the adversary's operational goal or objective—the *why* behind an action. Tactics sit in the top row of the MITRE ATT&CK Matrix and group attacker behaviors.

### Enterprise Tactics (14 Tactics)
* Reconnaissance
* Resource Development
* Initial Access
* Execution
* Persistence
* Privilege Escalation
* Defense Evasion
* Credential Access
* Discovery
* Lateral Movement
* Collection
* Command and Control
* Exfiltration
* Impact

### Mobile Tactics (14 Tactics)
* Initial Access
* Execution
* Persistence
* Privilege Escalation
* Defense Evasion
* Credential Access
* Discovery
* Lateral Movement
* Collection
* Command and Control
* Exfiltration
* Impact
* Network Effects
* Remote Service Effects

### ICS Tactics (12 Tactics)
* Initial Access
* Execution
* Persistence
* Privilege Escalation
* Evasion
* Discovery
* Lateral Movement
* Collection
* Command and Control
* Inhibit Response Function
* Impair Process Control
* Impact

### What is the ID of the "Lateral Movement" tactic in the Enterprise matrix?
> **ANSWER: TA0008**

### When was the "Persistence" tactic in the Mobile matrix created?
> **ANSWER: 17 October 2018**

### Which tactic across Enterprise, Mobile, and ICS matrices is used to obtain higher-level permissions on target systems?
> **ANSWER: Privilege Escalation**

---

## 5) Techniques, Sub-Techniques, and Procedures

```text
Techniques and Sub-Techniques:
Techniques describe the specific methods adversaries use to achieve a tactical goal (the "how"). Each technique falls under a specific tactic within the matrix. Sub-techniques provide further granularity into specific implementations.

What is a Procedure?
Procedures represent real-world execution examples of techniques and sub-techniques. They detail the exact tools, scripts, commands, or software utilized by a specific threat actor during an attack.
```

### What is the name of the technique with ID T1055 in the Enterprise matrix?
> **ANSWER: Process Injection**

### Which platform is the Enterprise technique with ID T1112 designed for?
> **ANSWER: Windows**

### In the MITRE ATT&CK framework, under which tactic does the "Supply Chain Compromise" technique fall?
> **ANSWER: Initial Access**

---

## 6) Mitigations

Mitigations represent defensive measures, configurations, and security controls recommended to prevent or reduce the impact of specific ATT&CK techniques. Each mitigation has a unique ID (e.g., `M1032`), name, and detailed description.

### What is the name of the mitigation with ID M1032 in Enterprise mitigations?
> **ANSWER: Multi-factor Authentication**

### What is the name of the Enterprise mitigation recommending "digital signature verification should be implemented to prevent untrusted code from running on enterprise devices"?
> **ANSWER: Code Signing**

---

## 7) Groups (APTs)

Advanced Persistent Threat (APT) Groups are sophisticated, often state-sponsored or financially motivated hacker organizations conducting targeted and persistent cyber campaigns.

MITRE ATT&CK maintains detailed profiles on known APT groups, mapping their historical TTPs to the matrix to reveal attack patterns and target profiles.

### What is the name of the software associated strictly with the "System Information Discovery" technique for the OilRig APT group?
> **ANSWER: systeminfo**

### What is the name of the APT group whose "Associated Groups" section includes "GOLD NIAGARA", "ITG14", and "Carbon Spider"?
> **ANSWER: FIN7**

---

## 8) Software

The Software category indexes malware, RATs, utilities, and legitimate dual-use administrative tools leveraged by APT groups. Each entry includes a unique ID, name, description, and mapping to associated techniques and threat actors.

### Which platform is the software "Cryptoistic" (used by Lazarus Group) designed for?
> **ANSWER: MacOS**

### What type of software is "Rotexy" on Android platforms?
> **ANSWER: Malware**

### What is the name of the APT group that utilizes the "PUNCHBUGGY" software targeting POS networks?
> **ANSWER: FIN8**

---

## 📝 Final Quiz & Answer Key

### What concept expresses the adversary's operational motivation/goal in the MITRE ATT&CK Framework?
> **ANSWER: Tactic**

### What concept explains how the adversary performs their action in the MITRE ATT&CK Framework?
> **ANSWER: Technique**

### What concept details practical execution examples (tools/commands used) by adversaries in the MITRE ATT&CK Framework?
> **ANSWER: Procedure**

### Which of the following is an ID of a Technique in the MITRE ATT&CK Framework?
> **ANSWER: T1426**

### Which of the following Enterprise techniques belongs to a different tactic?
> **ANSWER: Exploit Public-Facing Application**

### In which matrix is the "Impair Process Control" tactic located?
> **ANSWER: ICS Matrix**

### What tool is used for credential dumping specifically for Linux systems by the "TeamTNT" APT group?
> **ANSWER: MimiPenguin**

---
*100% CORRECT | LetsDefend SOC Analyst Path - Lecture 3 Notes*
