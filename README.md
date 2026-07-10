# AWS DevOps Engineer Intern Assignment

A simple static website deployed on an AWS EC2 instance using Nginx, with the source code managed through Git and GitHub.

## 📋 Overview

| Detail | Value |
|---|---|
| **Name** | Pranay Adavade |
| **College** | Viva College |
| **Branch** | B.Sc. IT |
| **EC2 Public IP** | 50.16.72.203 |
| **Elastic IP (Bonus)** | 107.21.252.38 |
| **Total Time Taken** | 2.5 hours |

## 🎯 Objective

Deploy a static website on an AWS EC2 instance using Nginx as the web server, manage the source code with Git/GitHub, and document the entire process end-to-end.

## ☁️ AWS Services Used

- **Amazon EC2** — Ubuntu Server (t2.micro, free-tier eligible) to host the website
- **Security Groups** — Inbound rules for SSH (port 22) and HTTP (port 80)
- **Key Pairs** — `.pem` file for secure SSH authentication
- **Elastic IP (Bonus)** — Static public IP so the address doesn't change on instance restart

## 🛠️ Setup Steps

### 1. Launch EC2 Instance
Launched an Ubuntu EC2 instance, generated a key pair for SSH access, and created a security group allowing ports 22 and 80.

```bash
ssh -i myfirst-key.pem ubuntu@ec2-50-16-72-203.compute-1.amazonaws.com
```

### 2. Install & Configure Nginx
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

Verified with:
```bash
sudo systemctl status nginx
free -h        # memory usage
df -h          # disk usage
top            # running processes
```

### 3. Deploy the Website
Replaced the default Nginx landing page with a custom HTML page containing personal details.

```bash
sudo nano /var/www/html/index.html
sudo systemctl restart nginx
```

Verified live at the EC2 public IP in a browser.

### 4. Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/pranayadavade15/aws-devops-intern-assignment.git
git pull origin main --allow-unrelated-histories --no-rebase
git branch -M main
git push -u origin main
```

### 5. Bonus: Elastic IP
Allocated and associated an Elastic IP (`107.21.252.38`) so the public address stays fixed across instance restarts.

## 🐛 Problems Faced & Fixes

| Problem | Fix |
|---|---|
| Untracked file conflict on pull | Ran `git add` + `git commit` locally before pulling |
| Divergent/unrelated branch histories | Used `--allow-unrelated-histories --no-rebase` |
| Vim editor opened for merge commit | Pressed `Esc`, typed `:wq` to save & exit |
| `master` vs `main` branch mismatch | Ran `git branch -M main` before pushing |
| GitHub password auth deprecated | Used a Personal Access Token (PAT) + `credential.helper store` |

## 📚 Key Learnings

- Launching and configuring EC2 instances, security groups, and key-pair SSH access
- How Nginx serves static content and how to customize the landing page
- Core Linux commands for service status, disk usage, memory, and process monitoring
- Git workflow for resolving unrelated-history conflicts (web upload vs. local commits)
- GitHub authentication via Personal Access Tokens
- The purpose of an Elastic IP for a consistent public address

## 🔗 Links

- **Live Site:** `http://50.16.72.203` (or Elastic IP: `http://107.21.252.38`)
- **Repository:** https://github.com/pranayadavade15/aws-devops-intern-assignment

---
*Full documentation with screenshots available in the assignment report.*
