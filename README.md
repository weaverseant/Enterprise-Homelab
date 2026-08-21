# 🏢 Enterprise Home Lab

A hands-on enterprise networking and cybersecurity environment built to develop practical experience with **network engineering, systems administration, virtualization, identity management, network security, and troubleshooting**.

This lab combines physical Cisco networking equipment with virtualized servers, firewalls, Windows clients, and security services.

> **Status:** 🚧 Active Development — infrastructure and documentation are continuously being expanded.

---

## 🎯 Project Goals

The purpose of this home lab is to gain practical experience designing and administering an environment similar to a small enterprise network.

Key objectives include:

* Design segmented enterprise networks using VLANs
* Configure Layer 2 and Layer 3 Cisco switching
* Implement inter-VLAN routing
* Deploy and administer Windows Active Directory
* Manage users, groups, Organizational Units, and Group Policy
* Implement role-based access to network resources
* Deploy virtual infrastructure with Proxmox VE
* Configure firewalling and network segmentation with pfSense
* Implement centralized authentication using RADIUS/AAA
* Monitor systems and security events
* Practice troubleshooting across network, server, and security layers

---

## 🧱 Lab Infrastructure

### Physical Infrastructure

| Component           | Purpose                              |
| ------------------- | ------------------------------------ |
| Cisco Catalyst 3750 | Layer 2/3 enterprise switching       |
| TP-Link SG108E      | Managed access/aggregation switching |
| Lenovo ThinkCentre  | Proxmox virtualization host          |
| Lenovo ThinkCentre  | Administrative/client workstation    |
| AT&T Gateway        | Upstream Internet connectivity       |

### Virtual Infrastructure

**Proxmox VE** serves as the primary virtualization platform.

Current virtual systems include:

| System         | Role                                                      |
| -------------- | --------------------------------------------------------- |
| DC01           | Windows Server / Active Directory Domain Controller / DNS |
| WIN11-CLIENT   | Windows 11 domain workstation                             |
| pfSense        | Firewall and network segmentation                         |
| Ubuntu Server  | Linux services and administration                         |
| Ubuntu Desktop | Linux workstation/testing                                 |

Additional services are introduced as the environment expands.

---

## 🌐 Network Architecture

The lab uses multiple VLANs to simulate segmentation between different enterprise systems and departments.

| VLAN | Subnet          |
| ---: | --------------- |
|   10 | `10.10.10.0/24` |
|   20 | `10.10.20.0/24` |
|   30 | `10.10.30.0/24` |
|   40 | `10.10.40.0/24` |
|   50 | `10.10.50.0/24` |
|   60 | `10.10.60.0/24` |
|   70 | `10.10.70.0/24` |

Cisco switching is used to practice:

* VLAN creation and management
* 802.1Q trunking
* Layer 3 switching
* Inter-VLAN routing
* ACLs
* EtherChannel
* HSRP
* Port security
* Network troubleshooting

---

## 🪟 Active Directory Environment

The Windows environment currently includes:

**Domain Controller:** `DC01`

**Lab Domain:** `SeanHomeLab.local`

Current Active Directory work includes:

* Active Directory Domain Services
* Integrated DNS
* Domain-joined Windows 11 workstation
* Organizational Unit design
* Departmental users and security groups
* Group Policy Objects
* Workstation security policies
* Group-based resource authorization
* File server/share permissions

Example OU structure:

```text
SeanHomeLab.local
│
├── Admins
├── HR
├── IT
├── Sales
├── Servers
└── Workstations
```

---

## 🔐 Security

Security technologies and concepts implemented or planned in the environment include:

* pfSense firewall policies
* VLAN segmentation
* Active Directory authentication
* Role-based security groups
* Group Policy security baselines
* NTFS/share permissions
* RADIUS/AAA
* ACLs
* Wazuh SIEM
* Centralized logging and monitoring

---

## 📁 Project Documentation

This repository will contain dedicated documentation for each major part of the environment:

```text
Enterprise-HomeLab/
│
├── active-directory/
├── cisco-networking/
├── diagrams/
├── pfsense/
├── proxmox/
├── radius-aaa/
├── troubleshooting/
└── wazuh/
```

Each section will include configuration notes, implementation steps, screenshots, troubleshooting examples, and lessons learned where appropriate.

---

## 🧪 Current Project

### Active Directory Enterprise Deployment

Current work focuses on building an enterprise-style Windows domain environment.

Completed milestones include:

* ✅ Windows Server deployment
* ✅ Active Directory Domain Services
* ✅ DNS configuration
* ✅ `SeanHomeLab.local` domain
* ✅ Windows 11 domain join
* ✅ Domain user authentication
* ✅ Organizational Unit structure
* ✅ Security groups
* ✅ Group Policy deployment
* ✅ Verification of workstation GPO processing
* 🚧 Departmental file-share deployment
* ⏳ Automatic network-drive mapping
* ⏳ Additional departmental access controls

---

## 🛠️ Technologies

**Networking:** Cisco IOS • VLANs • 802.1Q • Layer 3 Switching • ACLs • HSRP • EtherChannel

**Virtualization:** Proxmox VE

**Microsoft:** Windows Server • Active Directory • DNS • Group Policy • Windows 11

**Firewall/Security:** pfSense • RADIUS/AAA • Wazuh • Network Segmentation

**Linux:** Ubuntu • Linux Administration

---

## 📈 Future Development

Planned additions include:

* Expanded Active Directory Group Policy deployment
* Department-specific network drives
* RADIUS authentication
* Centralized network authentication
* Wazuh security monitoring
* Additional firewall segmentation
* Network monitoring
* Infrastructure diagrams
* Configuration backups
* Failure and troubleshooting scenarios

---

## ⚠️ Security Notice

Configurations and screenshots published in this repository are sanitized for public viewing. Passwords, credentials, private keys, tokens, and other sensitive information are excluded.

---

## 👤 Author

**Sean Weaver**

Cybersecurity Student • Army Veteran • Aspiring Network Engineer

Cisco Certified Support Technician (CCST) Networking

Currently pursuing **CCNA** and **CompTIA Security+**.
