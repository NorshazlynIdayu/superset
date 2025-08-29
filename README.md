# Apache Superset Setup with Docker on Windows

This guide explains how to set up **Apache Superset** using **Docker Compose** on Windows, including initialization and troubleshooting common issues.

---

## Prerequisites

1. **Windows 10/11**
2. **Docker Desktop** with **WSL2 backend** enabled
3. **VS Code** (optional, for editing files)
4. Basic knowledge of PowerShell

---

## 1️⃣ Clone Superset repository

Open PowerShell and run:

```powershell
cd C:\Users\yourname
git clone https://github.com/apache/superset.git
cd superset
```

## 2️⃣ Replace this 3 file with files below
1. superset.conf.template
2. docker-compose.yml
3. superset_config.py

## 3️⃣ Launch Superset Through Docker Compose
1. docker compose up -d --build
2. docker compose logs -f superset_app
Look for: * Running on http://0.0.0.0:8088/ if there proceed to next step
3. docker compose exec superset superset db upgrade
4. docker compose exec superset superset fab create-admin --username admin --password admin --email admin@example.com --firstname Admin --lastname User
IF IT SAY ALREADY EXIST, PROCEED TO NEXT STEP
5.docker compose exec superset superset init

## 5️⃣ Check Nginx
If superset_app is running and listening on 8088 internally, Nginx should proxy correctly.
Open browser at http://localhost:9090 
<img width="1919" height="910" alt="image" src="https://github.com/user-attachments/assets/6dc92c13-9b8f-44dd-9458-48414aa1d557" />
If this appears, you have successfully set up Superset. Hooray!🎉🎉

---

