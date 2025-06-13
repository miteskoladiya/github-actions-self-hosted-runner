# 🚀GitHub Actions with Self-Hosted Runner on AWS EC2

This repository demonstrates how to set up a **Self-Hosted Runner** for GitHub Actions using an **AWS EC2 instance**.

## 🧾 Prerequisites

- A GitHub repository
- An AWS EC2 instance (Amazon Linux/Ubuntu recommended)
- Basic Linux and terminal knowledge

---

## ⚙️ Step-by-Step Setup Guide

### 1. Launch EC2 Instance

- Go to AWS EC2 dashboard
- Launch a new instance (Ubuntu preferred)
- Configure security group:
  - Allow inbound access on **port 22 (SSH)**
  - Outbound access should be unrestricted for GitHub communication

---

### 2. Connect to EC2 via SSH

```bash
ssh -i "your-key.pem" ec2-user@your-ec2-ip

```

---

### 3. Create a GitHub Runner from Your Repo
Go to your GitHub repository → Settings → Actions → Runners → New self-hosted runner

Choose OS: Linux

Copy the 3 setup commands shown there (example below):

# Download runner package
curl -o actions-runner-linux-x64-2.314.1.tar.gz -L https://github.com/actions/runner/releases/download/v2.314.1/actions-runner-linux-x64-2.314.1.tar.gz

# Extract it
tar xzf ./actions-runner-linux-x64-2.314.1.tar.gz

# Configure it with token
./config.sh --url https://github.com/your-username/your-repo --token YOUR_TOKEN

---

### 4. Start the Runner
./run.sh

Once started, the terminal will show:
Listening for jobs...

---
### 5. Update GitHub Workflow to Use Self-Hosted Runner
Edit your .github/workflows/your-workflow.yml and add:

runs-on: self-hosted
---




