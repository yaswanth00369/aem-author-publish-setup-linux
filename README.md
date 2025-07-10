# AEM Author-Publish Setup on Linux (Ubuntu 24.04)

This repository documents the setup and configuration of Adobe Experience Manager (AEM) Author and Publish instances on a single Ubuntu Linux server with systemd service files.

## 🔧 What’s Included

- AEM Author and Publish instance setup using `.jar` files
- Port configuration (Author on 4502, Publish on 4503)
- Systemd service files to manage AEM as services
- Java configuration and memory tuning
- Basic content page with a “Related Posts” section using We.Retail
- Best practices and troubleshooting notes

## 🧱 Tech Stack

- AEM 6.x (JAR + License file)
- Java 11 (OpenJDK)
- Ubuntu 20.04+ (tested on EC2 t2.medium)
- Systemd for process management

## 📁 Folder Structure

/opt/aem/
├── author/
│ └── aem-author.jar
├── publish/
│ └── aem-publish.jar


/etc/systemd/system/
├── aem-author.service
├── aem-publish.service
