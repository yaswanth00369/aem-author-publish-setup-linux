# 🧱 AEM (Adobe Experience Manager) Author & Publish Setup on Ubuntu EC2

This guide outlines how to configure and run both **AEM Author** and **AEM Publish** instances on a single Ubuntu-based EC2 instance. It includes system requirements, installation steps, file structure, and service configuration.

---

## 📦 System Requirements

- **EC2 Instance**: Ubuntu 20.04 or later  
- **Instance Type**: `t2.medium` (2 vCPUs, 4 GB RAM)  
- **Java**: OpenJDK 11  
- **Storage**: 20 GB minimum recommended  
- **Network**: Inbound access to ports `4502`, `4503`, and `22` (SSH)

---

## ☕ Install Java 11

Run the following commands to install Java 11:

```bash
sudo apt update
sudo apt install openjdk-11-jdk -y

```

## ✅ Check Java Version

```bash
java -version
```


## 📁 Directory Structure for AEM

Organize AEM files as follows:

### 📂 Author Instance
```
/opt/aem/author/
├── aem-author.jar
└── license.properties
```

### 📂 Publish Instance
```
/opt/aem/publish/
├── aem-publish.jar
└── license.properties
```

> 💡 Get these `.jar` and `.properties` files from your IT/Adobe team.

## 📁 Directory Structure for Systemd Service Files

Organize systemd service files as follows:

### 📂 For both Author and Publish
```
/etc/systemd/system/
├── aem-author.service
├── aem-publish.service
```

## 🚀 Start AEM Instances (First-Time Setup)

### Start the Author instance on port `4502`:
```bash
cd /opt/aem/author
java -Xmx1024m -Dsling.run.modes=author -jar aem-author.jar -p 4502
```

### Start the Publish instance on port `4503`:
```bash
cd /opt/aem/publish
java -Xmx1024m -Dsling.run.modes=publish -jar aem-publish.jar -p 4503
```

👉 During the first startup, follow the prompt to set the **admin password**.

---

## 🔧 Enable and Control systemd Services

### Reload systemd to apply changes:
```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
```

### Enable services at boot:
```bash
sudo systemctl enable aem-author.service
sudo systemctl enable aem-publish.service
```

### Start services:
```bash
sudo systemctl start aem-author.service
sudo systemctl start aem-publish.service
```

### Check status:
```bash
sudo systemctl status aem-author.service
sudo systemctl status aem-publish.service
```

### Stop services:
```bash
sudo systemctl stop aem-author.service
sudo systemctl stop aem-publish.service
```




