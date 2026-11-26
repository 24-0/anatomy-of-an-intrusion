# 01 – VM Setup

## Requirements
- VMware Workstation 17 Player
- Ubuntu Server 24.04 LTS ISO
- Enough free disk space (keep the VM outside cloud-synced folders such as OneDrive)

## VM Configuration
| Setting | Value |
|---|---|
| Name | wazuh-server |
| RAM | 4 GB |
| CPUs | 2 |
| Disk | 50 GB |
| Network | NAT |

## Steps
1. In VMware Player choose **Create a New Virtual Machine** and select the Ubuntu Server ISO.
2. Set the name, a storage location outside OneDrive, and the resources above.
3. Install Ubuntu Server with defaults, enabling **OpenSSH server**.
4. After first boot, update the system:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
5. Note the VM's IP address:
   ```bash
   ip a
   ```
