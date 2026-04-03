# 🚀 Zira Plus – EC2 Deployment, Git & Jira Integration

A practical workflow to connect AWS EC2, manage code with Git, and notify your manager using **Jira Ticket IDs** whenever you push code to GitHub.

---

## 📖 Overview

This repository demonstrates:

* 🔐 Connecting to AWS EC2 using SSH
* ⚙️ Setting up an Ubuntu server
* 🔗 GitHub integration
* 🧾 Using **Jira Ticket IDs in commits**
* 📤 Automatic updates when pushing code

---

## 🛠️ Tech Stack

* ☁️ AWS EC2 (Ubuntu)
* 🔧 Git & GitHub
* 🧾 Jira (Task Management)
* 💻 Linux CLI

---

## ⚙️ Setup Guide

### 🔑 Connect to EC2

```bash
chmod 400 your-key.pem
ssh -i "your-key.pem" ubuntu@your-ec2-public-ip
```

---

### 📦 Install Git

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git -y
```

---

### 🔗 Clone Repository

```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

---

### ⚙️ Configure Git

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

---

## 🧾 Jira Ticket Workflow (Important)

### ✅ Commit with Jira Ticket ID

Always include your Jira Ticket ID in commit messages:

```bash
git commit -m "ZIRA-101: Login API completed"
```

Examples:

```bash
git commit -m "ZIRA-102: Fixed payment bug"
git commit -m "ZIRA-103: UI improvements"
```

👉 This helps:

* Track work in Jira
* Notify manager automatically
* Maintain professional workflow

---

## 🔗 GitHub Push Workflow

```bash
git add .
git commit -m "ZIRA-101: Feature completed"
git push origin main
```

---

## 🔔 Automatic Manager Notification (Best Practice)

### Option 1: Using Commit Message (Simple)

When you push code with Jira ID:

* Jira automatically links commit
* Manager can see updates in Jira dashboard

---

### Option 2: Git Hook (Auto Enforce Jira ID)

Create a commit hook:

```bash
nano .git/hooks/commit-msg
```

Paste this:

```bash
#!/bin/sh

if ! grep -q "ZIRA-" "$1"; then
  echo "❌ Commit message must include Jira Ticket ID (e.g., ZIRA-101)"
  exit 1
fi
```

Make executable:

```bash
chmod +x .git/hooks/commit-msg
```

👉 Now commits without Jira ID will be rejected.

---

### Option 3: GitHub + Jira Integration

* Connect GitHub repo with Jira
* Enable **Development panel** in Jira
* Every push → automatically visible in Jira

---

## 🌐 Run Project (Example)

```bash
python3 manage.py runserver 0.0.0.0:8000
```

Open in browser:

```
http://your-ec2-public-ip:8000
```

---

## ⚠️ Troubleshooting

### ❌ Permission Denied

```bash
chmod 400 your-key.pem
```

### ❌ Jira Not Linking

* Check ticket ID format (e.g., ZIRA-101)
* Ensure GitHub is connected to Jira

---

## 📌 Useful Commands

```bash
git status
git log
ls
cd folder
```

---

## 🎯 Workflow Summary

```text
Write Code → Add Jira ID → Commit → Push → Jira Updated → Manager Notified
```

---

## 📜 License

Free to use for learning and development.

---

## 💡 Author

**Yash Gondaliya**
IT Student | Developer 🚀
