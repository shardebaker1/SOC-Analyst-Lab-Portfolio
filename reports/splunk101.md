# 🔍 Splunk 101 – SIEM Fundamentals

## ✅ Objective
Learn the basics of using Splunk as a SIEM tool to search, visualize, and detect malicious activity using SPL (Search Processing Language).

## 🛠️ Tools Used
- Splunk Web Interface
- SPL (Search Processing Language)
- TryHackMe Lab Environment

## 📋 Scenario
You are a junior SOC analyst tasked with analyzing logs inside Splunk. Use queries to investigate brute-force attacks and privilege abuse.

---

## 🔎 Steps Taken

### Task 1: Search Fundamentals
- Used `index=*` to get familiar with basic querying.
- Used `sourcetype=WinEventLog:Security` to filter Windows logs.

### Task 2: Brute Force Attack
- Ran the following SPL query to search for failed logins:
  ```spl
  index=main EventCode=4625
