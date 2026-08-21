# Active Directory Enterprise Lab

## Overview

This project demonstrates the deployment and administration of a Microsoft Active Directory domain in a virtualized enterprise-style homelab environment.

The lab was built using Proxmox VE and includes a Windows Server Domain Controller and a Windows 11 client workstation. The environment was designed to provide hands-on experience with Active Directory, DNS, organizational units, user and group administration, domain authentication, and Group Policy.

## Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | Proxmox VE |
| Domain Controller | Windows Server - DC01 |
| Client | Windows 11 - CLT-W11-01 |
| Domain | SeanHomelab.local |
| Directory Service | Active Directory Domain Services |
| DNS | Windows Server DNS |
| Policy Management | Group Policy Management |

## Active Directory Structure

The `SeanHomelab.local` domain was organized using Organizational Units (OUs) to simulate an enterprise directory structure.

Organizational Units created include:

- Admins
- HR
- IT
- Sales
- Servers
- Workstations

This structure allows users, computers, and policies to be organized based on their organizational role.

## User and Group Management

A domain user account was created and managed through Active Directory Users and Computers.

Example configuration:

- User: Sean Weaver
- Department OU: IT
- Security Group: IT-Staff
- Authentication: Active Directory domain credentials

The user was successfully authenticated from a domain-joined Windows 11 workstation.

## Windows 11 Domain Integration

A Windows 11 virtual machine was configured as an enterprise client workstation.

The workstation was:

1. Configured to communicate with the Domain Controller.
2. Joined to the `SeanHomelab.local` domain.
3. Added to the `Workstations` Organizational Unit.
4. Restarted to complete domain enrollment.
5. Tested using domain-user authentication.

The workstation appears in Active Directory as:

`CLT-W11-01`

Domain authentication was verified using:

`whoami`

Example result:

`seanhomelab\sweaver`

## Group Policy Management

Group Policy Management was configured to centrally manage workstation security.

A dedicated Group Policy Object was created:

`GPO-Workstation-Security-Baseline`

The GPO was linked to the `Workstations` OU so that security settings automatically apply to domain workstations placed inside the OU.

This demonstrates centralized administration rather than configuring security settings independently on every workstation.

## Security Baseline

The workstation security GPO was configured through:

Computer Configuration  
→ Policies  
→ Windows Settings  
→ Security Settings  
→ Local Policies  
→ Security Options

Security settings were configured to demonstrate centralized workstation hardening.

One example implemented in the lab was an automatic workstation lock using the Windows machine inactivity policy.

## Group Policy Deployment and Verification

After configuring the GPO, policies were refreshed on the Windows 11 client using:

`gpupdate /force`

Windows confirmed that both Computer Policy and User Policy updates completed successfully.

Policy application was then verified using:

`gpresult`

The workstation successfully reported:

`GPO-Workstation-Security-Baseline`

under Applied Group Policy Objects.

This confirmed that the Domain Controller successfully delivered the security policy to the Windows 11 workstation.

## Troubleshooting

Several issues were encountered and resolved during deployment.

### Domain Authentication

Domain-user login initially failed.

Troubleshooting included:

- Verifying the user existed in Active Directory
- Confirming domain membership
- Resetting/verifying domain credentials
- Confirming communication with the Domain Controller

Domain authentication was ultimately successful.

### Group Policy Verification

Running computer-level `gpresult` from a standard command prompt resulted in:

`ERROR: Access Denied.`

The command was then executed from an elevated Administrator Command Prompt.

This allowed computer-level Group Policy information to be viewed successfully.

### Policy Application

Initially, user-level `gpresult` did not display the workstation GPO.

Further investigation showed that the security baseline was a computer policy linked to the `Workstations` OU.

Running computer-level policy results confirmed that the GPO was correctly applied to `CLT-W11-01`.

## Skills Demonstrated

This project demonstrates hands-on experience with:

- Microsoft Active Directory
- Windows Server administration
- Active Directory Domain Services
- DNS
- Organizational Units
- User and group administration
- Domain authentication
- Windows domain joining
- Group Policy Objects
- Group Policy Management
- Security policy deployment
- Windows workstation administration
- Proxmox virtualization
- Enterprise infrastructure concepts
- Command-line troubleshooting
- Identity and access management
- Technical troubleshooting

## Architecture

The simplified environment follows this design:

Proxmox VE  
├── DC01 - Windows Server / Domain Controller  
│   ├── Active Directory Domain Services  
│   ├── DNS  
│   └── Group Policy Management  
│  
└── CLT-W11-01 - Windows 11 Workstation  
    ├── Joined to SeanHomelab.local  
    ├── Domain User Authentication  
    └── Receives Centralized Group Policy

## Project Status

**Active / Continuing Development**

Future improvements will expand the environment with additional enterprise services, security controls, network segmentation, centralized authentication, monitoring, and additional client/server systems.
