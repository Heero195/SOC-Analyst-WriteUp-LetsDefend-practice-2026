# 📘 Lecture 1: SOC Fundamentals

---

## 1. Overview of SOC (What is a SOC?)

A **Security Operations Center (SOC)** is a centralized organizational unit responsible for continuously monitoring, detecting, analyzing, and responding to cybersecurity incidents.

Successful SOC operations rely on **three core pillars**:
* 👤 **People**: Skilled cybersecurity professionals equipped with analytical mindsets and up-to-date threat intelligence.
* ⚙️ **Processes**: Standardized incident response workflows aligned with industry frameworks such as **NIST SP 800-61, PCI-DSS, and HIPAA**.
* 🛠️ **Technology**: Integrated security tools tailored to the organization's architecture and operational requirements.

---

## 2. SOC Operational Models

| SOC Model | Operational Structure | Target Use Case |
|---|---|---|
| **In-house SOC** | Fully built, staffed, and managed internally by the organization. | Large enterprises and financial institutions with dedicated budgets. |
| **Virtual SOC** | Distributed team working remotely without a fixed physical facility. | Agile organizations seeking cost savings on physical infrastructure. |
| **Co-Managed SOC** | Hybrid model combining internal analysts with an External MSSP. | Organizations balancing internal control with external expertise. |
| **Command SOC** | Master SOC overseeing multiple regional or subsidiary SOC facilities. | Multinational telecom providers, defense agencies, and conglomerates. |

---

## 3. SOC Roles & Responsibilities

```text
[Tier 1 SOC Analyst: Triage & Filtering] ➔ [Tier 2 SOC Analyst: Deep Analysis & Incident Response]
                                                                  │
[SOC Lead / Manager: Operations & Strategy] ◄── [Tier 3 Analyst / Threat Hunter: APT & Malware Analysis]
```

* 🟢 **SOC Analyst (Tier 1 / Tier 2 / Tier 3)**:
  * *Tier 1 (Triage)*: Monitors SIEM alerts, validates initial events, and filters out False Positives.
  * *Tier 2 (Incident Response)*: Investigates root causes, correlates log sources, and executes remediation playbooks.
  * *Tier 3 (Specialist)*: Conducts deep-dive malware analysis, reverse engineering, and custom detection engineering (YARA/Sigma).
* 🔴 **Incident Responder**: Leads active containment, eradication, and post-breach mitigation during security incidents.
* 🟣 **Threat Hunter**: Proactively searches for covert adversaries (APTs) that evade traditional perimeter controls.
* 🛠️ **Security Engineer**: Deploys, maintains, and integrates security tooling (SIEM, EDR, SOAR).
* 👔 **SOC Manager**: Manages operations, budgeting, compliance reporting, and strategic alignment with executive leadership (CISO).

---

## 4. Core SOC Technology Stack

### 1. SIEM (Security Information and Event Management)
* **Function**: Centralizes log aggregation and delivers real-time security event correlation and alerting.
* **Industry Tools**: Splunk, IBM QRadar, ArcSight, FortiSIEM, Microsoft Sentinel.

### 2. Log Management
* Centralizes event logs across diverse log sources: Web Servers, Windows/Linux OS, Firewalls, Web Proxies, and EDR agents.
* Enables analysts to query historical traffic, DNS requests, source IPs, and non-standard port activities.

### 3. EDR (Endpoint Detection and Response)
* **Function**: Provides granular visibility and threat containment directly at the endpoint level.
* **Key Capabilities**:
  * **Telemetry Inspection**: Process tree analysis, network socket connections, browser history, and registry modifications.
  * **Live Response**: Remote command-line access for live forensic investigation.
  * **Network Isolation**: Instantly isolates compromised hosts to prevent lateral movement.
* **Industry Tools**: SentinelOne, CrowdStrike Falcon, VMware Carbon Black, Microsoft Defender for Endpoint.

### 4. SOAR (Security Orchestration, Automation, and Response)
* Automates repetitive investigation steps and response workflows using structured **Playbooks**.
* **Industry Tools**: Splunk Phantom, Palo Alto Cortex XSOAR, Demisto.

### 5. Threat Intelligence Feeds
* Enriches alerts with known Indicators of Compromise (IOCs: MD5/SHA256 hashes, malicious IP addresses, C2 domains).
* Key Sources: VirusTotal, AbuseCH, Cisco Talos, AlienVault OTX.

---

## 5. Incident Response Lifecycle (NIST SP 800-61)

1. 🛡️ **Preparation**: Establishing policies, hardening assets, deploying sensors, and training staff.
2. 🔍 **Detection & Analysis**: Triaging alerts, assessing severity, and determining incident blast radius.
3. 🚧 **Containment, Eradication & Recovery**: Isolating compromised endpoints, purging malicious artifacts, and restoring services safely.
4. 📝 **Post-Incident Activity**: Conducting Lessons Learned reviews and updating detection signatures.

---

## ⚠️ 6. Common Pitfalls to Avoid as a SOC Analyst

* ❌ **Over-reliance on VirusTotal**: A `0/70` detection ratio does not guarantee safety (e.g., brand-new zero-day malware).
* ❌ **Ignoring Cache Dates**: Failing to click "Re-analyze" on stale VirusTotal scans.
* ❌ **Rushing to Automated Sandboxes**: Skipping static analysis and contextual log correlation before dynamic execution.
* ❌ **Tunnel-Vision Log Analysis**: Focusing on a single isolated alert rather than tracing pre- and post-incident activity timelines.

---
Virtual SOC works remotely?  
> **ANSWER: Virtual SOC**

Responsible for connecting security products?  
> **ANSWER: Security Engineer**

What is SOC?  
> **ANSWER: Security Operation Center**

Most important tool?  
> **ANSWER: All of this, and much more**

Internal + MSSP model?  
> **ANSWER: Co-Managed SOC**

Find vulnerabilities before attackers?  
> **ANSWER: Threat Hunter**

Goal of SIEM?  
> **ANSWER: To provide real-time logging of events in an environment.**

LetsDefend SIEM page?  
> **ANSWER: Monitoring**

What is EDR?  
> **ANSWER: Software that monitors endpoint devices rather than the entire network.**

NIST Incident Lifecycle?  
> **ANSWER: Preparation, Detection/Analysis, Containment/Eradication and Recovery, Post-Incident Activity**

Threat Intelligence Feed does NOT provide?  
> **ANSWER: A sample of the infected file**

Common mistake?  
> **ANSWER: Insufficient log analysis**


