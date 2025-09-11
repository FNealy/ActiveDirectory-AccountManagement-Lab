
# 🖥️ Lab 2: User Account Management – Password Resets & Account Lockouts

## 🔹 Overview
This lab demonstrates common **help desk tasks in Active Directory**: resetting passwords, unlocking accounts, and troubleshooting account lockouts.  
The goal is to simulate realistic end-user issues and show proper administrative responses.

---

## 🔹 Architecture
- **Azure Virtual Network (VNet)**: `10.0.0.0/24`  
- **Virtual Machines**:
  - `DC-1` → Domain Controller + DNS  
  - `Client-1` → Domain-joined workstation  

📊 **Diagram (reuse AD Lab diagram)**:  
![AD Lab Diagram](./diagrams/ad_lab_diagram.png)

---

## 🔹 Features Implemented
✅ User account creation (test users: Charlie, Dave)  
✅ Password reset via ADUC  
✅ Forced password change at next logon  
✅ Account lockout simulation and troubleshooting  
✅ Event Viewer
