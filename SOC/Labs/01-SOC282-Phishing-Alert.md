# SOC282 - Phishing Alert Write-Up

## 📋 Incident Details

| Attribute | Details |
|---|---|
| **Alert ID** | SOC282 |
| **Alert Name** | Phishing Mail Detected |
| **Severity** | High |
| **Event Time** | 2026-09-17 14:15:00 UTC |
| **Target Host** | `Client-Workstation-04` (192.168.1.105) |
| **Target User** | `johndoe@company.local` |

---

## 🔍 Investigation Walkthrough

### Step 1: Alert Triage & Mail Inspection
Inspected the mail gateway log for incoming message flagged by SOC rules.
- **Sender**: `billing-update@account-security-alert.com`
- **Recipient**: `johndoe@company.local`
- **Subject**: `URGENT: Verify your account credentials immediately`
- **Attachment**: `Invoice_9942.zip` containing `Invoice_9942.exe`

### Step 2: IOC Analysis & Threat Intelligence

#### File Hash Analysis (`Invoice_9942.exe`)
- **MD5**: `e2c7657196f5f2048830f615410f0f5b`
- **SHA256**: `a8f5f12b72459b79412586e92750e335b1d92374e2d31221764619d08e567a1c`
- **VirusTotal**: 54/72 detections (Flagged as AgentTesla Infostealer / Trojan).

#### Network Indicators
- **C2 IP**: `185.220.101.5`
- **Domain**: `account-security-alert.com` (AbuseIPDB Score: 98% Malicious).

---

## 📊 Summary Table of IOCs

| Type | Value | Reputation | Description |
|---|---|---|---|
| **File Hash (MD5)** | `e2c7657196f5f2048830f615410f0f5b` | Malicious | AgentTesla Executable |
| **Malicious IP** | `185.220.101.5` | Malicious | Command & Control Server |
| **Sender Domain** | `account-security-alert.com` | Malicious | Phishing Infra |

---

## 🎯 Verdict & Containment Actions

* **Verdict**: **True Positive**
* **Containment & Remediation**:
  1. **Host Isolation**: Isolated `Client-Workstation-04` (192.168.1.105) from the network via EDR.
  2. **Firewall Blocking**: Added `185.220.101.5` and `account-security-alert.com` to egress blocklist.
  3. **Credential Reset**: Triggered mandatory password reset for `johndoe@company.local`.
  4. **Purge Email**: Deleted phishing message from all internal mailboxes via SEG.
