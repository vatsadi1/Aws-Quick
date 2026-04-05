# 📅 Day 2 – IAM (Authentication & Authorization in AWS)

## 🔥 Core Idea

**IAM = Identity + Access Control system in AWS**
→ Kaun login karega (Authentication)
→ Kya access milega (Authorization)

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

# 📅 Day 3 – EC2 (Elastic Compute Cloud)

## 🔥 Core Idea

**EC2 = Virtual Server in AWS**
→ Tum apna server bana sakte ho cloud me

---

## 🧩 1. What is EC2

* Full form: **Elastic Compute Cloud**
* On-demand virtual machines

👉 Tum CPU, RAM, storage choose kar sakte ho

---

## 🧩 2. Virtualization (Important)

* Physical server → multiple virtual servers

👉 Using **Hypervisor**

### Flow:

```id="virtflow"
Physical Server → Hypervisor → Multiple EC2 Instances
```

---

## 🧩 3. Why EC2

* No physical hardware
* Scalable (increase/decrease)
* Pay as you use

---

## 🧩 4. Scaling Concept

* **Scale Up** → Increase power (CPU/RAM)
* **Scale Down** → Reduce resources

👉 Isi wajah se “Elastic”

---

## 🧩 5. Regions & Availability Zones

* AWS ke multiple regions (India, USA, Europe)
* Har region me multiple AZ

👉 Near region = low latency

---

## 🧩 6. Instance Types

### 1. General Purpose

* Balanced use

### 2. Compute Optimized

* High CPU tasks

### 3. Storage Optimized

* High storage

### 4. Accelerated Computing

* GPU / ML tasks

---

## 🧩 7. Key Pair (Login System)

* Secure login without password

### Components:

* **Private Key (.pem)** → tumhare paas
* **Public Key** → EC2 me store

👉 SSH connection ke liye use hota hai

---

## 🧩 8. Cost Model

* Pay-as-you-go
  👉 Use karo → pay karo
  👉 Idle → no cost (except storage)

---

## 🧩 9. Tools

* PuTTY / Terminal
  👉 EC2 connect karne ke liye

---

## 🔁 Request Flow

```id="ec2flow"
User → Request EC2 → AWS → Virtual Machine Ready
```

---

## 🚨 Common Mistakes

* ❌ Private key lose kar dena
* ❌ Wrong instance type choose karna
* ❌ Region galat select karna

---

## 🧠 Interview One-Liners

* EC2 = virtual server
* Hypervisor = virtualization layer
* Key pair = secure login
* Instance type = performance category
* Region = location
* AZ = data center

---
