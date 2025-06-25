# How to Safely Update n8n on Hostinger VPS

This guide will walk you step-by-step through updating your existing **n8n** instance on a Hostinger VPS (pre-installed with Docker and Docker Compose) - **without losing any of your workflows, credentials, or data**.

> ✅ **Important:** Hostinger’s n8n VPS already uses persistent volumes, so this update process is safe and non-destructive.

![Hostinger hpanel screenshot](https://github.com/user-attachments/assets/5f375f2e-368b-4ace-9344-8a6cc5bc7ebc)

---
### 1️⃣ Access Your Hostinger VPS via Terminal
![Access Terminal via VPS screenshot](https://github.com/user-attachments/assets/4bafb591-0e21-4138-8c31-a42eab20656a)

### 2️⃣ (Optional) Clear Terminal

This just clears the screen for better visibility.
```
clear
```

### 3️⃣ Pull the Latest n8n Docker Image

This will download the latest version of n8n without affecting your data.
```
docker compose pull n8n
```
> ⚠️ Make sure you’re in the directory containing your `docker-compose.yml`. Which you can verify simply my entering `ls` in terminal.

### 4️⃣ Stop the Currently Running n8n Container

This stops the old container (**but does not remove your workflows**, because data is already persisted in Hostinger n8n VPS).
```
docker compose down
```

### 5️⃣ Start n8n Using the Updated Image

This restarts n8n with the latest version.
```
docker compose up -d
```

### 6️⃣ Confirm n8n is running successfully
```
docker compose ps
```

### 7️⃣ Confirm the Updated Version
```
docker exec -it root-n8n-1 n8n -v
```
> Replace n8n with your container name if it's different. Use 'docker ps' to check.

---
## 🔒 Data Persistence (Why Your Workflows Are Safe)

Hostinger’s Docker setup includes a persistent volume like:

```
volumes:
  - ~/.n8n:/home/node/.n8n
```

This ensures:

* ✅ Workflows
* ✅ Credentials
* ✅ Execution history
  ...all remain safe even when containers are stopped or updated.

---
## ✅ That’s It!

Your n8n instance is now successfully updated on Hostinger — with **no data lost** and **everything working on the latest version**.

### Support me if my videos or projects helped you:
<a href="https://github.com/sponsors/Moksh-Bhardwaj">
  <img src="https://img.shields.io/badge/Sponsor-%E2%9D%A4-lightgrey?logo=github" alt="Sponsor" width="160"/>
</a>

