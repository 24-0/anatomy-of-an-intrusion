# Anatomy of an Intrusion

An end-to-end SOC portfolio project that walks through the full life of an intrusion from the defender's side: building the monitoring stack, collecting endpoint and network telemetry, detecting suspicious activity, investigating alerts and documenting the response. Each phase adds one more SOC function.

## Project Goals
- Build a working SIEM-based detection environment on modest hardware
- Collect rich endpoint telemetry from a Windows machine
- Practice alert triage and investigation the way a SOC analyst would
- Document every phase clearly so the work can be reproduced

## Lab Environment

| Component | Details |
|---|---|
| Host | Windows laptop, AMD Ryzen 5 5500U, 8 GB RAM |
| Hypervisor | VMware Workstation 17 Player |
| SIEM VM | `wazuh-server` — Ubuntu Server 24.04, 4 GB RAM, 2 vCPU, 50 GB disk, NAT |
| Endpoint | Windows host with Wazuh agent `yash_here` and Sysmon |

## Architecture (Phase 1)

```
+---------------------------+            +-------------------------------+
| Windows laptop (host)     |  agent     | VMware VM: wazuh-server       |
|  - Wazuh agent yash_here  | ---------> |  - Wazuh manager              |
|  - Sysmon                 |            |  - Wazuh indexer              |
+---------------------------+            |  - Wazuh dashboard            |
                                         +-------------------------------+
```

## Roadmap

| Phase | Focus | Status |
|---|---|---|
| 1 | Wazuh SIEM, Windows agent, Sysmon telemetry, first alert review | Done |
| 2 | Network detection: Suricata on a separate sensor VM feeding Wazuh | Next |
| 3+ | Further SOC functions: detection rules, simulated attack activity, investigation and incident reporting | Planned |

## Phase 1 Summary
1. Created the Ubuntu Server VM in VMware and installed Wazuh (all-in-one).
2. Resolved a Wazuh API connection problem so the dashboard worked correctly.
3. Installed the Wazuh agent on the Windows laptop and registered it with the manager.
4. Installed Sysmon and configured the agent to read the Sysmon event log.
5. Confirmed Sysmon alerts appear in the Wazuh dashboard and began reviewing the first alert (rule 92058).

Detailed documentation:
- [01 – VM setup](docs/01-vm-setup.md)
- [02 – Wazuh installation](docs/02-wazuh-installation.md)
- [03 – Windows agent](docs/03-windows-agent.md)
- [04 – Sysmon integration](docs/04-sysmon-integration.md)
- [05 – First alert review](docs/05-first-alert-review.md)
- [06 – Troubleshooting & lessons learned](docs/06-troubleshooting.md)

## Skills Demonstrated
SIEM deployment · Windows endpoint telemetry (Sysmon) · Linux administration · virtualization and NAT networking · alert triage fundamentals · technical documentation

## Screenshots

Selected screenshots from the project are kept in the [`screenshots/`](screenshots/) folder.

<!-- Add images below, e.g. ![Description](screenshots/your-image.png) -->

## Disclaimer
Built for learning in an isolated personal lab. No credentials, keys or tokens are stored in this repository.
