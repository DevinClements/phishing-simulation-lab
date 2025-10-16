# 🧪 HTA Phishing Payload Simulation

## 📌 Overview
This artifact captures a simulated phishing attack using a `.hta` (HTML Application) payload delivered via Thunderbird. The payload was manually executed to trigger telemetry via Sysmon on a hardened Windows 11 victim VM.

---

## 📁 Payload Details

- **Filename**: `phishing_payload.hta`
- **Type**: HTML Application
- **Delivery Method**: Email attachment (Thunderbird draft)
- **Execution Path**: Manual launch from File Explorer
- **Behavior**: Launches alert box or executes `notepad.exe` (depending on payload version)

---

## 🧠 Detection Evidence (Sysmon)

| Event ID | Description         | Observed Behavior                          |
|----------|---------------------|--------------------------------------------|
| **1**    | Process Creation    | `mshta.exe` launched with full command line |
| **3**    | Network Connection  | (Not triggered in this test)               |
| **11**   | File Creation Time  | (Optional, if payload drops files)         |
| **13**   | Registry Changes    | (Optional, if persistence is scripted)     |

Captured via:


## 📸 Screenshots

| File                     | Description                          |
|--------------------------|--------------------------------------|
| `thunderbird_email.png`  | Email draft with `.hta` attachment   |
| `smart_screen_prompt.png`| SmartScreen warning before execution |
| `sysmon_event_1.png`     | Logged execution of `mshta.exe`      |

---

## 🛡️ System Hardening (Victim VM)

- PowerShell ScriptBlock Logging enabled
- Sysmon installed with SwiftOnSecurity config
- Windows Defender temporarily disabled for payload execution
- Thunderbird configured with dummy account: `victim@lab.local`

---

## 🚀 Next Steps

- Embed PowerShell stager in `.hta` for deeper telemetry
- Simulate C2 traffic using Kali attacker VM
- Capture Event ID 3 (network) and 11 (file creation)
- Document full attack chain with Suricata alerts and SOC pipeline

---


