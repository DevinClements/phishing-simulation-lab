# HTA Phishing Payload Simulation

## 📌 Overview
Simulated phishing delivery using a `.hta` payload attached to a Thunderbird email. Executed manually to trigger telemetry via Sysmon.

## 🧪 Payload Details
- **Filename**: `phishing_payload.hta`
- **Type**: HTML Application
- **Behavior**: Launches alert box or executes `notepad.exe`
- **Execution Path**: Manual launch from File Explorer

## 🧠 Detection Evidence
- **SmartScreen Prompt**: Warned about unknown publisher
- **Sysmon Event ID 1**: Logged `mshta.exe` execution
- **No outbound traffic** (for this test)

## 📸 Artifacts
| Artifact              | Description                          |
|-----------------------|--------------------------------------|
| `phishing_payload.hta`| Payload file                         |
| `smart_screen_prompt.png` | Execution warning dialog         |
| `sysmon_event_1.png`  | Process creation log (`mshta.exe`)   |
| `thunderbird_email.png` | Email with attached payload        |

## 🛡️ Next Steps
- Embed PowerShell stager in `.hta`
- Simulate C2 traffic with Kali
- Capture Event ID 3 (network) and 11 (file creation)
