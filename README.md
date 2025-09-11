<p align="center">
  <img src="https://i.imgur.com/2rlRGkK.png" alt="File Share & NTFS Permissions Logo" width="200"/>
</p>



# User Account Management – Password Resets & Account Lockouts

## 🔹 Overview
This lab demonstrates common **help desk tasks in Active Directory**: resetting passwords, unlocking accounts, and troubleshooting account lockouts.  
The goal is to simulate realistic end-user issues and show proper administrative responses.

---

## 🔹 Architecture
- **Azure Virtual Network (VNet)**: `10.0.0.0/24`  
- **Virtual Machines**:
  - `DC-1` → Domain Controller + DNS  
  - `Client-1` → Domain-joined workstation  


---

## 🔹 Features Implemented
✅ User account creation (test users: Charlie, Dave)  
✅ Password reset via ADUC  
✅ Forced password change at next logon  
✅ Account lockout simulation and troubleshooting  
✅ Event Viewer auditing for lockout source  

---

## 🔹 Implementation Steps

### 1. Create Test Users
- On DC-1 → **Active Directory Users and Computers (ADUC)**  
- OU: `Employees`  
- Create users: `Charlie`, `Dave`  
<img width="592" height="357" alt="Screen Shot 2025-09-11 at 12 38 02 PM" src="https://github.com/user-attachments/assets/a4818e1c-f274-4197-95dd-78d49575e8bb" />


---

### 2. Simulate Password Reset
- Select a user → **Reset Password**  
- Check: **User must change password at next logon**  
- Document password complexity requirements  
<img width="450" height="317" alt="Screen Shot 2025-09-11 at 12 48 27 PM" src="https://github.com/user-attachments/assets/9528defd-635d-4a66-b5d0-268ab7eedbfc" />
<img width="747" height="461" alt="Screen Shot 2025-09-11 at 12 49 12 PM" src="https://github.com/user-attachments/assets/ec9d3b9f-1cf4-45cd-aa97-aadf31f266d4" />
<img width="433" height="236" alt="Screen Shot 2025-09-11 at 12 50 08 PM" src="https://github.com/user-attachments/assets/f72aa545-f67a-4154-ab53-c3d4aaf9ca16" />
<img width="784" height="423" alt="Screen Shot 2025-09-11 at 12 59 06 PM" src="https://github.com/user-attachments/assets/aca73239-b26d-4119-abcb-74dae7ac9af8" />
<img width="781" height="307" alt="Screen Shot 2025-09-11 at 1 06 23 PM" src="https://github.com/user-attachments/assets/344ec018-a515-4b0c-8fa9-ad92ca881f84" />

---

### 3. Simulate Account Lockout
- Attempt wrong password multiple times on `Client-1`  
- User account becomes **locked out**  
- On DC-1 → **Event Viewer → Security logs** → locate **lockout source**  
<img width="807" height="524" alt="Screen Shot 2025-09-11 at 1 17 34 PM" src="https://github.com/user-attachments/assets/7285a055-7413-4a74-8bde-1a6d8fa81ad8" />
<img width="734" height="312" alt="Screen Shot 2025-09-11 at 1 28 28 PM" src="https://github.com/user-attachments/assets/40c29431-e216-4118-996e-050a4464e161" />



### 4. Unlock Account
- In ADUC → right-click locked user → **Unlock Account**  
- Document troubleshooting steps and verify login works  
<img width="388" height="448" alt="Screen Shot 2025-09-11 at 1 30 28 PM" src="https://github.com/user-attachments/assets/87513a22-ee0b-4b70-9d97-3ed4b2027334" />


### 5. Test End-User Login
- Log in as the user after password reset  
- Confirm forced password change worked  
- Ensure password complies with **Group Policy complexity**  

<img width="1440" height="900" alt="Screen Shot 2025-09-11 at 1 32 05 PM" src="https://github.com/user-attachments/assets/b0da226f-b8ca-4ca3-93b6-796ee5dd95f9" />


---

## 🔹 Troubleshooting
- **Issue:** User still cannot log in after reset  
  - **Fix:** Verify DNS points to DC-1 private IP  
    <img width="514" height="285" alt="Screen Shot 2025-09-11 at 1 36 18 PM" src="https://github.com/user-attachments/assets/a94bb57e-1ff9-4163-b1ae-9595060b0e85" />
<img width="961" height="154" alt="Screen Shot 2025-09-11 at 1 36 42 PM" src="https://github.com/user-attachments/assets/bd7f393f-0100-4d65-9744-9058a5168a2d" />

  - Ensure user is not entering old cached credentials  
- **Issue:** Password does not meet complexity  
  - **Fix:** Check Group Policy → Password Policy  

---

## 🔹 Skills Demonstrated
- AD user account management  
- Password resets & account unlocks  
- Event Viewer auditing  
- Security compliance enforcement  
- Real-world help desk troubleshooting  

---

## 🔹 Next Steps / Enhancements
- Document **frequent lockout patterns** to automate alerts  
- Implement **self-service password reset portal**  
- Track **user training metrics** to reduce help desk tickets  

