# 🛡️ Security Information and Event Management (SIEM) – Fundamentals

## ✅ Objective
Understand SIEM concepts, use cases, and how to monitor/analyze security logs to detect threats in an enterprise environment.

## 🛠️ Tools Used
- SIEM Dashboard (TryHackMe-provided)
- Log sources: Windows Event Logs, Sysmon
- Event IDs & Alert Rules

## 📋 Scenario
You are a SOC analyst reviewing SIEM alerts to detect suspicious behavior such as failed logins, privilege abuse, and lateral movement.

---

## 🔎 Steps Taken

### Task 1: SIEM Overview
- Learned about log ingestion, normalization, correlation, and alerting.
- Reviewed how logs from endpoints and network devices feed into SIEM.

### Task 2: Alert Investigation – Login Failures
- Investigated multiple failed login events:
  ```text
  EventCode: 4625
  TargetUserName: user1
  IP Address: 10.10.5.22
