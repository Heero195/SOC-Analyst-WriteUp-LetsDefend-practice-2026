# LetsDefend - SOC Analyst Learning Path Write-Ups

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=34&duration=3000&pause=800&color=C084FC&center=true&vCenter=true&width=900&lines=Heero195+-+LetsDefend+SOC+Analyst+Path;Incident+Response+%26+Security+Notes;Detailed+SOC+Alert+Investigations" />
</p>

A comprehensive collection of write-ups, incident analysis reports, and study notes for the **LetsDefend SOC Analyst Learning Path**, curated by **[Heero195](https://github.com/Heero195)**.

---

<p align="center">
  <img src="https://img.shields.io/badge/Focus-SOC%20Analyst%20%7C%20Blue%20Team-blueviolet?style=for-the-badge&logo=shield" />
  <img src="https://img.shields.io/badge/Platform-LetsDefend.io-0070ba?style=for-the-badge&logo=security" />
  <img src="https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge" />
</p>

---

## 📁 Repository Structure

```text
.
├── README.md                           # Main repository documentation
└── SOC 
    ├── Assets                          # Screenshots, diagrams, and visual proof
    │   └── screenshots/
    │
    ├── MD Files                        # Theoretical notes and framework analyses
    │   ├── 01-SOC-Fundamentals.md
    │   ├── 02-Cyber-Kill-Chain.md
    │   └── 03-MITRE-ATTACK.md
    │
    └── Labs                            # Practical Incident Response Write-Ups
        └── 01-SOC282-Phishing-Alert.md
```

---

## 📚 Modules & Study Notes

| # | Topic | Category | Status |
|---|---|---|---|
| 01 | [SOC Fundamentals](SOC/MD%20Files/01-SOC-Fundamentals.md) | Theory & Roles | Completed |
| 02 | [Cyber Kill Chain](SOC/MD%20Files/02-Cyber-Kill-Chain.md) | Framework | Completed |
| 03 | [MITRE ATT&CK Framework](SOC/MD%20Files/03-MITRE-ATTACK.md) | Framework | Completed |

---

## 🛡️ Practical Labs & Alert Investigations

| Alert ID | Alert Name | Category | Verdict | Write-Up |
|---|---|---|---|---|
| **SOC282** | Phishing Alert | Email Security | True Positive | [Read Write-Up](SOC/Labs/01-SOC282-Phishing-Alert.md) |

---

## ⚡ Methodology

Each lab investigation follows standard **SOC Incident Handling Procedures**:

1. **Alert Triage**: Examining SIEM alert details, severity level, and affected host/user.
2. **Log & Data Analysis**: Tricking IOCs across SIEM, EDR, Firewall, and Web proxy logs.
3. **Threat Intelligence Correlation**: Checking hash values, domains, and IPs against VirusTotal, AbuseIPDB, and Any.Run.
4. **Containment & Mitigation**: Determining True/False Positive status and specifying isolation actions.

---

## 📬 Contact & Connect

- **GitHub**: [@Heero195](https://github.com/Heero195)
- **Platform**: [LetsDefend.io](https://letsdefend.io)

---
*Disclaimer: All write-ups are for educational and security research purposes only.*
