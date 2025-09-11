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

---

### 3. Simulate Account Lockout
- Attempt wrong password multiple times on `Client-1`  
- User account becomes **locked out**  
- On DC-1 → **Event Viewer → Security logs** → locate **lockout source**  

📸 Screenshot: ![Event Viewer Lockout](./screenshots/password_resets/02_event_viewer.png)

---

### 4. Unlock Account
- In ADUC → right-click locked user → **Unlock Account**  
- Document troubleshooting steps and verify login works  

📸 Screenshot: ![Unlock Account](./screenshots/password_resets/03_unlock_account.png)

---

### 5. Test End-User Login
- Log in as the user after password reset  
- Confirm forced password change worked  
- Ensure password complies with **Group Policy complexity**  

📸 Screenshot: ![User Login](./screenshots/password_resets/04_user_login.png)

---

## 🔹 Troubleshooting
- **Issue:** User still cannot log in after reset  
  - **Fix:** Verify DNS points to DC-1 private IP  
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

