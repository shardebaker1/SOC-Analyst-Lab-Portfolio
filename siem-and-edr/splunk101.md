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
  `index=main EventCode=4625`  
- Observed multiple failed login attempts from a single IP address.

### Task 3: Successful Logins 
- Queried successful logins using:  
  `index=main EventCode=4624`  
- Found a successful login following multiple failed ones from the same IP.

### Task 4: Account Lockouts 
- Investigated account lockouts using:  
  `index=main EventCode=4740`  
- No account lockouts were triggered despite brute-force attempts.

### Task 5: Privilege Escalation 
- Searched for privilege escalation attempts:  
  `index=main EventCode=4672`  
- Identified an event showing special privileges assigned post-login.

### Task 6: User Creation 
- Identified newly created accounts with:  
  `index=main EventCode=4720`  
- No suspicious accounts were created during the session.

---

## 🧠 IOCs Identified
- **IP Address**: `192.168.5.22`  
- **Username**: `Administrator`  
- **Suspicious Events**:  
  - Multiple `4625` (failed logins)  
  - Followed by `4624` (successful login)  
  - Then `4672` (privilege escalation)

---

## 🛡️ Detection Summary
A brute-force attack was launched from IP address `192.168.5.22` resulting in several failed login attempts. Eventually, the attacker successfully logged in as `Administrator` and elevated privileges (EventCode 4672). No account lockouts were triggered, indicating potential policy weaknesses.

---

## 🧯 Recommendations
- 🔐 **Block IP** `192.168.5.22` at the firewall.
- 🔒 **Enforce account lockout policy** after repeated failed logins.
- ✅ **Enable multi-factor authentication (MFA)** for administrative users.
- 🛠️ Regularly audit and monitor privileged account activity.

---

## 📸 Screenshot
![Splunk Investigation](../images/splunk101-example.png)
