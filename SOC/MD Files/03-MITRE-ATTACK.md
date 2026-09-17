# 03 - MITRE ATT&CK Framework

## 📌 Overview
**MITRE ATT&CK®** (Adversary Tactics, Techniques, and Common Knowledge) is a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations.

---

## 🧭 Tactics vs. Techniques vs. Procedures (TTPs)

* **Tactic**: The adversary's tactical goal (the *why* - e.g., Initial Access, Persistence).
* **Technique**: The action taken to achieve the tactic (the *how* - e.g., Phishing T1566).
* **Procedure**: The specific implementation by a threat actor (e.g., APT29 using Spearphishing Attachment with malicious ISO).

---

## 📊 Core MITRE ATT&CK Enterprise Tactics

| Tactic ID | Tactic Name | Description |
|---|---|---|
| **TA0001** | Initial Access | How the adversary gets into your network. |
| **TA0002** | Execution | Running malicious code on local or remote systems. |
| **TA0003** | Persistence | Maintaining access across restarts and credential resets. |
| **TA0004** | Privilege Escalation | Gaining higher-level permissions (SYSTEM/Administrator). |
| **TA0005** | Defense Evasion | Avoiding detection by security controls. |
| **TA0006** | Credential Access | Stealing passwords, hashes, and Kerberos tokens. |
| **TA0007** | Discovery | Exploring the victim environment and network topology. |
| **TA0008** | Lateral Movement | Moving through the network to target assets. |
| **TA0009** | Collection | Gathering data of interest for exfiltration. |
| **TA0011** | Command & Control | Communicating with compromised systems. |
| **TA0010** | Exfiltration | Stealing data out of the target network. |
| **TA0040** | Impact | Disrupting, degrading, or destroying systems and data. |
