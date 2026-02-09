#  ☁️  Manual Cloud Deployment & Infrastructure Fundamentals**

> The application itself is intentionally simple — the primary goal was to learn **deployment, networking, and server fundamentals**.

🔗 **Live Website (Custom Domain):** https://learningtodeploy.nishan.works/  
📦 **GitHub Repository:** (this repo documents the original AWS setup)

---

## 🧠 Why This Project Exists

This project was created to:
- Learn how websites are hosted on real servers
- Understand DNS, reverse proxies, SSL, and CDNs
- See how traffic flows from a user’s browser to a backend server
- Gain confidence working with Linux and server configuration

---

## 🌐 Architecture Overview

This project involved **three separate systems working together**:

1. **AWS EC2** – for learning server setup and Nginx
2. **BunnyCDN** – for serving static images via CDN
3. **Custom Domain** – for real-world DNS routing

### 🧩 Traffic Flow Diagram

User Browser ---> Custom Domain (DNS) ---> Nginx (Reverse Proxy + SSL) ---> Web Application (AWS EC2)

Static Images:
User → BunnyCDN → Cached Images

<h2 align="center">📸 Deployment Proof</h2>

<div align="center">
  <img width="800"  alt="1" src="https://github.com/user-attachments/assets/df56a0cd-e65d-44e3-b6bf-f8a97c1f548f" />

  <p><em>Fig 1: [BunnyNet] CDN Dashboard.</em></p>

 

   <img width="800"  alt="2" src="https://github.com/user-attachments/assets/d7f3c115-39f3-4152-9b65-f66d7de568b5" />
  <p><em>Fig 2: Assests[Images] being stored in CDN storage</em></p>

   

   <img width="800"  alt="3" src="https://github.com/user-attachments/assets/966f2a95-9e79-4a0d-bc9c-d1fd868f5a26" />
  <p><em>Fig 3: Linked HostNames in BunnyNet</em></p>

   
   <img width="800"  alt="4" src="https://github.com/user-attachments/assets/bfcbffc7-1c80-40d6-95e7-43fadb7d3a45" />
  <p><em>Fig 4: Caching being used in CDN [Usage Stats]</em></p>

   <img width="800"  alt="5final" src="https://github.com/user-attachments/assets/af0cd806-f027-479c-8da8-14eed5d2aa0d" />
  <p><em>Fig 5: All 3: AWS Instance + BunnyNet CDN + Vercel  attached to my custom domain[DNS Routing] +</em></p>
</div>

<img width="800"  alt="6" src="https://github.com/user-attachments/assets/3572b526-5c77-4fa6-a1e2-68a7b79a82a7" />
 <p><em>Fig 6: Usage Hours of Instance running in AWS Dashboard</em></p>
</div>

<br />
## 🔍 Component Breakdown (What it does → What I learned)

### 1️⃣ AWS EC2 (Virtual Private Server)

**What it does:**  
AWS EC2 provides a virtual Linux server where applications and services can run.

**Why I used it:**  
To learn how websites are hosted without managed platforms.

**What I did:**
- Launched an Ubuntu EC2 instance
- Connected via SSH
- Managed files and services using the Linux CLI
- Configured security groups (ports 22, 80, 443)

---

### 2️⃣ Nginx (Reverse Proxy)

**What it does:**  
Nginx sits between the internet and the application.  
It receives incoming requests and forwards them to the correct service.

**Why it matters:**  
- Hides internal application ports
- Improves security
- Enables SSL and future scalability

**What I learned:**
- How reverse proxies work
- How HTTP requests are forwarded
- How misconfiguration causes `502 Bad Gateway` errors

---

### 3️⃣ SSL & Certbot (HTTPS)

**What it does:**  
Certbot automatically issues and manages SSL certificates using Let’s Encrypt.

**Why it matters:**  
- Encrypts data between browser and server
- Required for modern websites
- Builds trust and security

**What I did:**
- Installed Certbot on the EC2 instance
- Generated SSL certificates
- Enabled HTTPS via Nginx

---

### 4️⃣ Custom Domain & DNS

**What it does:**  
DNS maps a human-readable domain name to a server’s IP address.

**Why it matters:**  
- Required for real production websites
- Enables SSL and branding

**What I learned:**
- A records and domain pointing
- How DNS connects domain → server
- Common mistakes with incorrect IP mapping

---

### 5️⃣ BunnyCDN (Content Delivery Network)

**What it does:**  
A CDN caches static files (images, CSS) on global edge servers and serves them closer to users.

**Why it matters:**  
- Faster load times
- Reduced server load
- Better user experience

**How it was used:**
- Images were hosted and served via BunnyCDN
- CDN pulled assets from its origin and cached them
- Website referenced CDN URLs for images

---

## 📉 Cost & Migration Note 

The project was originally hosted fully on **AWS EC2**.

After completing the learning goals:
- I closed the instance[after a while], it took quite a few of my free credits.
- Kept this repository as documentation of the original deployment.
- Same with the BunnyCDN, my free trial expired.

---

##  Learnings

- How HTTP requests travel from **DNS → Server → Application**
- Why reverse proxies are essential in backend systems
- How SSL works in practice, not just theory
- How CDNs improve performance and scalability
- How to debug:
  - `502 Bad Gateway` errors
  - Nginx error logs
  - Misconfigured ports and DNS issues
