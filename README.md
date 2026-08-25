# SOC Capstone Project — Network Monitoring & Attack Detection Lab

A simulated Security Operations Center (SOC) environment built using virtual machines to demonstrate security monitoring, intrusion detection, and incident analysis. The lab integrates a firewall, an IDS, and a SIEM platform to detect and investigate simulated cyber attacks including port scanning and brute-force login attempts.

## Table of Contents

- [Project Overview](#project-overview)
- [Network Topology](#network-topology)
- [Tools and Technologies](#tools-and-technologies)
- [Configuration Steps](#configuration-steps)
- [Results and Findings](#results-and-findings)
- [Author](#author)

## Project Overview

The objective of this project was to design and implement a simulated SOC environment capable of detecting and analyzing real-world attack techniques. The lab combined a firewall (`pfSense`), a network-based intrusion detection system (`Suricata`), and a SIEM platform (`Wazuh`) to monitor traffic and endpoint activity across a Windows 10 victim machine and an Ubuntu attacker machine.

Two attacks were simulated — an **Nmap port scan** and an **SSH/Windows brute-force login attack** — to test the environment's detection and alerting capabilities. Both attacks were successfully identified, logged, and correlated across network and host-level sources, demonstrating the value of layered security monitoring in a SOC.

## Network Topology

The lab consisted of four virtual machines connected through VirtualBox internal and bridged networks:

- **pfSense (firewall/router)** — 4 network adapters: Bridged (WAN), Internal Network → LAN, Internal Network → DMZ, and Host-Only
- **Windows 10 (victim)** — connected via Internal Network → LAN, assigned IP `192.168.2.10`
- **Ubuntu (attacker)** — connected via Internal Network → LAN, assigned IP `192.168.2.11` / `192.168.2.12`
- **Wazuh (SIEM server)** — connected via Internal Network with a Bridged Adapter for dashboard access, reachable at `192.168.0.54`

pfSense acted as the central firewall controlling traffic between systems, with a custom firewall rule applied on the OPT2 interface to keep the web management interface accessible during testing. Connectivity between machines was verified using `ping` and `ip a` / `ipconfig` commands, confirming devices were correctly assigned IP addresses on the pfSense LAN network.

## Tools and Technologies

- **VirtualBox** — virtualization platform for hosting all lab machines
- **pfSense** — firewall/router controlling network traffic
- **Wazuh** — SIEM platform for log aggregation, alerting, and dashboards
- **Suricata** — network-based IDS/IPS for detecting malicious traffic
- **Windows 10** — victim/target machine
- **Ubuntu** — attacker machine
- **Nmap** — network scanning and reconnaissance tool
- **Hydra** — brute-force password auditing tool
- **Windows Event Viewer** — endpoint log review (Security event logs)

## Configuration Steps

1. Set up four virtual machines in VirtualBox: pfSense, Windows 10, Ubuntu, and Wazuh, with adapters configured as described in the Network Topology section.
2. Installed and configured pfSense with WAN and LAN interfaces to act as the central firewall/router.
3. Accessed the pfSense web interface via HTTPS and added a firewall rule on the OPT2 interface to prevent being locked out during testing.
4. Verified connectivity between the Ubuntu attacker machine and Windows victim machine using `ping` and confirmed IP assignments with `ip a` and `ipconfig`.
5. Installed Suricata on the Ubuntu machine and confirmed the service was active using `systemctl status suricata`.
6. Deployed the Wazuh SIEM server (OVA) and accessed its dashboard over HTTPS.
7. Installed Wazuh agents on both the Windows 10 and Ubuntu machines, registering the Wazuh manager address (`192.168.0.54`) so both machines began forwarding logs.
8. Verified both agents showed as active in the Wazuh Endpoints dashboard.
9. Simulated **Attack 1 — Nmap Scan**: ran `nmap -sS <Windows-IP>` from the Ubuntu attacker machine to identify open ports and services on the Windows target.
10. Simulated **Attack 2 — Brute Force**: ran `hydra -l user -P passwords.txt ssh://<target-ip>` to generate repeated failed login attempts against the target.
11. Reviewed Windows Event Viewer Security logs, filtering for Event ID `4625` (failed logon) to confirm the brute-force attempts were recorded locally.
12. Reviewed Wazuh Discover logs and dashboard alerts to confirm both attacks were detected and correlated across Suricata network alerts and Wazuh host-based logs.

## Results and Findings

- The Nmap scan generated detectable network traffic that was identified by Suricata and forwarded to Wazuh, which displayed alerts showing the source IP (attacker) and destination IP (target), confirming successful reconnaissance detection.
- The brute-force attack triggered multiple Event ID `4625` failed logon events on the Windows machine, which Wazuh successfully ingested and flagged as suspicious authentication activity.
- Correlating network-level logs (Suricata) with host-level logs (Wazuh agents on Windows and Ubuntu) provided clear visibility into both attacker and target activity, including source/destination IPs, timestamps, and event details.
- Challenges encountered included Wazuh agents initially failing to connect due to configuration issues, network misconfiguration between VMs, delayed alerting, and permission errors when running security tools. These were resolved by verifying agent configuration, correcting network adapter settings, adjusting Wazuh time filters, and using elevated (`sudo`) privileges.
- The project demonstrated the effectiveness of combining a firewall, IDS, and SIEM to detect reconnaissance and brute-force attacks, reinforcing the importance of layered, correlated monitoring in a SOC environment.
- Recommended improvements identified from the exercise include enforcing strong password policies, implementing account lockout mechanisms, applying network segmentation, tightening firewall rules, and maintaining continuous SIEM monitoring with regular patching.

## Author

**Tapiwa Muyengwa**
Cybersecurity Professional | Purple Team Mindset | Networking, SOC, GRC & Pen Testing

- LinkedIn: [linkedin.com/in/tapiwa-muyengwa-64a9a3320](https://linkedin.com/in/tapiwa-muyengwa-64a9a3320)
- Email: `Muyengwataps@gmail.com`
