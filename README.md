I built a real-world Linux + DevOps production environment simulating a fintech infrastructure using Ubuntu, Docker, NGINX, Bash scripting, GitHub Actions, and cloud deployment practices.
This project helped me understand:

- [x] Linux Administration
- [x] Production Troubleshooting
- [x] Docker & Container
- [x] Monitoring & Logging
- [x] CI/CD Pipelines
- [x] Infrastructure Automation
- [x] DevOps Workflows

---

# REAL LIVE LINUX + DEVOPS PROJECT

**“Enterprise FinTech Infrastructure Simulation”**

This project will simulate what happens inside a real tech company.

You will act as:

- Linux System Administrator
- Cloud Engineer
- DevOps Engineer
- Site Reliability Engineer (SRE)

---

# PROJECT OVERVIEW

**Business Scenario**

A fintech startup called **PayFlowX** needs infrastructure for:

- Hosting a payment API
- Running a web application
- Monitoring server health
- Automating backups
- Managing Linux users
- Running Docker containers
- Reverse proxy using NGINX
- CI/CD deployment pipeline
- Incident monitoring

You are the Devops Engineer responsible.

---

# PROJECT ARCHITECTURE

                     INTERNET
                         │
                         ▼
                  NGINX Reverse Proxy
                         │
        ┌────────────────────────────────┐
        │                                │
        ▼                                ▼

Docker Container 1 Docker Container 2
Frontend App Backend API
│ │
└──────────────┬─────────────────┘
▼
Linux Ubuntu Server
│
┌─────────────┼─────────────┐
▼ ▼ ▼
Monitoring Backups Logging

---

# TECH STACK

| Technology           | Purpose          |
| -------------------- | ---------------- |
| Ubuntu Linux         | Server OS        |
| Docker               | Containerization |
| NGINX                | Reverse proxy    |
| GitHub               | GitHub           |
| Bash Scripting       | Automation       |
| AWS EC2 / VirtualBox | Hosting          |
| GitHub Actions       | CI/CD            |
| Linux Commands       | Administration   |
| SSH                  | Remote access    |
| Journalctl           | Logs             |
| Htop                 | Monitoring       |

---

## STEP 1 — CREATE YOUR SERVER

**OPTION A — AWS EC2**

**Create:**

- Ubuntu Server 22.04
- t2.micro
- Allow:
  - SH (22)
  - HTTP (80)
  - HTTPS (443)

**Connect**

```Bash
ssh -i key.pem ubuntu@your-public-ip
```

---

**OPTION B — VirtualBox**

Install:

- Ubuntu Server ISO
- 2GB RAM
- 20GB Storage

---

## STEP 2 — PROJECT STRUCTURE

```Plain text

payflowx-devops-project/
│
├── app/
│ ├── frontend/
│ └── backend/
│
├── nginx/
│ └── nginx.conf
│
├── scripts/
│ ├── backup.sh
│ ├── cleanup.sh
│ └── monitor.sh
│
├── docker/
│ └── Dockerfile
│
├── logs/
│
├── screenshots/
│
├── README.md
│
└── deployment-guide.md
```

---

## STEP 3 — INSTALL SOFTWARE ESSENTIAL TOOLS

```Bash
sudo apt update

sudo apt install -y \
docker.io \
nginx \
git \
curl \
wget \
htop \
net-tools
```

---

## STEP 4 — CREATE A SIMPLE APPLICATION

### Backend API

**Create folder:**

```Bash
mkdir -p app/backend
cd app/backend
```

Create file:

```Bash
nano app.py
```

**Paste:**

```python

from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "PayFlowX API Running Successfully"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

## STEP 5 — CREATE DOCKERFILE

```Bash
nano Dockerfile
```

**Paste:**

```Dockerfile

FROM python:3.10

WORKDIR /app

COPY . .

RUN pip install flask

CMD ["python", "app.py"]
```

---

## STEP 6 — BUILD & RUN CONTAINER

```Bash
docker build -t payflowx-api .

docker run -d -p 5000:5000 payflowx-api
```

**Verify:**

```docker ps
curl localhost:5000
```

**Expected:**

```Plain Text
PayFlowX API Running Successfully
```

---

## STEP 7 — CONFIGURE NGINX REVERSE PROXY

```Bash
sudo nano /etc/nginx/sites-available/payflowx
```

**Paste:**

```Nginx
server {
    listen 80;

    location / {
        proxy_pass http://127.0.0.1:5000;
    }
}
```

**Enable:**

```Bash
sudo ln -s /etc/nginx/sites-available/payflowx /etc/nginx/sites-enabled/

sudo nginx -t

sudo systemctl restart nginx
```

---

# REAL-WORLD SCENARIO

Now your fintech API is:

- Running in Docker
- Behind NGINX
- Accessible publicly
- Hosted on Linux

This mirrors real production infrastructure.

---

## STEP 8 — USER MANAGEMENT

**Create developers:**

```Bash
sudo useradd devops
sudo useradd backend
sudo passwd devops
```

**Grant sudo access:**

```Bash
sudo usermod -aG sudo devops
```

---

# STEP 9 — SERVER MONITORING

**CPU & RAM**

```Bash

top
htop
free -m
```

**Disk**

```Bash
df -h
du -sh /var/log
```

**Logs**

```Bash
journalctl -u nginx

tail -f /var/log/nginx/access.log
```

---

# STEP 10 — INCIDENT RESPONSE SIMULATION

**Scenario**

Website becomes unavailable.
Troubleshooting Workflow

**Check Container**

```Bash
docker ps
```

**Check NGINX**

```Bash
systemctl status nginx
```

**Check Ports**

``Bash
ss -tulnp

````

**Check Logs**
```Bash
tail -f /var/log/nginx/error.log
````

---

# STEP 11 — AUTOMATE BACKUPS SCRIPT

**Create:**

```Bash
nano backup.sh
```

**Paste:**

```Bash
#!/bin/bash
DATE=$(date +%F)

tar -czf /backup/payflowx-$DATE.tar.gz /home/ubuntu/payflowx-devops-project

echo "Backup Completed"
```

**Make executable:**

```Bash
chmod +x backup.sh
```

**Run:**

```Bash
./backup.sh
```

---

# STEP 12 — AUTOMATE USING CRON JOBS

```Bash
crontab -e
```

**Add:**

```Bash
0 2 * * * /home/ubuntu/scripts/backup.sh
```

This will run the backup script daily at 2 AM.

# STEP 13 — SECURITY HARDENING

**Firewall**

```Bash
sudo ufw allow OpenSSH
sudo ufw allow 80
sudo ufw enable
```

**Fail2Ban**

```Bash
sudo apt install fail2ban
```

---

# STEP 14 — GITHUB INTEGRATION

**Initialize repo:**

```Bash
git init
git add .
git commit -m "Initial DevOps project"
```

**Push to GitHub:**

```Bash
git remote add origin YOUR_GITHUB_REPO

git push -u origin main
```

---

# STEP 15 — ADD CI/CD PIPELINE

**Create:**

```Plain text
.github/workflows/deploy.yml
```

**Paste:**

```YAML
name: Deploy Application

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v3
```

---

# STEP 16 — SCREENSHOTS FOR RECRUITERS

**Take screenshots of:**

- Docker running
- NGINX status
- Linux terminal
- htop monitoring
- GitHub repo
- CI/CD pipeline
- Logs
- Backup execution

**Store inside:**

```Plain text
screenshots/
```
