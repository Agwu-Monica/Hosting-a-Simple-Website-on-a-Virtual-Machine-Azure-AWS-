# Hosting-a-Simple-Website-on-a-Virtual-Machine-Azure/AW

Hosting a Simple Website on a Virtual Machine (Azure / AWS)
📌 Project Overview

This project demonstrates how to deploy and host a static website on a cloud-based Virtual Machine using Microsoft Azure (or AWS).

The process includes provisioning infrastructure, configuring networking, installing a web server (Nginx), deploying a website template, and mapping a domain using DNS.

🧰 Technologies Used
Microsoft Azure
Ubuntu Linux
Nginx
SSH
Azure VNET & Subnet
Network Security Group (NSG)
CIDR
MobaXterm / PowerShell
VS Code
Namecheap (DNS Management)
DNS Checker
🎯 Objectives
Provision a Virtual Machine in the cloud
Configure secure network access (SSH & HTTP)
Install and configure Nginx web server
Deploy a static website template
Map domain name to server IP
Validate global DNS propagation
🏗️ Architecture Flow
User Browser → Domain (Namecheap DNS) → Public IP → VM (Azure/AWS) → Nginx → Website Files
⚙️ Step 1: Network Configuration
1. Create Virtual Network (VNET)
Define IP range using CIDR
Example: 10.0.0.0/16
2. Create Subnet
Example: 10.0.1.0/24
3. Configure Network Security Group (NSG)

Allow inbound traffic:

SSH (22) → Remote access
HTTP (80) → Web traffic
🖥️ Step 2: Deploy Virtual Machine
Navigate to Azure Portal → Virtual Machines → Create
Configure:
Resource Group
VM Name
Region
OS: Ubuntu Linux
Size (Free tier or small instance)
Authentication:
Username + Password (or SSH key)
Networking:
Attach VNET & Subnet
Assign Public IP
Attach NSG
Open ports:
SSH (22)
HTTP (80)
Review and Create VM
🔐 Step 3: Connect to Virtual Machine
Option 1: PowerShell (SSH)
ssh username@public-ip
Option 2: MobaXterm
Host: Public IP
Username
Port: 22
🔧 Step 4: Server Configuration
Update and Upgrade System
sudo apt update
sudo apt upgrade -y
Install Nginx
sudo apt install nginx -y
Verify Nginx Status
sudo systemctl status nginx
🌐 Step 5: Verify Default Web Server

Open browser:

http://<public-ip>

You should see the default Nginx welcome page.

🎨 Step 6: Prepare Website Template
Download a template (e.g., from ThemeWagon)
Extract files locally
Edit using VS Code:
Modify HTML
Replace images/assets
Test locally via browser
📤 Step 7: Upload Website to Server
Upload via MobaXterm
Drag & drop zipped project folder
On Server:
ls
sudo apt install unzip -y
unzip <file-name>.zip
📂 Step 8: Deploy Website Files
Copy files to Nginx directory:
sudo cp -r <folder-name>/* /var/www/html/
Remove default Nginx page:
sudo rm /var/www/html/index.nginx-debian.html
Verify files:
cd /var/www/html
ls
🌍 Step 9: Access Live Website

Open:

http://<public-ip>

Your website should now be live.

🌐 Step 10: Configure Domain (Namecheap)
Login to Namecheap
Go to Domain → Manage → Advanced DNS
Add Record:
Type	Host	Value
A Record	@	Public IP
Save changes
🔎 Step 11: Verify DNS Propagation

Use DNS Checker to confirm global propagation.

✅ Step 12: Final Testing
Access via:
Public IP
Domain name

Ensure:

Website loads correctly
Assets display properly
🧹 Step 13: Cleanup (Cost Optimization)

To avoid charges:

Delete Virtual Machine
Delete associated resources:
Public IP
NIC
Disk
📦 Project Outcome

By completing this project, you have:

Built and configured a cloud-based VM
Implemented networking (VNET, Subnet, NSG)
Deployed a production-like web server
Hosted a live website
Configured DNS for domain access
💡 Key Learnings
Infrastructure provisioning in Azure
Linux server administration
Web server configuration (Nginx)
File transfer and deployment
DNS management and propagation






## Notion Link
https://swamp-diadem-74c.notion.site/Hosting-a-simple-website-in-Virtual-Machine-Azure-or-AWS-2ff5e80cc23580b5b66fdcf946fdab53?source=copy_link
