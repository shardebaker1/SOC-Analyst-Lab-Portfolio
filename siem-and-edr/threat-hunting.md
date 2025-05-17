# 🛡️ SIEM & EDR: Alert Triage, Monitoring & Threat Hunting

## ✅ Objective
Gain hands-on experience using SIEM and EDR tools to investigate malicious activity through log analysis, alert triage, and threat hunting.

## 🛠️ Tools Used
- Splunk
- Elastic SIEM
- EDR Interfaces (TryHackMe labs)
- Windows Event Viewer & Sysmon
- PowerShell logging
- VirusTotal / hash investigation

## 📋 Scenario
You're a junior SOC analyst responsible for identifying suspicious events using SIEM and EDR tools. Your tasks include detecting brute-force attacks, privilege escalation, persistence techniques, and lateral movement.

---

## 🔎 Steps Taken

Used multiple platforms including SIEM dashboards and EDR tools to monitor event logs and respond to alerts.

- Reviewed Windows Security Events and Sysmon logs.
- Monitored for brute-force attacks using Event ID `4625` (failed logon).
- Found successful logins using Event ID `4624` shortly after failed attempts.
- Detected privilege escalation using Event ID `4672`.
- Checked for new user creation with Event ID `4720`.
- Used EDR to trace suspicious process chains (e.g., `explorer.exe` → `powershell.exe`).
- Investigated persistence techniques via registry run keys (Sysmon Event ID `13`).
- Validated suspicious hashes and URLs via VirusTotal.
- Analyzed parent-child relationships for execution chains in EDR.

---

## 🧠 IOCs Identified

- **Attacker IP**: `10.10.5.22`
- **Suspicious User**: `user1`
- **Malicious Process Chain**:
  - `explorer.exe` → `powershell.exe` → custom script
- **Registry Persistence**:
  - Run key entry added: `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
- **Event Sequence**:
  - `4625` (failed login)
  - `4624` (successful login)
  - `4672` (admin privilege granted)
  - `13` (registry write via Sysmon)
  - `1` (process creation)

---

## 🛡️ Detection Summary

An attacker attempted a brute-force attack from IP `10.10.5.22`, eventually succeeding and logging in as `user1`. Shortly after, they gained administrative privileges (4672) and established persistence by modifying the registry (Sysmon Event ID 13). EDR telemetry confirmed PowerShell execution chained from `explorer.exe`, suggesting hands-on keyboard activity. There were no alerts for user creation, but the registry modification suggests an attempt to maintain access.

---

## 🧯 Recommendations

- 🚫 **Block IP** `10.10.5.22` at the firewall and update IDS/IPS signatures.
- 🔐 **Implement account lockout policies** to prevent brute-force attempts.
- ✅ **Enable MFA** for all administrative accounts.
- 🔍 **Monitor Event IDs**: `4625`, `4624`, `4672`, `4720`, and Sysmon `1`, `13`.
- 🧹 **Harden PowerShell logging** and restrict access to built-in scripting tools.
- 🧪 **Submit observed hashes and scripts** to sandbox or VirusTotal.
- 📈 **Deploy anomaly-based detection** for registry changes and parent-child anomalies.

---

## 📸 Screenshots

_Add your relevant screenshots here as Markdown image links:_

```md
![SIEM Dashboard](../images/siem-dashboard-example.png)
![EDR Alert Example](../images/edr-alert-chain.png)
