# 📘 Lecture 4: Introduction to Phishing

---

## 1) Introduction

## 📌 Overview

Definition & Strategic Purpose

* **Definition**: A **Phishing Attack** is a form of social engineering where adversaries deceive users into clicking malicious URLs or executing weaponized files to steal sensitive credentials and personal data.
* **Strategic Objective**: Beyond basic password theft, adversaries exploit the **human element** — universally recognized as the weakest link in the security perimeter — as an initial launching pad for deeper network penetration.

---

Position & Significance in Cybersecurity

> [!IMPORTANT]
> **Cyber Kill Chain Alignment**: Phishing operates directly within **Phase 3: Delivery** — the exact stage where pre-crafted malicious artifacts are transmitted to target victims.

> [!TIP]
> **Prevalence**: Phishing remains the #1 most prevalent **Initial Access / Attack Vector** utilized by adversaries in modern cyber campaigns.


<img width="950" height="681" alt="image" src="https://github.com/user-attachments/assets/77071c38-5271-4015-b376-66a873fb7fe3" />

---

Social Engineering & Psychological Manipulation

Adversaries leverage high-impact social engineering scenarios to compel victims into acting impulsively without verification:

| Psychological Vector | Lure Strategy | Scenario Example | Attacker Intent |
|---|---|---|---|
| 🎁 **Greed & Opportunity** | Enticing rewards & discounts | *"You have won a prize!"* / *"Claim your exclusive mega discount!"* | Triggers excitement to bypass rational caution. |
| ⚠️ **Fear & Urgency** | Intimidation & threats | *"Your account will be terminated immediately unless verified within 24 hours."* | Instills panic to force compliance without checking legitimacy. |

---

## 2) Information Gathering

### Email Spoofing & Authentication Protocols
Because legacy SMTP protocols lack built-in authentication, adversaries utilize **Email Spoofing** to forge sender addresses and impersonate trusted individuals or organizations.

To combat spoofing, three core email authentication protocols are deployed:
* **SPF (Sender Policy Framework)**: Specifies which mail servers/IP addresses are authorized to send emails on behalf of a domain.
* **DKIM (DomainKeys Identified Mail)**: Adds a cryptographic digital signature to emails to verify domain authorship and message integrity.
* **DMARC (Domain-based Message Authentication, Reporting, and Conformance)**: Enforces domain alignment rules using SPF and DKIM results, defining handling policies (*None, Quarantine, Reject*).

#### 🛠️ Manual Verification Technique
* Identify the **SMTP Source IP Address** from raw mail headers.
* Query the domain's SPF, DKIM, DMARC, and MX records using tools like **MxToolbox**.
* Conduct a **WHOIS Lookup** on the SMTP IP address to verify whether the IP belongs to the claimed organization's ASN/infrastructure.

> [!WARNING]
> **Account Takeover Warning**: Passing SPF/DKIM authentication does **NOT** guarantee an email is safe. Adversaries often compromise legitimate personal or corporate email accounts (Business Email Compromise - BEC) to send malicious emails from authentic addresses.

---

### Email Traffic Analysis & Gateway Hunting
Analyzing mail gateway logs helps SOC analysts assess attack scope, target audience, and campaign patterns:

| Gateway Search Parameter | Purpose in Investigation |
|---|---|
| **Sender Address** (`info@letsdefend.io`) | Identifies specific sender accounts used in the campaign. |
| **SMTP Source IP** (`127.0.0.1`) | Uncovers originating mail relay servers across multiple spoofed accounts. |
| **Domain Base** (`@letsdefend.io`) | Detects all inbound emails originating from a specific domain. |
| **Brand Keywords** (`letsdefend`) | Catches phishing variants sent from public providers (e.g., Gmail, Hotmail) or typosquatted domains. |
| **Subject Line Keywords** | Tracks campaigns where sender IPs and email addresses change dynamically. |

#### 📊 Target Audience & Timezone Intelligence
* **Target Concentration**: If malicious emails repeatedly target specific employees, their addresses may have been harvested via OSINT tools (e.g., **`theHarvester`** on Kali Linux) or leaked on public paste sites (PasteBin).
* **Timezone Analysis**: Emails received consistently outside standard corporate working hours indicate the adversary is operating from a **different geographical time zone**, aiding threat actor profiling.
