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
