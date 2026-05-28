#  <h2 align="center">Enterprise-Home-Lab</h2>

<!-- Enterprise-Home-Lab Badges -->
<p align="center">

<a href="https://mikrotik.com/" target="_blank">
  <img src="https://img.shields.io/badge/MikroTik-RouterOS%20v7-293239?style=flat-square&logo=mikrotik&logoColor=white" height="30">
</a>

<a href="https://www.proxmox.com/" target="_blank">
  <img src="https://img.shields.io/badge/Proxmox-Virtualization-E57000?style=flat-square&logo=proxmox&logoColor=white" height="30">
</a>

<a href="https://www.docker.com/" target="_blank">
  <img src="https://img.shields.io/badge/Docker-Containerized%20Services-2496ED?style=flat-square&logo=docker&logoColor=white" height="30">
</a>

<a href="https://www.wireguard.com/" target="_blank">
  <img src="https://img.shields.io/badge/WireGuard-Secure%20VPN-88171A?style=flat-square&logo=wireguard&logoColor=white" height="30">
</a>

<a href="https://wazuh.com/" target="_blank">
  <img src="https://img.shields.io/badge/Wazuh-SIEM%20Monitoring-005E9C?style=flat-square&logo=wazuh&logoColor=white" height="30">
</a>

<a href="https://suricata.io/" target="_blank">
  <img src="https://img.shields.io/badge/Suricata-IDS%2FIPS-EF3B2D?style=flat-square&logo=suricata&logoColor=white" height="30">
</a>

<a href="https://www.opensearch.org/" target="_blank">
  <img src="https://img.shields.io/badge/OpenSearch-Observability%20Stack-005EB8?style=flat-square&logo=opensearch&logoColor=white" height="30">
</a>

<a href="https://www.portainer.io/" target="_blank">
  <img src="https://img.shields.io/badge/Portainer-Container%20Management-13BEF9?style=flat-square&logo=portainer&logoColor=white" height="30">
</a>

<a href="https://www.home-assistant.io/" target="_blank">
  <img src="https://img.shields.io/badge/Home%20Assistant-Automation-41BDF5?style=flat-square&logo=homeassistant&logoColor=white" height="30">
</a>

<a href="https://github.com/Juliocesar-sec/Enterprise-Home-Lab" target="_blank">
  <img src="https://img.shields.io/badge/Status-Production%20Ready-success?style=flat-square" height="30">
</a>

</p>

 Enterprise Home Lab & Network Portfolio
==========================================

> Advanced Home Lab / Small Office Infrastructure built with MikroTik, Proxmox, Docker, VLAN Segmentation, Security Monitoring, and High Availability services.

![Architecture-Design](https://github.com/Juliocesar-sec/Enterprise-Home-Lab/blob/bc6c083219acb8331983a9803698a3b9b82fb665/Architecture-Design/Topology/HomeLab.png)

About This Project
====================

Enterprise-Home-Lab is a production-inspired infrastructure project designed to simulate modern enterprise networking, virtualization, and security operations within a home lab environment.

The lab combines advanced routing, VLAN segmentation, virtualization, containerization, monitoring, and cybersecurity tooling into a unified self-hosted platform built for both learning and real-world operational experience.

The environment was developed using enterprise concepts and best practices, including:

- Network segmentation and isolation
- Infrastructure virtualization with Proxmox VE
- Containerized service deployment with Docker
- SIEM and IDS/IPS monitoring
- Secure remote access using WireGuard
- Reverse proxy and SSL management
- Automated backups and disaster recovery
- Observability and centralized logging

This project serves as both:

- A personal infrastructure platform for self-hosted services
- A technical portfolio demonstrating hands-on networking and security skills

The architecture is continuously improved to explore enterprise technologies such as high availability, automation, monitoring, and scalable infrastructure design.


 Overview
===========

This project showcases a modern enterprise-inspired home lab architecture focused on:

-   Advanced routing and firewalling
-   Network segmentation with VLANs
-   Virtualization using Proxmox VE
-   Containerized services with Docker
-   Security monitoring and IDS/IPS
-   VPN remote access with WireGuard
-   Observability and centralized logging
-   Backup and disaster recovery
-   Reverse proxy and secure exposure

The environment was designed for:

-   Learning enterprise networking
-   Cybersecurity practice
-   Infrastructure automation
-   Self-hosted services
-   Home automation
-   Media streaming
-   SIEM and monitoring labs

Inspired by professional network portfolios and homelab documentation practices.

 Architecture
===============

Physical Infrastructure
-----------------------

| Device                   | Role                        | Description                                                   |
| ------------------------ | --------------------------- | ------------------------------------------------------------- |
| MikroTik RB5009UG+S+IN   | Core Router / Firewall      | Main routing, firewalling, VLAN segmentation, and VPN gateway |
| MikroTik CSS610-8G-2S+IN | Layer 2 Core Switch         | VLAN-aware switching and 10G SFP+ uplink aggregation          |
| Lenovo ThinkCentre m910  | Proxmox Virtualization Host | Hosts VMs, containers, and infrastructure services            |
| TP-Link SFT1200          | Wi-Fi Access Layer          | Edge connectivity for wireless and IoT devices                |
| External USB Drive / NAS | Backup Storage              | VM snapshots, backups, and disaster recovery storage          |

 Network Topology
===================

                        INTERNET
                             │
                    ┌────────────────┐
                    │ MikroTik       │
                    │ RB5009UG+S+IN  │
                    │ Router/Firewall│
                    └────────────────┘
                             │
                     SFP+ 10G Uplink
                             │
                    ┌────────────────┐
                    │ MikroTik       │
                    │ CSS610-8G-2S+  │
                    │ Core Switch    │
                    └────────────────┘
                      │      │      │
                      │      │      └── Wi-Fi / IoT
                      │      │
                      │      └──────── NAS
                      │
                      └────────────── Proxmox Host
                                          │
                         ┌────────────────────────────────┐
                         │ Virtual Machines & Containers  │
                         └────────────────────────────────┘
    

 VLAN Design
==============

| VLAN ID | Name       | Subnet          | Purpose                        |
| ------- | ---------- | --------------- | ------------------------------ |
| 10      | Management | `10.10.10.0/24` | Network devices and monitoring |
| 20      | Servers    | `10.10.20.0/24` | VMs, Docker, NAS               |
| 30      | IoT        | `10.10.30.0/24` | Smart home devices             |
| 40      | Cameras    | `10.10.40.0/24` | CCTV / NVR                     |
| 50      | Guest      | `10.10.50.0/24` | Guest Wi-Fi                    |
| 60      | VPN        | `10.10.60.0/24` | WireGuard clients              |


 Virtualization Stack
========================

Hypervisor
----------

-   Proxmox VE
-   KVM Virtualization
-   LXC Containers
-   ZFS-ready architecture
-   Scheduled snapshots

 Virtual Machines
===================

VM 1 — Docker Host
------------------

| Category | Details                                                                                  |
| -------- | ---------------------------------------------------------------------------------------- |
| OS       | Ubuntu Server 22.04 LTS                                                                  |
| Services | Docker, Portainer, WireGuard, Nginx Proxy Manager, AdGuard Home, Uptime Kuma, Watchtower |
| Purpose  | Main lightweight container host for infrastructure services                              |


VM 2 — Home Assistant
---------------------

| Category | Details                                       |
| -------- | --------------------------------------------- |
| OS       | Home Assistant OS                             |
| Purpose  | Smart home automation platform                |
| Features | Zigbee, Bluetooth, MQTT, Add-ons, Automations |


VM 3 — Security / IDS
---------------------

| Category | Details                                    |
| -------- | ------------------------------------------ |
| OS       | Ubuntu Server                              |
| Services | Suricata IDS, CrowdSec, Wazuh Agent, Zeek  |
| Purpose  | Intrusion detection and traffic inspection |


VM 4 — Observability & SIEM
---------------------------

| Category | Details                                    |
| -------- | ------------------------------------------ |
| Services | Wazuh, OpenSearch, Dashboards, Syslog      |
| Purpose  | Centralized logging and security analytics |


VM 5 — Media Server
-------------------

| Category | Details                                       |
| -------- | --------------------------------------------- |
| Services | Jellyfin                                      |
| Features | Intel QuickSync transcoding, remote streaming |
| Purpose  | Media streaming platform                      |


VM 6 — Backup Server
--------------------

| Category | Details                                   |
| -------- | ----------------------------------------- |
| Services | Proxmox Backup Server, Restic, BorgBackup |
| Purpose  | Disaster recovery and VM backups          |


 Security Features
====================

Router Security
---------------

-   Stateful firewall
-   NAT filtering
-   Geo-blocking
-   VLAN isolation
-   Port forwarding restrictions
-   Policy routing

Monitoring
----------

-   IDS/IPS
-   SIEM logging
-   Service monitoring
-   Traffic inspection

VPN
---

-   WireGuard remote access
-   Secure remote administration
-   Encrypted site-to-site connectivity

 Docker Containers
====================

| Container           | Purpose                                |
| ------------------- | -------------------------------------- |
| Nginx Proxy Manager | Reverse proxy and SSL management       |
| AdGuard Home        | DNS filtering and ad blocking          |
| WireGuard           | VPN server for remote access           |
| Portainer           | Docker container management            |
| Uptime Kuma         | Service monitoring and uptime checks   |
| Watchtower          | Automatic container updates            |
| Cloudflared         | Secure tunneling and external exposure |



 Observability Stack
======================

| Tool        | Function                    |
| ----------- | --------------------------- |
| Wazuh       | SIEM and security analytics |
| Suricata    | IDS/IPS network inspection  |
| OpenSearch  | Log indexing and search     |
| Dashboards  | Visualization and analytics |
| Uptime Kuma | Service health monitoring   |


 Network Services
===================

Core Services
-------------

| Service        | Description                      |
| -------------- | -------------------------------- |
| DHCP           | Dynamic IP address allocation    |
| DNS Forwarding | Internal DNS resolution          |
| VLAN Routing   | Inter-VLAN communication control |
| QoS            | Traffic prioritization           |
| WAN Failover   | Automatic WAN redundancy         |
| Multi-WAN      | Load balancing and resiliency    |


Reverse Proxy
-------------

| Feature          | Purpose                         |
| ---------------- | ------------------------------- |
| SSL Termination  | HTTPS encryption handling       |
| HTTPS Exposure   | Secure public access            |
| Internal Routing | Service forwarding              |
| Access Control   | Authentication and restrictions |


 Backup Strategy
==================

Local Backups
-------------

| Method               | Description                    |
| -------------------- | ------------------------------ |
| Daily Snapshots      | Automated Proxmox VM snapshots |
| Incremental Backups  | Reduced storage consumption    |
| External USB Storage | Offline backup retention       |


Disaster Recovery
-----------------

| Strategy              | Description                 |
| --------------------- | --------------------------- |
| VM Restore Testing    | Backup validation           |
| Configuration Exports | Router and service recovery |
| Encrypted Retention   | Secure backup storage       |

 Future Improvements
======================

-   2.5GbE upgrade
-   Wi-Fi 7 migration
-   High Availability cluster
-   Kubernetes integration
-   NAS replication
-   Hardware IDS appliance
-   SFP+ aggregation
 Technologies Used
=====================

Networking
----------

-   RouterOS v7
-   SwOS
-   VLANs
-   WireGuard
-   SFP+

Virtualization
--------------

-   Proxmox VE
-   KVM
-   LXC

Security
--------

-   Wazuh
-   Suricata
-   CrowdSec

Containers
----------

-   Docker
-   Portainer
-   Nginx Proxy Manager

Monitoring
----------

-   OpenSearch
-   Dashboards
-   Uptime Kuma

 Screenshots
==============

Network Topology
----------------

![NetworkTopology](https://github.com/Juliocesar-sec/Enterprise-Home-Lab/blob/a56fd1fc35ed7d0569c39e79cd373b8efa2f9793/Architecture-Design/Topology/network_topology.png)
    

Proxmox Dashboard
-----------------

    /assets/proxmox-dashboard.png
    

Wazuh Dashboard
---------------

    /assets/wazuh-dashboard.png
    

 Learning Goals
=================

This environment was built to improve skills in:

-   Enterprise networking
-   VLAN architecture
-   Virtualization
-   Cybersecurity
-   SIEM implementation
-   IDS/IPS monitoring
-   Infrastructure hardening
-   Linux administration
-   Reverse proxying
-   Self-hosted services

 Author
============

Infrastructure and security enthusiast focused on:

-   Networking
-   Virtualization
-   Cybersecurity
-   Self-hosted infrastructure
-   Enterprise home labs

 Project Status
================

🟢 Active Development
🟢 Production Ready
🟢 Continuous Improvements
