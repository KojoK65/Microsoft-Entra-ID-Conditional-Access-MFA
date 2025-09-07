# 💼 Microsoft Entra ID: Conditional Access & MFA

## 🎯 Project Objective  
This project demonstrates how to design, configure, and test Conditional Access (CA) policies in Microsoft Entra ID. The goal was to enforce modern identity protections using MFA for privileged users and block legacy authentication methods—without interrupting operations, using report-only mode.

---

## 🛠️ What I Did

### 1. Disabled Security Defaults  
- Opened the **Microsoft Entra Admin Center**  
- Navigated to **Properties > Manage Security defaults**  
- Disabled Security Defaults to allow custom Conditional Access policy configuration

**⚙️ Security Defaults turned off in Entra ID**
<br>
<img width="70%" src="https://github.com/user-attachments/assets/b269b4b5-f35b-4035-8a9e-16a7ac91bef7" />

---

### 2. Created CA Policy to Require MFA for Admin Roles  
- Created a Conditional Access policy named `CA - Require MFA for Admins`  
- Targeted high-privilege roles: **Global Administrator**, **Security Administrator**, etc.  
- Excluded the **break-glass** admin account to prevent lockout  
- Applied to **All cloud apps**  
- Grant control was set to **Require multi-factor authentication**  
- Policy mode: **Report-only** for safe validation

**🔐 Conditional Access policy requiring MFA for admin roles**
<br>
<img width="70%" src="https://github.com/user-attachments/assets/6de557b3-d2a5-4f2a-9cd9-51ea435c5b2b" />

---

### 3. Created CA Policy to Block Legacy Authentication  
- Created a Conditional Access policy named `CA - Block Legacy Auth`  
- Targeted **All users**, excluding the break-glass account  
- Applied to **All cloud apps**  
- Configured client apps condition to include **Legacy authentication clients**  
- Grant control was set to **Block access**  
- Policy mode: **Report-only**

**🚫 Conditional Access policy blocking legacy authentication protocols**
<br>
<img width="70%" src="https://github.com/user-attachments/assets/d0cfecf0-ffb6-43b5-b04e-9fbf6c7953a3" />

---

## ✅ Outcome

- Successfully created and tested two Conditional Access policies:
  - ✅ **MFA enforcement** for high-privilege roles  
  - 🚫 **Blocking of legacy authentication protocols**  
- Both policies were applied in **Report-only mode** to monitor impact without enforcing changes  
- Confirmed readiness for real-world implementation with no disruptions

---

## 📈 Skills Demonstrated  
- 🔐 **Conditional Access policy design** in Microsoft Entra ID  
- 🧪 **Non-disruptive policy testing** using report-only mode  
- 🛑 **Blocking insecure authentication protocols**  
- 👥 **Protecting privileged accounts** with enforced MFA

---
