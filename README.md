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

