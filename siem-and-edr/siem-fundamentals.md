# 📊 SIEM Fundamentals – Event Monitoring & Analysis

## ✅ Objective
Understand the fundamentals of Security Information and Event Management (SIEM), focusing on log collection, alert triage, detection of suspicious behavior, and basic threat investigation.

## 🛠️ Tools Used
- Windows Event Viewer
- Sysmon
- SIEM Interface
- MITRE ATT&CK Mapping
- TryHackMe Lab Environment

## 📋 Scenario
You're working as a SOC analyst monitoring a network using a SIEM platform. Your job is to analyze logs, detect patterns of suspicious behavior, and respond to alerts. You’ll follow a structured process to identify potential threats from authentication events, privilege changes, and persistence mechanisms.

---

## 🔎 Steps Taken

### Task 1: Failed Logins
- Searched for failed login attempts using:  
  `EventCode=4625`
- Found multiple failed login attempts from IP address `192.168.100.14`.

### Task 2: Successful Logins
- Queried successful logins using:  
  `EventCode=4624`
- Observed successful login from the same IP following failed attempts.
- Username involved: `sysadmin1`.

### Task 3: Privilege Escalation
- Searched for privilege escalation using:  
  `EventCode=4672`
- Found a privilege escalation event immediately after login by `sysadmin1`.

### Task 4: Persistence via Registry
- Checked for persistence mechanisms using:  
  `EventCode=13 TargetObject="HKCU\Software\Microsoft\Windows\CurrentVersion\Run"`
- Detected a `.vbs` script added to the registry run key.

### Task 5: PowerShell Execution
- Investigated unusual execution patterns with:  
  `EventCode=1 Image="powershell.exe" ParentImage="explorer.exe"`
- Found evidence of PowerShell being used interactively by the logged-in user, indicating post-compromise activity.

---

## 🧠 IOCs Identified
- **IP Address**: `192.168.100.14`
- **Username**: `sysadmin1`
- **Suspicious Events**:  
  - Multiple failed login attempts (`4625`)  
  - Successful login (`4624`)  
  - Privilege escalation (`4672`)  
  - Registry modification for persistence (`13`)  
  - PowerShell execution (`1`)

---

## 🛡️ Detection Summary
A potential brute-force attack was launched from IP `192.168.100.14`, resulting in multiple failed login attempts. The attacker successfully authenticated as `sysadmin1` and immediately escalated privileges (`4672`). Post-login, persistence was achieved via a `.vbs` script added to the Run registry key. PowerShell execution was also observed, indicating command execution or payload delivery.

---

## 🧯 Recommendations
- 🚫 **Block** IP `192.168.100.14` and investigate its source.
- 🔐 **Reset credentials** for `sysadmin1` and audit all privileged accounts.
- 🧹 **Remove** malicious script from registry run key.
- 🛡️ **Enable logging** and alerts for registry and PowerShell events.
- ✅ **Implement account lockout policies** to prevent brute-force attacks.
- 🔍 Perform full host-based investigation on affected systems.

---

## 📸 Screenshot
![SIEM Investigation](../images/siem-fundamentals-example.png)
