# WireGuard VPN + Dynamic DNS + Automatic Updates on Raspberry Pi 4

## Overview
This project sets up a secure WireGuard VPN server on a Raspberry Pi 4 (2GB RAM) to allow remote access to a home network. It includes a Dynamic DNS (DDNS) client to handle IP changes and a script to automate system updates to keep the server secure.

## Features
- WireGuard VPN server configuration with key generation and firewall rules
- DDNS client script to update public IP automatically (supports DuckDNS/No-IP)
- Automatic system update script with logging and cron scheduling
- Network diagram and firewall configuration documentation included

## Prerequisites
- Raspberry Pi 4 or any computer that you will let run 24/7 
- Public-facing router with port forwarding enabled (UDP 51820)
- DDNS account with DuckDNS or No-IP

## Setup Instructions

### 1. WireGuard VPN
- Run `wget https://git.io/wireguard -O wireguard-install.sh && bash wireguard-install.sh` to install and configure WireGuard
- Thanks to this github link https://github.com/Nyr/wireguard-install

### 2. Dynamic DNS
- Edit `ddns/ddns-update.sh` with your DDNS provider token and domain
- Set up cron job using `ddns/ddns-cronjob.sh` to run every 5 minutes

### 3. Automatic Updates
- Use `auto-updates/update-script.sh` to run system updates and log output
- Schedule with cron via `auto-updates/update-cronjob.sh` for daily updates

## Usage
- Connect to your VPN remotely using the client config
- Monitor update logs in `/var/log/wireguard-update.log`
- View your current public IP at your DDNS dashboard

## Network Diagram
![Network Diagram](docs/network_diagram.png)

## Firewall Rules
See detailed rules in [docs/firewall-rules.md](docs/firewall-rules.md)

## License
MIT License

