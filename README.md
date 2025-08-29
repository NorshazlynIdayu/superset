# Apache Superset Setup with Docker on Windows

This guide explains how to set up **Apache Superset** using **Docker Compose** on Windows, including initialization and troubleshooting common issues.

---

# Prerequisites

1. **Windows 10/11**
2. **Docker Desktop** with **WSL2 backend** enabled
3. **VS Code** (optional, for editing files)
4. Basic knowledge of PowerShell

---
# Guide to Setting Up Superset
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

## 4️⃣ Check Nginx
If superset_app is running and listening on 8088 internally, Nginx should proxy correctly.
Open browser at http://localhost:9090 
<img width="1919" height="910" alt="image" src="https://github.com/user-attachments/assets/6dc92c13-9b8f-44dd-9458-48414aa1d557" />
If this appears, you have successfully set up Superset. Hooray!🎉🎉

---
# Superset Database & Dataset Connection

## 1️⃣ Open http://localhost:9090  and login with username: admin password: admin
## 2️⃣ Setup Database Connection
i) Go to Setting > Database Connection > +Database > Choose PostgresSQL > and fill the form 
<img width="623" height="872" alt="image" src="https://github.com/user-attachments/assets/94c4130d-f929-4863-bf37-7f0eec9ca7b2" />
ii) Click Advanced > Performance > set all as -1 >  Finish
<img width="610" height="502" alt="image" src="https://github.com/user-attachments/assets/60bc724d-7eab-4d77-9788-758aa406e6b8" />
iii) Go to Dataset > +Dataset > choose as inn image > Create
<img width="386" height="322" alt="image" src="https://github.com/user-attachments/assets/b719d850-f4d3-4dc1-8140-c33a8c6d5edf" />
REPEAT THIS STEP FOR : 	sites_in_viewport & rsrp_in_viewport

---
# Creating Charts and Dashboards
## 1️⃣ Go to Charts > +Chart > dataset : rsrp_in_viewport chart type: Histogram > Create
<img width="1915" height="903" alt="image" src="https://github.com/user-attachments/assets/7675ec5a-b994-4823-82d3-a5a68eadc4b5" />
## 2️⃣ Create the chart > Save
<img width="1919" height="904" alt="image" src="https://github.com/user-attachments/assets/63a77345-9324-499b-a6c6-f58b682085a5" />

# Connect chart to teria
## 1️⃣ Open the chart that has been created, e.g., RSRP.
## 2️⃣ Go to 3 dot > Share > Embed code
<img width="664" height="467" alt="image" src="https://github.com/user-attachments/assets/ae26348d-7cf3-43a1-aea4-89ae8c29c4a2" />
## 3️⃣ Copy url that like this: src="http://localhost:9090/superset/explore/p/MJ87nLb2GEq/?standalone=1&height=400"
## 4️⃣ In terria open map.html and find rsrp. change the src to url that you copy from superset.
## 5️⃣ REPEAT ALL THIS FOR CREATING UPLOAD AND DOWNLOAD. COMPLAINTS AND SITE WITH SAME STEP JUST CHANGE THE CHART TYPE TO BIG NUMBER







