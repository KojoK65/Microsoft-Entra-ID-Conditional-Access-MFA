# 💼 Microsoft Entra ID: Conditional Access & MFA

> **🎯 Objective:** Apply and test high-value Conditional Access (CA) policies in Microsoft Entra ID to enforce MFA for admin roles and block legacy authentication.

---

## ✅ Lab Summary

This lab demonstrates how to configure and validate key Conditional Access policies in Microsoft Entra ID (formerly Azure AD):

- Require **MFA for high-privilege admin roles** (e.g., Security Admin)
- **Block legacy authentication protocols** to improve security posture
- Run both policies in **Report-only mode** for safe testing

---

## 🛠️ Prerequisites

- Microsoft Entra ID P2 license
- Access to Entra Admin Center
- One user assigned a privileged admin role (e.g., Security Admin)
- Break-glass Global Admin account excluded from CA policies
- 500 test users split across 5 departments
- Security Defaults disabled

---

## 🔧 Step-by-Step Implementation

### 🔒 Step 0 — Disable Security Defaults

> If enabled, disable Security Defaults to allow for custom Conditional Access configuration.

- Action:  
  Set to **Disable** and click **Save**

*Security defaults disabled in Entra ID properties*
<img width="1920" height="965" alt="Screenshot (36)" src="https://github.com/user-attachments/assets/b269b4b5-f35b-4035-8a9e-16a7ac91bef7" />

---

### 🔐 Step 1 — Create CA Policy: Require MFA for Admin Roles

> Require multifactor authentication for privileged users using directory roles

- Configuration:
  - **Name:** `CA - Require MFA for Admins`
  - **Users:**  
    - Include: Directory Roles → Select `Global Administrator`, `Security Administrator`, etc.  
    - Exclude: `breakglass@yourtenant.onmicrosoft.com`
  - **Cloud apps:** All cloud apps
  - **Grant controls:** Require multifactor authentication
  - **Enable policy:** Report-only

📸 *Policy showing MFA for Admins configuration*
<img width="1920" height="964" alt="Screenshot (38)" src="https://github.com/user-attachments/assets/6de557b3-d2a5-4f2a-9cd9-51ea435c5b2b" />

---

### 🚫 Step 2 — Create CA Policy: Block Legacy Authentication

> Block older authentication protocols that bypass modern security controls like MFA

- Configuration:
  - **Name:** `CA - Block Legacy Auth`
  - **Users:**  
    - Include: All users  
    - Exclude: `breakglass@yourtenant.onmicrosoft.com`
  - **Cloud apps:** All
  - **Conditions → Client apps:**  
    - Configure = Yes  
    - Check **Legacy authentication clients**
  - **Grant controls:** Block access
  - **Enable policy:** Report-only

*Policy summary page showing legacy auth block configuration*
<img width="1920" height="960" alt="Screenshot (44)" src="https://github.com/user-attachments/assets/d0cfecf0-ffb6-43b5-b04e-9fbf6c7953a3" />

---

## ✅ Outcome

- Successfully configured two high-value Conditional Access policies in Microsoft Entra ID
- All policies run in **Report-only mode** to allow safe evaluation
- Admin role (e.g., Security Admin) scoped for MFA enforcement
- Legacy authentication protocols scoped for future blocking
- Ready for real-world rollout and testing
