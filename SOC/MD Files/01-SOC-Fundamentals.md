# 01 - SOC Fundamentals

## 📌 Overview
A **Security Operations Center (SOC)** is a centralized unit within an organization responsible for monitoring, detecting, analyzing, and responding to cybersecurity incidents on an ongoing basis.

---

## 👥 Key SOC Roles & Tiers

| Tier | Role | Primary Responsibilities |
|---|---|---|
| **Tier 1** | Triage Analyst | Continuously monitors SIEM alerts, filters out false positives, and escalates true incidents. |
| **Tier 2** | Incident Responder | Conducts deep-dive investigations, correlates logs, isolates infected endpoints, and performs containment. |
| **Tier 3** | Threat Hunter / Specialist | Actively hunts for hidden threats, analyzes malware, and creates custom detection rules (YARA/Sigma). |
| **SOC Lead / Manager** | Operations Lead | Manages SOC operations, handles major incident escalation, and reports to CISO. |

---

## 🛠️ Essential SOC Tooling

1. **SIEM (Security Information and Event Management)**: Centralized log aggregation (Splunk, Elastic, Microsoft Sentinel).
2. **EDR (Endpoint Detection and Response)**: Real-time endpoint monitoring and containment (CrowdStrike, Defender for Endpoint).
3. **SOAR (Security Orchestration, Automation, and Response)**: Automated playbooks for rapid response (Cortex XSOAR, Shuffle).
4. **Threat Intelligence Platforms (TIP)**: Contextual enrichment (VirusTotal, AlienVault OTX, AbuseIPDB).

---

## 🔄 SOC Incident Response Lifecycle (NIST SP 800-61)

1. **Preparation**: Configuring tools, policies, and sensors.
2. **Detection & Analysis**: Triaging alerts and validating incident scope.
3. **Containment, Eradication & Recovery**: Stopping the threat, removing malware, restoring systems.
4. **Post-Incident Activity**: Lessons learned, updating detection signatures.
