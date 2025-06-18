---
sidebar_position: 5
---

# 🔌 How to Get Socket URL

## 📋 Overview
Learn how to set up WebSocket server and get your Socket URL for real-time communication in e-School SaaS.

### 1️⃣ Install Required Packages
Open the Terminal from an SSH Connection:

```bash
sudo apt-get update
```

```bash
sudo apt-get install supervisor
```

### 2️⃣ Create Configuration File
```bash
sudo nano /etc/supervisor/conf.d/your-laravel-websockets.conf
```

### 3️⃣ Add Configuration
Add the following content to the configuration file:

```ini
[program:laravel-websockets]
process_name=%(program_name)s_%(process_num)02d
command=php /path/to/your/laravel/artisan websocket:init
autostart=true
autorestart=true
user=username
numprocs=1
redirect_stderr=true
stdout_logfile=/path/to/your/laravel/storage/logs/laravel-websockets.log
```

### 4️⃣ Update Supervisor
```bash
sudo supervisorctl reread
```

```bash
sudo supervisorctl update
```

### 5️⃣ Start WebSocket Service
```bash
sudo supervisorctl start laravel-websockets
```

### 6️⃣ Check Status
```bash
sudo supervisorctl status
```

**✅ Expected Output:**
```
laravel-websockets   RUNNING   pid 12345, uptime 0:03:21
```

## 🎉 Final Result

**🔗 Your Socket URL:** `ws://YOUR-SERVER-IP:8090`

## 📝 Important Notes
- Replace `/path/to/your/laravel/` with your actual Laravel project path
- Replace `username` with your server username
- Ensure port 8090 is open in your firewall
- Test the WebSocket connection after setup 