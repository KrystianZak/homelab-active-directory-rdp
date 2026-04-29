# homelab-active-directory-rdp

Active Directory lab with centralized RDP access using GPO and RBAC.

## What this project shows

* Centralized RDP access via Group Policy
* Role-Based Access Control (RBAC)
* No manual configuration on endpoints

## Architecture

(images/architecture/architecture.png)

* Proxmox (virtualization)
* Windows Server (DC01)
* Windows 11 (client)

## Access Model (RBAC)

| Group            | Access                |
| ---------------- | --------------------- |
| IT_Admins        | Local Administrators  |
| RDP_Users        | Remote Desktop access |
| Accounting_Users | Department grouping   |

## GPO – Centralized Access

(images/gpo/gpo-local-groups-rbac.png)

* `IT_Admins` → Administrators
* `RDP_Users` → Remote Desktop Users

## Security Baseline

(images/gpo/gpo-security-baseline.png)

* Guest account disabled
* Last user hidden
* Session timeout (300s)

## Example Users

* IT Admin → `IT_Admins`, `RDP_Users`
* Accounting → `Accounting_Users`, `RDP_Users`
* Standard → `RDP_Users`

## Summary

Centralized Windows environment with RBAC and GPO automation.
