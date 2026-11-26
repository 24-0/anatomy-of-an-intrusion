# 03 – Windows Agent Enrollment

## Steps
1. In the dashboard open **Agents → Deploy new agent**.
2. Select **Windows**, enter the Wazuh server IP and the agent name `yash_here`.
3. Run the generated commands in an **elevated** PowerShell window on the laptop.
4. Start the service:
   ```powershell
   NET START WazuhSvc
   ```

## Verification
- The dashboard shows the agent as **Active**.
- `C:\Program Files (x86)\ossec-agent\ossec.log` shows a successful connection to the server.
