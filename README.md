# 💼 Microsoft Entra ID: Conditional Access & MFA

> **🎯 Objective:** Apply and test high-value Conditional Access (CA) policies in Microsoft Entra ID to enforce MFA for admin roles and block legacy authentication.

---

## ✅ Lab Summary

This lab demonstrates how to configure and validate key Conditional Access policies in Microsoft Entra ID (formerly Azure AD):

- Require **MFA for high-privilege admin roles** (e.g., Security Admin)
- **Block legacy authentication protocols** to improve security posture
- Run both policies in **Report-only mode** for safe testing
- Confirm configuration via **portal and sign-in logs**

---

## 🛠️ Prerequisites

- Microsoft Entra ID P2 license (or E3/E5)
- Access to Entra Admin Center
- One user assigned a privileged admin role (e.g., Security Admin)
- Break-glass Global Admin account excluded from CA policies
- 500 test users split across 5 departments
- Security Defaults disabled

---

## 🔧 Step-by-Step Implementation

### 🔒 Step 0 — Disable Security Defaults

> If enabled, disable Security Defaults to allow for custom Conditional Access configuration.

- Path:  
  `Entra Admin Center → Entra ID → Properties → Manage security defaults`

- Action:  
  Set to **Disable** and click **Save**

📸 *Screenshot: Security defaults disabled in Entra ID properties*

---

### 🔐 Step 1 — Create CA Policy: Require MFA for Admin Roles

> Require multifactor authentication for privileged users using directory roles

- Path:  
  `Entra Admin Center → Security → Conditional Access → Policies → + New policy`

- Configuration:
  - **Name:** `CA - Require MFA for Admins`
  - **Users:**  
    - Include: Directory Roles → Select `Global Administrator`, `Security Administrator`, etc.  
    - Exclude: `breakglass@yourtenant.onmicrosoft.com`
  - **Cloud apps:** All cloud apps
  - **Grant controls:** Require multifactor authentication
  - **Enable policy:** Report-only

📸 *Screenshot: Policy summary page showing MFA for Admins configuration*

---

### 🚫 Step 2 — Create CA Policy: Block Legacy Authentication

> Block older authentication protocols that bypass modern security controls like MFA

- Path:  
  `Entra Admin Center → Security → Conditional Access → Policies → + New policy`

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

📸 *Screenshot: Policy summary page showing legacy auth block configuration*

---

## 📸 Deliverables (for documentation)

| Screenshot | Description |
|------------|-------------|
| Security Defaults | Security defaults set to disabled |
| Policy: Require MFA for Admins | Policy configuration summary |
| Policy: Block Legacy Auth | Policy configuration summary |

---

## ✅ Outcome

- Successfully configured two high-value Conditional Access policies in Microsoft Entra ID
- All policies run in **Report-only mode** to allow safe evaluation
- Admin role (e.g., Security Admin) scoped for MFA enforcement
- Legacy authentication protocols scoped for future blocking
- Ready for real-world rollout and testing
