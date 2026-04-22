# 🌐 Route 53 Integration — Notes App (Cloud Deployment)

---

# 📌 Overview

This section describes how a custom domain was integrated with the deployed Notes App using AWS Route 53.

The application, hosted on an EC2 instance, is now accessible via a domain instead of a public IP, improving usability and production readiness.

---

# ☁️ Deployment Architecture

```
User → Custom Domain (myapp.com)
      → Route 53 (DNS Resolution)
      → EC2 Instance (Ubuntu Server)
      → Node.js Backend (Express)
      → React Frontend (Static Served)
```

---

# ⚙️ Implementation Workflow

## 1. Domain Setup

- A custom domain was purchased using a domain registrar (GoDaddy / Namecheap)

Example:
```
myapp.com
```

---

## 2. Route 53 Hosted Zone

- Created a Public Hosted Zone in AWS Route 53

```
Type: Public Hosted Zone
Domain: myapp.com
```

---

## 3. Nameserver Mapping

- Route 53 generated nameservers
- These nameservers were updated in the domain registrar panel

```
ns-xxxx.awsdns-xx.com
ns-xxxx.awsdns-xx.net
ns-xxxx.awsdns-xx.org
ns-xxxx.awsdns-xx.co.uk
```

---

## 4. DNS Record Configuration

### Root Domain Mapping

```
Type: A
Name: @
Value: EC2 Public IP
```

### WWW Mapping

```
Type: A
Name: www
Value: EC2 Public IP
```

---

## 5. Reverse Proxy Setup (Nginx)

Install Nginx:

```bash
sudo apt install nginx -y
```

Configure Nginx:

```bash
sudo nano /etc/nginx/sites-available/default
```

Paste:

```nginx
server {
    listen 80;
    server_name myapp.com www.myapp.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
    }
}
```

Restart Nginx:

```bash
sudo systemctl restart nginx
```

---

## 6. HTTPS (SSL Setup)

Install Certbot:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Enable HTTPS:

```bash
sudo certbot --nginx
```

---

# 🌍 Final Access

```
http://myapp.com
https://myapp.com
```

---

# 🚧 Challenges Faced

- DNS propagation delay
- Incorrect nameserver configuration
- Port exposure issues on EC2
- HTTP vs HTTPS confusion

---

# ✅ Key Learnings

- Route 53 handles DNS resolution, not hosting
- Nameserver configuration is critical
- Nginx enables clean routing (no port usage)
- HTTPS requires SSL configuration

---

# 📈 Result

- Domain successfully mapped to EC2 instance
- Application accessible via custom domain
- HTTPS enabled for secure access
- Production-ready deployment achieved

---

# 🔥 Status

```
Domain: Connected
DNS: Route 53
Server: EC2 (Ubuntu)
Protocol: HTTPS Enabled
```

---

# DONE ✅
