# LECTURE2: Cyber Kill Chain
## 1) Introduction to Cyber Kill Chain

## 📌 Overview
The **Cyber Kill Chain** framework, developed by Lockheed Martin, breaks down a cyber attack into 7 distinct phases. Understanding these phases allows SOC analysts to identify where an attack was detected and stop it before completion.


### Which organization was the Cyber Kill Chain model developed by?
> **ANSWER: Lockheed Martin**
### In what year was the organization that developed the Cyber Kill Chain model founded?
> **ANSWER: 1995**
### In what year was the Cyber Kill Chain model developed?
> **ANSWER: 2011**



---

## 🎯 The 7 Phases of the Cyber Kill Chain

```text
[1. Reconnaissance] ➔ [2. Weaponization] ➔ [3. Delivery] ➔ [4. Exploitation]
                                                                  │
[7. Actions on Objectives] ◄── [6. Command & Control] ◄── [5. Installation]
```

### 1. Reconnaissance
* **Description**: Attacker gathers intelligence on the target (IPs, open ports, employee emails, tech stack).
* **SOC Detection**: Port scanning logs, OSINT monitoring, web server reconnaissance logs.

### 2. Weaponization
* **Description**: Pairing malware payload with an exploit (e.g., weaponized PDF/Word document with macro).
* **SOC Detection**: Occurs on attacker infrastructure (hard to detect directly until delivery).

### 3. Delivery
* **Description**: Transmitting the weaponized payload to the victim (Phishing email, USB, malicious website).
* **SOC Detection**: Secure Email Gateway (SEG) alerts, Web Proxy logs, IDS/IPS signatures.

### 4. Exploitation
* **Description**: Payload code executes on victim device by exploiting a vulnerability or user action.
* **SOC Detection**: EDR process execution alerts, suspicious PowerShell/Cmd spawned from Office apps.

### 5. Installation
* **Description**: Attacker establishes persistence on the victim system (Registry run keys, Scheduled tasks, Services).
* **SOC Detection**: EDR persistence alerts, Windows Event Logs (ID 4697, ID 7045).

### 6. Command & Control (C2)
* **Description**: Establishing a remote communication channel back to the attacker's server.
* **SOC Detection**: Beaconing traffic, unusual DNS requests, outbound connections over non-standard ports.

### 7. Actions on Objectives
* **Description**: Attacker achieves goal (Data exfiltration, ransomware encryption, lateral movement).
* **SOC Detection**: Large outbound data transfers, volume shadow copy deletion, domain controller access.
