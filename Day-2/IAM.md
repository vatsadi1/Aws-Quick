# 📅 Day 2 – IAM (Authentication & Authorization in AWS)

## 🔥 Core Idea

**IAM = Identity + Access Control system in AWS**
→ Kaun login karega (Authentication)
→ Kya access milega usko (Authorization)

---

## 🧩 1. Users

* Individual identity in AWS
* Example: Developer, Admin

👉 Login karne ke liye use hota hai
👉 Credentials:

* Email / Username
* Password

---

## 🧩 2. Policies

* Define karta hai **kya allowed hai kya nahi**

### Example:

* EC2 read only
* S3 full access
* DB access restricted

👉 JSON format me likhte hain

---

## 🧩 3. Groups

* Multiple users ka collection

### Example:

* Dev Team
* QA Team
* DB Admin

👉 Ek hi policy multiple users pe apply kar sakte ho

---

## 🧩 4. Roles

* Temporary access (no username/password)

### Use case:

* EC2 → S3 access
* Cross account access

👉 Secure way hai services ko connect karne ka

---

## 🔁 Flow (Simple)

```id="d2flow"
User → Login → IAM checks Policy → Access Grant / Deny
```

---

## ⚡ Real Example

* Dev group → EC2 access
* QA group → Read-only access
* DB Admin → Full DB control

---

## 🚨 Common Mistakes

* ❌ Direct full access (Admin) sabko dena
* ❌ Policies bina structure ke likhna
* ❌ Roles use na karna (security risk)

---

## 🧠 Interview One-Liners

* IAM = authentication + authorization
* Policy = permission rules
* Group = multiple users management
* Role = temporary secure access

---

---
