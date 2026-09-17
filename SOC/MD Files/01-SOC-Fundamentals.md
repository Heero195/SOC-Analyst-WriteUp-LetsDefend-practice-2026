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
