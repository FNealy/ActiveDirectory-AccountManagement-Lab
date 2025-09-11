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

📸 Screenshot: ![Create Users](./screenshots/users_groups/01_create_users.png)

---

### 2. Simulate Password Reset
- Select a user → **Reset Password**  
- Check: **User must change password at next logon**  
- Document password complexity requirements  

📸 Screenshot: ![Reset Password](./screenshots/password_resets/01_reset_password.png)

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

