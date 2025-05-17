# 🧠 Elastic Security – SIEM Fundamentals

## ✅ Objective
Learn how to use Elastic Security to analyze logs, investigate alerts, and understand SIEM workflows for detection and threat hunting.

## 🛠️ Tools Used
- Elastic Stack (Elasticsearch, Kibana)
- Elastic Security SIEM Interface
- TryHackMe Lab Environment

## 📋 Scenario
You are a security analyst leveraging Elastic Security to monitor and investigate suspicious activity. You’ll learn how to use Kibana’s SIEM dashboards, analyze alerts, and hunt for threats.

---

## 🔎 Steps Taken

### Task 1: Navigated the SIEM App
- Accessed the **Security** section in Kibana.
- Explored built-in dashboards for **Detections**, **Hosts**, and **Network**.

### Task 2: Analyzed Alerts
- Reviewed alerts in the **Detections > Alert Table**.
- Used filters to pinpoint suspicious events based on user activity, host, and severity level.

### Task 3: Investigated with Timeline
- Opened the **Timeline** feature.
- Added fields like `source.ip`, `destination.ip`, and `event.category`.
- Followed a brute-force login scenario to identify compromised credentials.

### Task 4: Correlated Events
- Investigated event chains across different hosts and users.
- Used visual timelines to map attacker movement.

### Task 5: Used SIEM Detections
- Reviewed active detection rules and matched them against alert data.
- Tuned detection rules and severity levels for better triage.

---

## 🧠 IOCs Identified
- **Attacker IP**: `192.168.100.20`  
- **Usernames**: `admin`, `elastic`  
- **Suspicious Events**:  
  - Multiple failed logins  
  - Successful login  
  - Lateral movement attempts

---

## 🛡️ Detection Summary
A brute-force login attempt was observed from `192.168.100.20` targeting administrative accounts. After several failed attempts, the attacker successfully authenticated and initiated further activity across multiple hosts. Timeline correlation revealed potential lateral movement and privilege abuse.

---

## 🧯 Recommendations
- 🔐 **Block external access** from `192.168.100.20`.
- 🔒 **Enforce stronger password policies** for privileged accounts.
- ✅ **Enable audit logging** and real-time alerting for brute-force indicators.
- 🛠️ Regularly review and tune SIEM detection rules.

---

## 📸 Screenshot
![Elastic SIEM Investigation](../images/elastic-siem-example.png)
