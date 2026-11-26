# 02 – Wazuh Installation (All-in-One)

The all-in-one install puts the manager, indexer and dashboard on one host, which suits a small lab.

## Install
Check the official Wazuh quickstart for the current script URL, then run:
```bash
curl -sO https://packages.wazuh.com/4.x/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```
The installer prints the admin credentials at the end. **Store them in a password manager and never commit them to GitHub.**

## Access the dashboard
From the host browser open `https://<VM-IP>`, accept the self-signed certificate warning and log in as `admin`.

## Verify services
```bash
sudo systemctl status wazuh-manager wazuh-indexer wazuh-dashboard
```
All three should show `active (running)`.
