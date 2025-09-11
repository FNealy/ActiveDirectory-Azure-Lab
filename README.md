# 🖥️ Active Directory Domain Services Lab (Azure)

## 🔹 Overview
This project demonstrates the deployment and configuration of an **Active Directory Domain Services (AD DS) lab environment** in Microsoft Azure.  
The goal is to simulate a small business IT environment where users, groups, and computers are centrally managed through a domain controller.

---

## 🔹 Architecture
- **Azure Virtual Network (VNet)**
  - Subnet: `10.0.0.0/24`
- **Virtual Machines**
  - `DC-1` (Windows Server 2019 → Domain Controller + DNS)
  - `Client-1` (Windows 10 → Domain-joined workstation)

---

## 🔹 Features Implemented
✅ Active Directory Domain Services installation  
✅ DNS configuration for internal name resolution  
✅ User & Group account creation  
✅ Client domain join (`mycompany.local`)  
✅ Group Policy Objects (GPOs) for password policy + wallpaper enforcement  
✅ File share with NTFS permissions based on AD groups  

---

## 🔹 Implementation Steps

### 1. Create Virtual Machines in Azure
- Deployed `DC-1` (Windows Server 2019).
- Deployed `Client-1` (Windows 10).
- Both joined to the same VNet.
- Assigned static private IP to `DC-1`.
<img width="1160" height="280" alt="Screen Shot 2025-09-10 at 5 16 00 PM" src="https://github.com/user-attachments/assets/b068725e-ee14-47ea-ab73-8d0776abfbfe" />
<img width="563" height="170" alt="Screen Shot 2025-09-10 at 5 18 07 PM" src="https://github.com/user-attachments/assets/f0609dfa-33ef-45c9-a083-340dac2f9c82" />



---

### 2. Install Active Directory Domain Services
- Added the **AD DS** role in Server Manager.
- Promoted `DC-1` to a domain controller → `mycompany.local`.
<img width="1440" height="900" alt="Screen Shot 2025-09-10 at 5 25 29 PM" src="https://github.com/user-attachments/assets/c9647014-781e-4f94-980a-346c88ea294d" />

<img width="509" height="405" alt="Screen Shot 2025-09-10 at 5 28 02 PM" src="https://github.com/user-attachments/assets/f9aa8b82-0477-4121-b74e-4f9b3da6412a" />

---

### 3. Configure DNS
- Configured `DC-1` as DNS server.
- Set Client-1 DNS → DC-1 private IP.
<img width="1440" height="900" alt="Screen Shot 2025-09-10 at 5 34 29 PM" src="https://github.com/user-attachments/assets/a90cbeaa-bed9-4f74-bde7-35a6f05639a5" />

<img width="845" height="646" alt="Screen Shot 2025-09-10 at 5 42 23 PM" src="https://github.com/user-attachments/assets/0b3b8ab7-87f5-4e93-86f0-eccc90c82b32" />


### 4. Create Users & Groups
- Created OU: `Employees`
- Created Group: `HR`
- Added users: `Alice HR`, `Bob HR`

<img width="752" height="525" alt="Screen Shot 2025-09-11 at 11 18 32 AM" src="https://github.com/user-attachments/assets/5447f1af-1c50-4490-8a92-0aaff4411e13" />

---

### 5. Join Client-1 to the Domain
- Changed domain → `mycompany.local`

<img width="868" height="598" alt="Screen Shot 2025-09-10 at 6 28 22 PM" src="https://github.com/user-attachments/assets/0bf56e80-ef44-47b7-b680-1d0ac2774c74" />


---

### 6. Apply Group Policy Objects (GPOs)
- Enforced **password complexity**
- Set desktop wallpaper via GPO
<img width="802" height="593" alt="Screen Shot 2025-09-10 at 6 36 38 PM" src="https://github.com/user-attachments/assets/f7225ebf-d133-4778-9aa0-9a822a151116" />
<img width="801" height="353" alt="Screen Shot 2025-09-10 at 6 39 25 PM" src="https://github.com/user-attachments/assets/397c4ddb-e9be-4210-acf9-326425c3910d" />
<img width="778" height="561" alt="Screen Shot 2025-09-10 at 6 40 23 PM" src="https://github.com/user-attachments/assets/d05fe099-37cd-4c70-a721-f45e3d5dcc95" />
<img width="1124" height="547" alt="Screen Shot 2025-09-11 at 11 48 41 AM" src="https://github.com/user-attachments/assets/2f0fd8ca-afc4-4bac-9747-46d7b0c1d34c" />

<img width="672" height="774" alt="Screen Shot 2025-09-10 at 6 57 04 PM" src="https://github.com/user-attachments/assets/1b4561ef-bb64-41e4-ab18-763853313822" />
<img width="800" height="590" alt="Screen Shot 2025-09-10 at 8 50 47 PM" src="https://github.com/user-attachments/assets/3343331c-8600-4f5c-bfbb-3979038852dc" />
<img width="691" height="644" alt="Screen Shot 2025-09-10 at 8 50 11 PM" src="https://github.com/user-attachments/assets/026c1c14-9e3c-46d4-b033-aca355ed7913" />


<img width="1440" height="900" alt="Screen Shot 2025-09-10 at 8 48 17 PM" src="https://github.com/user-attachments/assets/0ede3e12-43f5-43ab-8ffa-a3969aacc6b2" />

### 7. File Share with Permissions
- Created `\\DC-1\FinanceShare`
- `HR` group → Read/Write
- Non-HR users → Denied
<img width="626" height="347" alt="Screen Shot 2025-09-10 at 8 53 38 PM" src="https://github.com/user-attachments/assets/64879419-55e4-4edd-92d2-348443f8cd25" />
<img width="518" height="570" alt="Screen Shot 2025-09-10 at 9 22 46 PM" src="https://github.com/user-attachments/assets/c9b279c5-e0bd-4644-93f7-6b182b9374c2" />
<img width="518" height="570" alt="Screen Shot 2025-09-10 at 9 22 46 PM" src="https://github.com/user-attachments/assets/4e551b8b-5719-44ed-a285-81b75c8634d8" />


---

## 🔹 Troubleshooting
- **Issue**: Client-1 couldn’t join domain → fixed DNS config.  
- **Issue**: GPO not applying → used `gpupdate /force` and checked OU.  

---

## 🔹 Skills Demonstrated
- Azure virtual networking  
- Windows Server administration  
- Active Directory Domain Services  
- DNS management  
- Group Policy Objects (GPOs)  
- NTFS & Share permissions  
- PowerShell automation  
- Troubleshooting  

---

## 🔹 Next Steps / Enhancements
- Add redundancy with a second domain controller.  
- Configure Remote Desktop Gateway for secure external access.  
- Monitor domain controller uptime with Azure Monitor.  
