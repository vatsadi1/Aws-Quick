# 📅 Day 4 – AWS VPC (Quick Revision Notes)

## 🔥 Core Idea

**VPC = Virtual Private Network inside AWS**
→ Tumhara isolated cloud network jahan tum infra control karte ho.

---

## 🧩 1. CIDR Block (IP Range)

* Defines network size
* Example:

  ```
  10.0.0.0/16
  ```
* ⚠️ Small CIDR = scaling problem later

---

## 🧩 2. Subnets

* VPC ke partitions

### Types:

* **Public Subnet**

  * Internet access
* **Private Subnet**

  * No direct internet

---

## 🧩 3. Internet Gateway (IGW)

* VPC → Internet connection
* Required for public subnet

---

## 🧩 4. Route Table

* Traffic rules define karta hai

Example:

```
0.0.0.0/0 → IGW
```

---

## 🧩 5. NAT Gateway

* Private subnet → Internet access (indirect)

### Use:

* npm install
* API calls
* Updates

⚠️ Without NAT → private EC2 useless for outbound internet

---

## 🧩 6. Security Groups (SG)

* Instance-level firewall
* Only **ALLOW rules**

### Example:

* Allow HTTP (80)
* Allow SSH (22 restricted)

---

## 🧩 7. Network ACL (NACL)

* Subnet-level firewall
* **ALLOW + DENY**

### Difference:

* SG → smart + stateful
* NACL → raw + stateless

---

## 🧩 8. Elastic IP

* Static public IP
* Restart ke baad change nahi hota

---

## 🧩 9. Load Balancer

* Traffic distribute karta hai
* High availability provide karta hai

Types:

* ALB → HTTP/HTTPS
* NLB → TCP (fast)

---

## 🧩 10. Target Group

* Load balancer ko batata hai:

  * kaunse EC2 use karne
  * kaun healthy hai

---

## 🧩 11. Auto Scaling Group (ASG)

* Traffic ke hisaab se EC2 add/remove

⚠️ Without ASG → high traffic = crash

---

## 🧩 12. VPC Peering

* 2 VPCs connect (private communication)

---

## 🧩 13. VPC Endpoints

* AWS services access without internet
* Example: S3 private access

---

## 🧠 Request Flow (Important)

```
User → Internet → IGW → Load Balancer → EC2 → Database
```

---

## 🏗️ Standard Production Setup

* VPC (10.0.0.0/16)
* 2 Public Subnets (multi AZ)
* 2 Private Subnets
* IGW
* NAT Gateway
* Route Tables
* Load Balancer
* EC2 (ASG)
* DB (Private)

---

## 🚨 Common Mistakes

* ❌ DB in public subnet
* ❌ No Load Balancer
* ❌ No NAT but private EC2
* ❌ Single AZ deployment

---

## ⚡ Interview One-Liners

* VPC = isolated network in cloud
* Subnet = network partition
* IGW = internet entry
* NAT = private → internet
* SG = instance firewall
* NACL = subnet firewall
* ALB = traffic distribution
* ASG = auto scaling

---

## 🧠 Reality Check

* Only VPC + EC2 → beginner
* Full architecture (ALB + NAT + ASG + Private DB) → production-ready

---
