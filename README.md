# homelab-active-directory-rdp

Active Directory lab demonstrating centralized RDP access using Group Policy and RBAC.

---

## Overview

- Centralized RDP access via GPO
- Role-Based Access Control (RBAC)
- No manual configuration on endpoints

---

## Architecture

![Architecture](images/architecture/architecture.png)

- Proxmox (virtualization)
- DC01 – Windows Server (Domain Controller)
- WS01 – Windows 11 (client)

---

## RBAC Model

| Group            | Access                    |
|------------------|--------------------------|
| IT_Admins        | Local Administrators     |
| RDP_Users        | Remote Desktop access    |
| Accounting_Users | Department-level grouping|

---

## GPO Configuration

![GPO RBAC](images/gpo/gpo-local-groups-rbac.png)

Centralized group assignment via GPO:

- `IT_Admins` → Local Administrators
- `RDP_Users` → Remote Desktop Users

---

## Security Baseline

![Security Baseline](images/gpo/gpo-security-baseline.png)

- Guest account disabled
- Last logged-in user hidden
- Session timeout: 300 seconds

---

## Example Access

- IT Admin → `IT_Admins`, `RDP_Users`
- Accounting User → `Accounting_Users`, `RDP_Users`
- Standard User → `RDP_Users`

---

## Result

- Users gain RDP access through group membership only
- No local configuration required
- Fully centralized access control via GPO
