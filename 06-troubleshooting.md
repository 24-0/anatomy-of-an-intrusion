# 06 – Troubleshooting & Lessons Learned

- **Wazuh API connection error in the dashboard:** the dashboard could not reach the Wazuh API at first; it was resolved during Phase 1 and the dashboard has worked since.
- **Limited RAM (8 GB):** with the SIEM VM running, free host memory gets tight. Keep the VM at 4 GB and close unneeded apps.
- **Disk space:** keep VM files off cloud-synced folders to avoid sync errors and full storage.
- **Agent not connecting:** confirm the VM IP, that the host and VM share the NAT network, and that the Wazuh services are running.
- **Sysmon events missing:** check the `localfile` block is inside `<ossec_config>` and that the agent was restarted.
- **After a network or VMware network reset:** the NAT subnet and VM IPs may change. Re-check the VM IP with `ip a`, update the manager address in the agent's `ossec.conf`, and restart the agent.
