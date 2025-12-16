# Hybrid Active Directory Lab: Windows Server 2022 & RHEL 9 Integration

## 🎯 Objective
To simulate a real-world enterprise environment where many operating systems (Windows & Linux) must be managed centrally. The goal was to deploy a Domain Controller, enforce security policies, and enable Linux servers to authenticate against Active Directory.

## 🛠 Skills Learned
- **System Administration:** Windows Server 2022, Active Directory Domain Services (AD DS).
- **Security:** Implementing Group Policy Objects (GPO) to harden endpoints.
- **Integration:** Configuring SSSD and Realmd to join RHEL/Rocky Linux to a Windows domain.
- **Virtualization:** Managing resources in Proxmox VE.

## 💻 Technologies
- Windows Server 2022 (Domain Controller)
- Rocky Linux 9 (Client)
- Proxmox VE (Hypervisor)

## 📝 Steps Performed

### 1. Domain Controller Deployment
- Installed Windows Server 2022 on Proxmox using VirtIO drivers for performance.
- Promoted server to a **Domain Controller**, establishing the new forest `corp.local`.
- Configured static IP and DNS settings to ensure stable connectivity.

![Domain Controller Setup](INSERT_IMAGE_LINK_HERE)

### 2. Security Policy Configuration (GPO)
- Created a dedicated Organizational Unit (OU) and User Accounts for testing.
- Designed a "Block Control Panel" Group Policy Object (GPO) to restrict user access to system settings.
- Verified policy application using `gpupdate /force`.

![GPO Configuration](INSERT_IMAGE_LINK_HERE)

### 3. Linux Integration (The Bridge)
- Configured Rocky Linux 9 networking to point to the Windows DC for DNS resolution.
- Installed necessary packages: `realmd`, `sssd`, `oddjob`, `adcli`.
- Successfully joined the Linux host to the domain using `realm join`.

![Linux Join Command](INSERT_IMAGE_LINK_HERE)

## 🏆 The Result
- Successfully verified that a Windows Active Directory user could authenticate on the Linux server.
- The `id` command confirms the user `hunter@corp.local` is recognized by the Linux system.

![Final Verification](INSERT_IMAGE_LINK_HERE)
