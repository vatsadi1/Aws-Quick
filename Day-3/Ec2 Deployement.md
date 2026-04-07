# 🚀 EC2 MERN Deployment — Flow Cheat Sheet

---

# 🧠 CORE IDEA (REMEMBER THIS ONLY)

```text
SERVER → CODE → INSTALL → RUN → EXPOSE
```

---

# ⚡ STEP-BY-STEP FLOW

## 1. CONNECT (Access server)

```bash
ssh -i key.pem ubuntu@YOUR-IP
```

**Meaning:**

* Connect your local machine to EC2 server

---

## 2. SETUP SERVER (Prepare environment)

```bash
sudo apt update
sudo apt install -y nodejs npm git
```

**Meaning:**

* Install required tools (Node + Git)

---

## 3. GET YOUR CODE

```bash
git clone YOUR_REPO_URL
cd YOUR_PROJECT
```

**Meaning:**

* Download your project from GitHub

---

## 4. INSTALL DEPENDENCIES

```bash
npm install
```

**Meaning:**

* Install all packages your app needs

---

## 5. RUN YOUR SERVER

```bash
node server.js
```

**Meaning:**

* Start backend (Express server)

---

## 6. OPEN PORT (VERY IMPORTANT)

In AWS Security Group:

```
Port: 3000
Source: 0.0.0.0/0
```

**Meaning:**

* Allow internet to access your app

---

## 7. ACCESS YOUR APP

```text
http://YOUR-IP:3000
```

---

# 🔁 OPTIONAL (PRODUCTION FLOW)

## Use PM2 (keep app alive)

```bash
npm install -g pm2
pm2 start server.js
pm2 save
pm2 startup
```

---

## Use Nginx (clean URL)

* Removes port
* Adds security layer

---

# ❌ COMMON FAILURES

| Problem               | Cause                   |
| --------------------- | ----------------------- |
| Permission denied     | Wrong key / username    |
| Cannot reach          | Port not open           |
| Blank page            | Static files not served |
| localhost not working | Using wrong URL         |

---

# 🧠 FINAL SUMMARY

```text
1. SSH into server
2. Install tools
3. Clone project
4. Install dependencies
5. Run server
6. Open port
7. Access via IP
```

---

# DONE ✅
