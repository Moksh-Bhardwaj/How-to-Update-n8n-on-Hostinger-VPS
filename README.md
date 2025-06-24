# How to Safely Update n8n on Hostinger or Any VPS
In this GitHub repo, I'll show you step by step how to update your n8n when you're self-hosting it on the cloud or on a VPS like Hostinger. 

## How to update n8n on hostinger or VPS

![Hostinger hpanel screenshot](https://github.com/user-attachments/assets/5f375f2e-368b-4ace-9344-8a6cc5bc7ebc)

### 1) Access your Hostinger VPS or VPS via Terminal
![Access Terminal via VPS screenshot](https://github.com/user-attachments/assets/4bafb591-0e21-4138-8c31-a42eab20656a)

### 2) First let's clear the screen (this step is optional)
```
clear
```

### 3) Install Docker using the Official Installations Script
```
curl -fsSL https://get.docker.com | sh
```

### 4) Enable Docker to start immediately and on System Reboot
```
systemctl enable --now docker
```

### 5) Download the latest n8n Docker Image
```
docker compose pull n8n
```

### 6) Safely Stop and Remove the existing n8n Container 
```
docker compose down
```

### 7) Deploy n8n using the newly pulled Image
```
docker compose up -d
```

### 8) Confirm n8n is running successfully
```
docker compose ps
```

### 9) Check n8n version
```
docker exec -it root-n8n-1 n8n-v
```
