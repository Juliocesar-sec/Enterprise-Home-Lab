# Enterprise-Home-Lab

🚀 Enterprise Home Lab & Network Portfolio
==========================================

> Advanced Home Lab / Small Office Infrastructure built with MikroTik, Proxmox, Docker, VLAN Segmentation, Security Monitoring, and High Availability services.

📖 Overview
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

🧠 Architecture
===============

Physical Infrastructure
-----------------------

Device

Purpose

MikroTik RB5009UG+S+IN

Core Router / Firewall

MikroTik CSS610-8G-2S+IN

Layer 2 Core Switch

Lenovo ThinkPad T470

Proxmox Virtualization Host

TP-Link SFT1200

Wi-Fi Access Layer

External USB Drive / NAS

Backup Storage

🌐 Network Topology
===================

                        INTERNET
                             │
                    ┌────────────────┐
                    │ MikroTik       │
                    │ RB5009UG+S+IN │
                    │ Router/Firewall│
                    └────────────────┘
                             │
                     SFP+ 10G Uplink
                             │
                    ┌────────────────┐
                    │ MikroTik       │
                    │ CSS610-8G-2S+ │
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
                         │ Virtual Machines & Containers │
                         └────────────────────────────────┘
    

🧩 VLAN Design
==============

VLAN

Name

Subnet

Purpose

10

Management

10.10.10.0/24

Network devices and monitoring

20

Servers

10.10.20.0/24

VMs, Docker, NAS

30

IoT

10.10.30.0/24

Smart home devices

40

Cameras

10.10.40.0/24

CCTV / NVR

50

Guest

10.10.50.0/24

Guest Wi-Fi

60

VPN

10.10.60.0/24

WireGuard clients

🖥️ Virtualization Stack
========================

Hypervisor
----------

-   Proxmox VE
-   KVM Virtualization
-   LXC Containers
-   ZFS-ready architecture
-   Scheduled snapshots

📦 Virtual Machines
===================

VM 1 — Docker Host
------------------

### OS

-   Ubuntu Server 22.04 LTS

### Services

-   Docker
-   Portainer
-   WireGuard
-   Nginx Proxy Manager
-   AdGuard Home
-   Uptime Kuma
-   Watchtower

### Purpose

Main lightweight container host for infrastructure services.

VM 2 — Home Assistant
---------------------

### OS

-   Home Assistant OS

### Purpose

Smart home automation platform with isolated VM deployment.

### Features

-   Zigbee support
-   Bluetooth integration
-   Add-ons
-   Automations
-   MQTT

VM 3 — Security / IDS
---------------------

### OS

-   Ubuntu Server

### Services

-   Suricata IDS
-   CrowdSec
-   Wazuh Agent
-   Zeek (optional)

### Purpose

Network traffic inspection and intrusion detection.

VM 4 — Observability & SIEM
---------------------------

### Services

-   Wazuh
-   OpenSearch
-   Dashboards
-   Syslog aggregation

### Purpose

Centralized logging, monitoring, and security analytics.

VM 5 — Media Server
-------------------

### Services

-   Jellyfin

### Features

-   Intel QuickSync transcoding
-   Local media streaming
-   Remote access

VM 6 — Backup Server
--------------------

### Services

-   Proxmox Backup Server
-   Restic
-   BorgBackup

### Purpose

Snapshots, VM backups, and disaster recovery.

🔒 Security Features
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

🐳 Docker Containers
====================

Container

Purpose

Nginx Proxy Manager

Reverse proxy

AdGuard Home

DNS filtering

WireGuard

VPN server

Portainer

Docker management

Uptime Kuma

Monitoring

Watchtower

Automatic updates

Cloudflared

Secure tunneling

📊 Observability Stack
======================

Tool

Function

Wazuh

SIEM

Suricata

IDS

OpenSearch

Log indexing

Dashboards

Visualization

Uptime Kuma

Health checks

📡 Network Services
===================

Core Services
-------------

-   DHCP
-   DNS forwarding
-   VLAN routing
-   QoS
-   WAN failover
-   Multi-WAN support

Reverse Proxy
-------------

-   SSL termination
-   HTTPS exposure
-   Internal routing
-   Access control

💾 Backup Strategy
==================

Local Backups
-------------

-   Daily Proxmox snapshots
-   Incremental backups
-   External USB storage

Disaster Recovery
-----------------

-   VM restore testing
-   Configuration exports
-   Encrypted backup retention

⚙️ Future Improvements
======================

-   2.5GbE upgrade
-   Wi-Fi 7 migration
-   High Availability cluster
-   Kubernetes integration
-   NAS replication
-   Hardware IDS appliance
-   SFP+ aggregation

🛠️ Technologies Used
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

📷 Screenshots
==============

Network Topology
----------------

    /assets/network-topology.png
    

Proxmox Dashboard
-----------------

    /assets/proxmox-dashboard.png
    

Wazuh Dashboard
---------------

    /assets/wazuh-dashboard.png
    

📚 Learning Goals
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

👨‍💻 Author
============

Infrastructure and security enthusiast focused on:

-   Networking
-   Virtualization
-   Cybersecurity
-   Self-hosted infrastructure
-   Enterprise home labs

⭐ Project Status
================

🟢 Active Development
🟢 Production Ready
🟢 Continuous Improvements
