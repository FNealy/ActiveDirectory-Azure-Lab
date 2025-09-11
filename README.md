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

<img width="1160" height="280" alt="Screen Shot 2025-09-10 at 5 16 00 PM" src="https://github.com/user-attachments/assets/bcb5fb87-cfd1-412a-b9af-3f14cafb9237" />


---

### 2. Install Active Directory Domain Services
- Added the **AD DS** role in Server Manager.
- Promoted `DC-1` to a domain controller → `mycompany.local`.

 <img width="1440" height="900" alt="Screen Shot 2025-09-10 at 5 25 29 PM" src="https://github.com/user-attachments/assets/881d52a3-d914-4deb-83a9-3dd8dd6d6140" />
<img width="1440" height="900" alt="Screen Shot 2025-09-10 at 5 27 21 PM" src="https://github.com/user-attachments/assets/1fef4436-d13f-4ba4-a44b-52bfdb10c30d" />
<img width="509" height="405" alt="Screen Shot 2025-09-10 at 5 28 02 PM" src="https://github.com/user-attachments/assets/48ac02fb-0b50-411f-aa3d-4eec1c74f505" />


---

### 3. Configure DNS
- Configured `DC-1` as DNS server.
- Set Client-1 DNS → DC-1 private IP.
<img width="1440" height="900" alt="Screen Shot 2025-09-10 at 5 34 29 PM" src="https://github.com/user-attachments/assets/32a4c490-5d81-49fc-bf55-ca95bc3f4ca2" />
<img width="845" height="646" alt="Screen Shot 2025-09-10 at 5 42 23 PM" src="https://github.com/user-attachments/assets/cebc0c85-204f-41eb-8654-3a62c3674504" />

---

### 4. Create Users & Groups
- Created OU: `Employees`
- Created Group: `HR`
- Added users: `Alice HR`, `Bob HR`

<img width="670" height="459" alt="Screen Shot 2025-09-10 at 6 33 15 PM" src="https://github.com/user-attachments/assets/a6150a19-70db-4ce7-9a6f-a8dc28e0d1b3" />
<img width="631" height="318" alt="Screen Shot 2025-09-10 at 6 33 20 PM" src="https://github.com/user-attachments/assets/232f7968-2f8b-4d4d-93e2-e103336a9bcf" />

---

### 5. Join Client-1 to the Domain
- Changed domain → `mycompany.local`

<img width="868" height="598" alt="Screen Shot 2025-09-10 at 6 28 22 PM" src="https://github.com/user-attachments/assets/8e53dc35-e0bb-4666-bbb9-18540d931f29" />


---

### 6. Apply Group Policy Objects (GPOs)
- Enforced **password complexity**
- Set desktop wallpaper via GPO

 <img width="802" height="593" alt="Screen Shot 2025-09-10 at 6 36 38 PM" src="https://github.com/user-attachments/assets/468f229d-74f7-4799-8a4c-cbd8b65a23ec" />
<img width="778" height="561" alt="Screen Shot 2025-09-10 at 6 40 23 PM" src="https://github.com/user-attachments/assets/9a27e568-7442-400d-83b0-634cae6ec833" />

---

### 7. File Share with Permissions
- Created `\\DC-1\FinanceShare`
- `HR` group → Read/Write
- Non-HR users → Denied

 <img width="626" height="347" alt="Screen Shot 2025-09-10 at 8 53 38 PM" src="https://github.com/user-attachments/assets/c32d49b7-7bd1-4c31-89be-d2f67ace970f" />
<img width="518" height="570" alt="Screen Shot 2025-09-10 at 9 22 46 PM" src="https://github.com/user-attachments/assets/7a55cc80-78e3-4edc-b552-b95250e840b8" />
<img width="540" height="591" alt="Screen Shot 2025-09-10 at 9 23 04 PM" src="https://github.com/user-attachments/assets/659e3395-1a12-47f7-b58b-dc8afe7f1881" />


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
