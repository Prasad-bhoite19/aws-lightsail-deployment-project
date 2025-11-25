# 🚀 AWS Lightsail Deployment Project

![AWS Lightsail](https://img.shields.io/badge/AWS-Lightsail-blue?logo=amazonaws)

![Status](https://img.shields.io/badge/Status-Completed-success)

![License](https://img.shields.io/badge/License-MIT-yellow)

**Author:** Prasad  
**Date:** 25-Nov-2025  

---

## 📖 Project Overview

- AWS Lightsail is an easy-to-use cloud platform that simplifies launching and managing virtual servers, databases, and networking.  
- This project demonstrates **deploying a web application on Lightsail**, including server setup, security, SSL, and domain integration.

## Key Features:
- Simple VPS setup with static IP  
- Firewall & security configuration  
- Deploy web applications (Node.js, PHP, WordPress, etc.)  
- SSL via Certbot  
- Snapshots & backup for disaster recovery  

---

## 🌐 Architecture Diagram
```

                     ┌────────────────────────────┐
                     │        End Users            │
                     │  (Web / Mobile Clients)     │
                     └───────────────┬────────────┘
                                     │
                                     ▼
                         ┌─────────────────────┐
                         │  Lightsail Static   │
                         │   Public IP / DNS   │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │  AWS Lightsail       │
                         │    Instance          │
                         │  (Linux/Ubuntu)      │
                         ├─────────────────────┤
                         │ Application Code     │
                         │ Web Server (Nginx /  │
                         │ Apache / NodeJS etc) │
                         └──────────┬──────────┘
                                    │
                        ┌───────────┴───────────┐
                        │                       │
                        ▼                       ▼
             ┌──────────────────┐      ┌──────────────────┐
             │ Lightsail DB      │      │ Lightsail Storage│
             │ (MySQL/Postgres)  │      │  (Object/Static) │
             └──────────────────┘      └──────────────────┘
                        │
                        ▼
           ┌──────────────────────────────┐
           │ Optional: Lightsail CDN      │
           │ (Global Cached Content)      │
           └──────────────────────────────┘
                        │
                        ▼
             ┌───────────────────────────┐
             │   CloudWatch Metrics       │
             │   Logs / Monitoring        │
             └───────────────────────────┘
```
## 🏗 Architecture Components

- Component	Description
- Lightsail Instance	Virtual private server to host applications
- Static IP	Permanent IP for DNS and domain mapping
- Domain / DNS	Connect your custom domain to the instance
- Firewall / Security	Manage inbound/outbound traffic safely
- Lightsail Database	Optional managed database for applications
- Snapshots	Backup instances and data for recovery

## 🛠 Prerequisites

- Active AWS account
- Basic Linux knowledge & SSH client
- Domain name (optional)
- Lightsail subscription enabled

## ⚡ Step-by-Step Deployment

### 1️⃣ Launch Lightsail Instance

- Go to AWS Lightsail Console
- Click Create instance
- Select Region & Platform (Linux/Unix or Windows)
- Choose Blueprint (OS only, WordPress, Node.js, etc.)
- Pick Instance plan based on your needs
- Name the instance → Create instance

### 2️⃣ Connect via SSH

- **Browser SSH: Click Connect using SSH**

- Terminal SSH:
```
ssh -i /path/to/key.pem username@your-static-ip
```
### 3️⃣ Configure Firewall & Networking

- Go to Networking → Firewall
- Add rules for:
  - HTTP → 80
  - HTTPS → 443
  - SSH → 22 (optional)

- Allocate Static IP → attach to instance

### 4️⃣ Install Web Server (Example: Nginx)
```
sudo apt update
```

```
sudo apt install nginx -y
```

```
sudo systemctl start nginx
```

```
sudo systemctl enable nginx
```

### 5️⃣ Deploy Your Application

- Upload files via SCP / SFTP / Lightsail console
- Configure Nginx / Apache to serve your app

Restart server:
```
sudo systemctl restart nginx
```
### 6️⃣ Domain Setup (Optional)

- Point domain A record to Lightsail Static IP
- Test by visiting your domain

### 7️⃣ Enable SSL (HTTPS)
```
sudo apt install certbot python3-certbot-nginx -y
```

```
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
```
- Verify HTTPS by visiting your domain

### 8️⃣ Create Snapshots (Backup)

- Go to Snapshots → Create snapshot → Name it for reference

## 🔒 Security Best Practices

- *Use SSH key authentication only, disable password login*

- Keep server updated:
```
sudo apt update && sudo apt upgrade -y
```
- Enable automatic security updates:
```
sudo apt install unattended-upgrades -y
```
- *Restrict firewall rules to only necessary ports*

## 📊 Monitoring & Logs

- *Lightsail metrics: CPU, Network, Disk*

- Logs:
```
sudo tail -f /var/log/nginx/access.log
```

```
sudo tail -f /var/log/nginx/error.log
```
## ⚙ Useful Commands

- Action	Command

- SSH to instance	
```
ssh -i key.pem user@ip
```
- Update server
```
sudo apt update && sudo apt upgrade -y
```
- Restart Nginx	
```
sudo systemctl restart nginx
```
- Check server status	
```
sudo systemctl status nginx
```
- *Backup snapshot	Lightsail Console → Snapshots*

## 🌟 Optimization Tips

- Start with smallest instance → scale later
- Enable Lightsail Load Balancer for high traffic
- Use caching with CloudFront
- Delete unused snapshots/instances to save costs

## 🛠 Troubleshooting

- Instance unreachable: Check firewall & Static IP
- Website not loading: Ensure web server running & DNS propagated
- SSL errors: Check logs at /var/log/letsencrypt/

## 🔧 Future Enhancements

- Automate instance creation using Terraform / CloudFormation
- Multi-tier architecture (App + DB + Cache)
- CI/CD pipelines for auto-deployment
- Integrate CloudWatch alerts & monitoring

## 📚 References

- AWS Lightsail Documentation
- AWS Blog Tutorials
- Certbot Documentation

## 🙌 Author
Prasad

## 📩 Connect With Me :-

If you’d like to collaborate, discuss projects, or just say hello — feel free to reach out!  

### 🔗 Social & Professional Links
- 🌐 [Portfolio Website](https://prasad-bhoite19.github.io/prasad-portfolio/)  
- 💼 [LinkedIn](http://linkedin.com/in/prasad-bhoite-a38a64223)  
- 🐙 [GitHub](https://github.com/Prasad-bhoite19)  
- ✉️ [Email](prasadsb2002@gmail.com)  

💬 Always open for opportunities in **Cloud, DevOps, and Full-Stack Projects**
