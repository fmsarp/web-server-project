# 🐧 Personal Linux-Based Web Server with Automated Backups

Welcome! This project is part of my post-DevOps Bootcamp journey to deepen my Linux, Bash scripting, and system automation skills. It involves building a personal web server on Ubuntu, hosting a static HTML page with Nginx, and automating daily backups using a custom Bash script and cron.

---

## 📌 Project Goals

* Set up a Linux virtual server running Nginx
* Host a simple HTML web page
* Write a Bash script to back up website files daily
* Automate the backup using cron
* Secure the server with basic best practices

---

## ⚙️ Tools & Technologies

* 🐧 **Ubuntu Server 22.04 LTS**
* 🧱 **Nginx**
* 🖥️ **VirtualBox** (or any virtualization platform)
* 📜 **Bash Scripting**
* ⏱️ **cron**
* 🔥 **UFW (Uncomplicated Firewall)**
* 💾 **Git / GitHub** for version control and documentation

---

## 🚀 Project Setup

### 1. Virtual Machine Setup

* Installed Ubuntu Server 22.04 LTS via VirtualBox
* Allocated: 4 GB RAM, 25 GB storage, 2 CPU cores
* Enabled SSH for remote access

### 2. Install and Configure Nginx

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

* Created a simple HTML page at `/var/www/html/index.html`

```html
<!DOCTYPE html>
<html>
<body>
<h1>My DevOps Web Server</h1>
<p>Welcome to my first Linux project!</p>
</body>
</html>
```

---

## 📦 Automated Backup Script

### Script: `backup-web.sh`

```bash
#!/bin/bash
# Backup script for web server files
BACKUP_DIR="$HOME/backups"
SOURCE_DIR="/var/www/html"
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_FILE="web_backup_$DATE.tar.gz"

if [ -d "$SOURCE_DIR" ]; then
    tar -czf "$BACKUP_DIR/$BACKUP_FILE" "$SOURCE_DIR"
    echo "Backup created: $BACKUP_FILE"
else
    echo "Error: Source directory $SOURCE_DIR does not exist"
    exit 1
fi
```

* Make it executable: `chmod +x ~/backup-web.sh`
* Test: Run manually and verify `.tar.gz` file in `~/backups/`

---

## 📅 Automate with Cron

* Schedule: Daily at 2 AM

```bash
crontab -e
```

Add:

```bash
0 2 * * * /home/<your-username>/backup-web.sh >> /home/<your-username>/backups/backup.log 2>&1
```

---

## 🔐 Server Security

* Installed and configured `ufw` firewall

```bash
sudo apt install ufw -y
sudo ufw allow 80/tcp
sudo ufw allow 22/tcp
sudo ufw enable
```

* Created a new sudo user and disabled root SSH login

---

## 📚 What I Learned

* VM provisioning and Linux server setup
* Nginx configuration and static web hosting
* Writing and debugging Bash scripts
* Task automation using cron
* Basic server hardening and user access control

---

## 💡 Possible Extensions

* Add MySQL and PHP to create a LAMP stack
* Containerize the server using Docker
* Automate the full setup using Ansible
* Deploy to AWS using the Free Tier

---

## 🔗 Resources

* [Ubuntu Server Docs](https://ubuntu.com/server/docs)
* [Nginx Beginner’s Guide](https://nginx.org/en/docs/)
* [freeCodeCamp Bash Scripting](https://www.youtube.com/playlist?list=PLWKjhJtqVAbkFiqHnNaxpOPhh9tSWMXIF)
* [Learn Linux in 5 Days (Udemy)](https://www.udemy.com/course/learn-linux-in-5-days/) *(optional)*

---

## 🧠 Next Steps

✅ **Part 1**: Linux Project - ✅ Complete
🔜 **Part 2**: Learn Ansible for configuration management
🔜 **Part 3**: Dockerize the Nginx web server
🔜 **Part 4**: Implement CI/CD with GitHub Actions
🔜 **Part 5**: Deploy on AWS Free Tier
🔜 **Part 6**: Study for RHCSA/CKA certification

---

## 🙌 Feedback & Collaboration

Feel free to fork this repo, try the project yourself, or open issues if you have ideas for improvement.
Let’s connect on [LinkedIn](https://linkedin.com) or share feedback on [X/Twitter](https://twitter.com)!

---

## 📸 Screenshots

*(Include images like terminal output, your webpage in a browser, or your backup directory structure)*
[Website](https://github.com/user-attachments/assets/b9d31848-27ee-481d-9948-1cb0e43398ce)
[Script execution output](https://github.com/user-attachments/assets/818e88e3-bd58-4473-9daf-8c40fe2b6ae3)
[backup log](https://github.com/user-attachments/assets/4be1e3a4-125a-41fe-8a6c-33a2e2873143)



---
