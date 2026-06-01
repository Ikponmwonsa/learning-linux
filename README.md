**INSTRUCTOR DETAILS**


| Information |	Details |
| ------------| ------- |
| Name	| Ikponmwonsa Okundigie |
| Email | okundigieamen@gmail.com |
| Website | https://dev.to/ikay |
| LinkedIn profile | https://www.linkedin.com/in/ikponmwonsa-okundigie-7731a92b6/ |

# The Ultimate Linux Command Cheatsheet for Real-World DevOps & Cloud Engineers

If you want to stand out as a Cloud Engineer, DevOps Engineer, Systems Administrator, SRE, Platform Engineer, or Backend Engineer, Linux is not optional — it is the backbone of modern infrastructure.

From AWS EC2 servers to Azure Virtual Machines, Docker containers, Kubernetes clusters, CI/CD pipelines, cybersecurity operations, and enterprise automation — Linux powers nearly everything.

This guide is designed like a real-world tech company environment.

You’ll learn:

- Essential Linux commands
- Real enterprise scenarios
- Production troubleshooting
- Cloud & DevOps workflows
- Security operations
- Networking
- Monitoring
- GitHub project structure
- Resume-ready project experience

Real-World Scenario

Imagine you just got hired as a Junior Cloud/DevOps Engineer at a fintech company.

Your daily responsibilities include:

- Managing Linux servers on AWS/Azure
- Monitoring applications
- Troubleshooting outages
- Managing users and permissions
- Automating backups
- Configuring NGINX
- Deploying applications
- Checking logs
- Monitoring CPU/RAM
- Using Git and Docker
- Handling incidents during production outages

This cheatsheet teaches Linux exactly the way engineers use it in real companies.

1. ## Linux Navigation Commands

These are the commands engineers use every minute.

```bash
| Command  | Purpose                  | Real-World Scenario                    |
| -------- | ------------------------ | -------------------------------------- |
| `pwd`    | Show current directory   | Confirm server path before deployment  |
| `ls`     | List files               | Check application files                |
| `ls -la` | Detailed hidden files    | Inspect `.env` or config files         |
| `cd`     | Change directory         | Navigate to app folders                |
| `clear`  | Clear terminal           | Clean workspace during troubleshooting |
| `tree`   | Display folder structure | Visualize project architecture         |
```

Example

```bash
pwd
ls -la
cd /var/www/application
```

**_Real Company Usage_**

A DevOps engineer checks deployment folders before restarting production services.

---

2. ## File & Directory Management

```bash
| Command          | Purpose                      |
| ---------------- | ---------------------------- |
| `touch file.txt` | Create file                  |
| `mkdir logs`     | Create folder                |
| `rm file.txt`    | Delete file                  |
| `rm -rf folder`  | Delete directory recursively |
| `cp file1 file2` | Copy file                    |
| `mv old new`     | Rename/move file             |
```

Example

```bash
mkdir backup
cp app.log backup/
mv old.conf new.conf
```

**_Real Scenario_**

Before updating production configs, engineers back up old configuration files.

---

3. ## Viewing File Content

```bash
| Command   | Purpose             |
| --------- | ------------------- |
| `cat`     | View entire file    |
| `less`    | Scroll through logs |
| `head`    | First lines         |
| `tail`    | Last lines          |
| `tail -f` | Live log monitoring |
```

Example

```bash
tail -f /var/log/nginx/error.log
```

**_Real Scenario_**
During outages, engineers monitor live application logs.

---

4. ## User & Permission Management
   Linux security heavily depends on permissions.

```bash
| Command   | Purpose              |
| --------- | -------------------- |
| `whoami`  | Current user         |
| `sudo`    | Run as administrator |
| `useradd` | Create user          |
| `passwd`  | Set password         |
| `chmod`   | Change permissions   |
| `chown`   | Change ownership     |
```

Example

```bash
sudo useradd devops
sudo passwd devops
chmod 755 deploy.sh
chown ubuntu:ubuntu app.py
```

**_Real Scenario_**

New engineers receive SSH access to production servers.

---

5. ## Process Management

```bash
| Command       | Purpose                     |
| ------------- | --------------------------- |
| `ps aux`      | Show running processes      |
| `top`         | Real-time system monitoring |
| `htop`        | Interactive monitoring      |
| `kill PID`    | Stop process                |
| `pkill nginx` | Kill by name                |
```

Example

```bash
ps aux | grep nginx
kill 2334
```

**_Real Scenario_**

An application crashes and consumes 100% CPU. Engineers identify and stop the faulty process.

---

6. ## Networking Commands
   Critical for Cloud & DevOps.

```bash
| Command          | Purpose                |
| ---------------- | ---------------------- |
| `ping`           | Connectivity test      |
| `curl`           | API testing            |
| `wget`           | Download files         |
| `netstat -tulnp` | Open ports             |
| `ss -tulnp`      | Modern port inspection |
| `ip a`           | Show IP address        |
| `traceroute`     | Network path           |
```

Example

```bash
curl http://localhost:8080
ping google.com
ss -tulnp
```

**_Real Scenario_**

Engineers verify APIs after deployment.

---

7. ## Disk & Storage Management

```bash
| Command  | Purpose         |
| -------- | --------------- |
| `df -h`  | Disk usage      |
| `du -sh` | Folder size     |
| `mount`  | Mounted drives  |
| `lsblk`  | Storage devices |
```

Example

```bash
df -h
du -sh /var/log
```

**_Real Scenario_**

Production server runs out of disk space due to large logs.

---

8. ## Package Management
   Ubuntu/Debian

```bash
sudo apt update
sudo apt install nginx
```

**RHEL/CentOS**

```bash
sudo yum install nginx
```

**_Real Scenario_**

Installing monitoring agents or web servers.

---

9. ## Service Management (Systemd)

```bash
| Command                   | Purpose       |
| ------------------------- | ------------- |
| `systemctl start nginx`   | Start service |
| `systemctl stop nginx`    | Stop service  |
| `systemctl restart nginx` | Restart       |
| `systemctl status nginx`  | Check status  |
| `systemctl enable nginx`  | Auto-start    |
```

Example

```bash
sudo systemctl restart nginx
sudo systemctl status nginx
```

**_Real Scenario_**
Restarting applications after deployment.

---

10. ## Linux Logs & Monitoring

```bash
| Command      | Purpose       |
| ------------ | ------------- |
| `journalctl` | System logs   |
| `dmesg`      | Kernel logs   |
| `free -m`    | Memory usage  |
| `uptime`     | System uptime |
```

Example

```bash
journalctl -u nginx
free -m
```

**_Real Scenario_**
Troubleshooting server crashes.

---

11. ## SSH & Remote Access

```bash
| Command | Purpose      |
| ------- | ------------ |
| `ssh`   | Remote login |
| `scp`   | Secure copy  |
| `rsync` | File sync    |
```

Example

```bash
ssh ubuntu@10.0.0.5
scp app.py ubuntu@10.0.0.5:/var/www
```

**_Real Scenario_**
Deploying applications to cloud servers.

---

12. ## Linux + Git Workflow

```bash
| Command         | Purpose        |
| --------------- | -------------- |
| `git clone`     | Download repo  |
| `git status`    | Check changes  |
| `git add .`     | Stage files    |
| `git commit -m` | Commit         |
| `git push`      | Upload changes |
```

Example

```bash
git clone repo-url
git add .
git commit -m "Updated deployment script"
git push origin main
```

**_Real Scenario_**
Pushing infrastructure automation scripts.

---

13. ## Linux + Docker Workflow
    Docker Commands

```bash
| Command         | Purpose            |
| --------------- | ------------------ |
| `docker ps`     | Running containers |
| `docker images` | Images             |
| `docker build`  | Build image        |
| `docker run`    | Run container      |
| `docker logs`   | View logs          |
```

Example

```bash
docker build -t fintech-app .
docker run -d -p 80:80 fintech-app
```

**_Real Scenario_**

Deploying containerized microservices.

---

14. ## Linux + AWS Real Scenario
    **Situation**

Your production API is down.
**Troubleshooting Steps**

```bash
ssh ubuntu@server-ip

systemctl status nginx

tail -f /var/log/nginx/error.log

df -h

free -m

curl localhost:8000
```

**Root Cause**

Disk became full due to oversized logs.

**Resolution**

```bash
rm -rf old-logs
systemctl restart nginx
```

**Business Impact**

Application restored for thousands of customers.

This is exactly what recruiters want to hear.

---

15. ## Linux Automation with Bash Scripting

**backup.sh**

```bash
#!/bin/bash

DATE=$(date +%F)

tar -czf backup-$DATE.tar.gz /var/www/html

echo "Backup completed"
```

**Run Script**

```bash
chmod +x backup.sh
./backup.sh
```

**Real Scenario**

Automated nightly backups for production systems.

---

16. ## CI/CD Linux Deployment Flow
    **Pipeline Flow**

```bash
Developer Pushes Code
        ↓
GitHub Actions/Jenkins
        ↓
Linux Build Server
        ↓
Docker Build
        ↓
Testing
        ↓
Deploy to AWS EC2
        ↓
NGINX Reverse Proxy
        ↓
Production
```

