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

# AWS VPC Full Architecture (Interview + Real World)

## 🔥 Final Architecture (Production Level)

```
User 
 ↓
Internet 
 ↓
Internet Gateway (IGW)
 ↓
Application Load Balancer (Public Subnet - Multi AZ)
 ↓
Auto Scaling Group (EC2 - Private Subnet - Multi AZ)
 ↓
Database (RDS / MongoDB - Private Subnet)
```

---

## 🧩 Complete Breakdown (Layer by Layer)

### 1. 🌐 Entry Layer (Public Facing)

* **Internet Gateway (IGW)**

  * VPC ko internet se connect karta hai

* **Application Load Balancer (ALB)**

  * Public subnet me hota hai
  * Traffic ko multiple EC2 me distribute karta hai
  * Health check karta hai

---

### 2. ⚙️ Application Layer

* **EC2 Instances (Backend / App)**

  * Private subnet me deploy
  * Direct internet access ❌
  * Only ALB se traffic receive

* **Auto Scaling Group (ASG)**

  * Load ke hisaab se EC2 add/remove
  * High availability

---

### 3. 🗄️ Data Layer

* **Database (RDS / MongoDB)**

  * Private subnet me
  * Internet se direct access ❌
  * Only EC2 se connect

---

### 4. 🔁 Outbound Internet (Important)

* **NAT Gateway (Public Subnet)**

  * Private EC2 ko internet use karne deta hai
  * Example:

    * npm install
    * API calls

---

### 5. 🔐 Security Layer

* **Security Groups**

  * ALB → allow HTTP/HTTPS
  * EC2 → allow only ALB
  * DB → allow only EC2

* **NACL**

  * Subnet level control (extra security)

---

### 6. 🧭 Networking Layer

* **Route Tables**

  * Public subnet:

    ```
    0.0.0.0/0 → IGW
    ```
  * Private subnet:

    ```
    0.0.0.0/0 → NAT Gateway
    ```

---

## 🏗️ Visual Architecture

![Image](https://miro.medium.com/0%2AV5riEqJqLT3LnU2b.png)

![Image](https://docs.aws.amazon.com/images/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/images/centralized-egress-gwlb-and-ec2.png)

![Image](https://miro.medium.com/1%2Apr1-wCKu61aTK0ubsDzuIg.png)

![Image](https://miro.medium.com/v2/1%2Aw061vfa1Ew-PIcbY89uM7w.png)

---

## ⚡ Key Design Decisions (Interview Gold)

### ✔️ Multi AZ Deployment

* 2+ Availability Zones
* Fault tolerance

---

### ✔️ Public vs Private Separation

* ALB → Public
* EC2 → Private
* DB → Private

---

### ✔️ Stateless App Servers

* EC2 me data store mat karo
* DB / S3 use karo

---

### ✔️ Health Checks

* ALB unhealthy instance hata deta hai

---

## 🚨 Brutal Mistakes (Reject Level)

* ❌ EC2 public subnet me without reason
* ❌ Database public subnet me
* ❌ No Load Balancer
* ❌ No Auto Scaling
* ❌ Single AZ

---

## 🧠 One-Line Memory Trick

**"IGW → ALB → EC2 (ASG) → DB + NAT for outbound"**

---

## ⚡ Short Pitch (Interview me bolne ke liye)

“Main ek VPC design karta hoon jisme ALB public subnet me hota hai, EC2 instances private subnet me ASG ke under run karte hain, database isolated private subnet me hota hai, aur NAT Gateway private instances ko outbound internet access deta hai. Ye setup highly available, scalable aur secure hota hai.”

---

