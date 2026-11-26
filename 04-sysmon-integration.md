# 04 – Sysmon Integration

Sysmon records detailed process creation, network connections and file activity that default Windows logging lacks.

## Install Sysmon
1. Download Sysmon from Microsoft Sysinternals.
2. Use a community configuration such as SwiftOnSecurity's `sysmon-config`.
3. In an elevated prompt:
   ```powershell
   .\Sysmon64.exe -accepteula -i sysmonconfig.xml
   ```

## Forward events to Wazuh
Add this block inside `<ossec_config>` in `C:\Program Files (x86)\ossec-agent\ossec.conf`:
```xml
<localfile>
  <location>Microsoft-Windows-Sysmon/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>
```
Restart the agent:
```powershell
Restart-Service -Name wazuh
```

## Verification
In the dashboard, filter events by the agent and search for `Sysmon` to confirm alerts are arriving.
