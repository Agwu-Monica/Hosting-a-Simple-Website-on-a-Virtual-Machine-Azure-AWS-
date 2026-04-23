# Hosting-a-Simple-Website-on-a-Virtual-Machine-Azure/AW

Hosting a Simple Website on a Virtual Machine (Azure / AWS)

---------------------------------------------------------------------------------------------

## Project Overview

### This project demonstrates 

How to deploy and host a static website on a cloud-based Virtual Machine using Microsoft Azure 

### The process includes

Provisioning infrastructure

Configuring networking 

Installing a web server (Nginx) 

Deploying a website template  

Mapping a domain using DNS.

-----------------------------------------------------------

## Technologies Used

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

------------------------------------------------------------------------

## Objectives

Provision a Virtual Machine in the cloud

Configure secure network access (SSH & HTTP)

Install and configure Nginx web server

Deploy a static website template

Map domain name to server IP

Validate global DNS propagation

---------------------------------------------------------------------

## Architecture Flow

User Browser → Domain (Namecheap DNS) → Public IP → VM (Azure/AWS) → Nginx → Website Files

### Step 1: Network Configuration

#### 1. Create Virtual Network (VNET)

Define IP range using CIDR

Example: 10.0.0.0/16

#### 2. Create Subnet

Example: 10.0.1.0/24


<img width="983" height="315" alt="image" src="https://github.com/user-attachments/assets/17a733c5-811a-4dbe-a51b-13389f5687f7" />



#### 3. Configure Network Security Group (NSG)

Allow inbound traffic:

SSH (22) → Remote access

HTTP (80) → Web traffic


### Step 2: Deploy Virtual Machine

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


<img width="1338" height="469" alt="image" src="https://github.com/user-attachments/assets/08c8b0ec-22f8-4fc7-9e57-9403452ba359" />



### Step 3: Connect to Virtual Machine

Option 1: PowerShell (SSH)

ssh username@public-ip

Option 2: MobaXterm

Host: Public IP

Username

Port: 22


<img width="829" height="690" alt="image" src="https://github.com/user-attachments/assets/236519a3-d611-4798-aaf3-2feab26baf2c" />



### Step 4: Server Configuration

Update and Upgrade System

sudo apt update

sudo apt upgrade -y

Install Nginx

sudo apt install nginx -y

Verify Nginx Status

sudo systemctl status nginx



<img width="664" height="584" alt="image" src="https://github.com/user-attachments/assets/29e021a6-140d-4a6e-86d2-a8443cfe1464" />



### Step 5: Verify Default Web Server

Open browser:

http://<public-ip>

You should see the default Nginx welcome page.



<img width="926" height="439" alt="image" src="https://github.com/user-attachments/assets/b3c8d128-a89f-47f4-be42-b1f9c5be0ca9" />



### Step 6: Prepare Website Template

Download a template (e.g., from ThemeWagon)

Extract files locally

Edit using VS Code:

Modify HTML

Replace images/assets

Test locally via browser



<img width="1180" height="636" alt="image" src="https://github.com/user-attachments/assets/ae9a1262-222d-425d-87c5-75f743337e74" />



### Step 7: Upload Website to Server

Upload via Vs Code

Drag & drop zipped project folder

On Server:

ls

sudo apt install unzip -y

unzip <file-name>.zip


<img width="1306" height="682" alt="image" src="https://github.com/user-attachments/assets/8e8aa6a9-7e45-43c0-8a88-beb54a43f9a6" />



### Step 8: Deploy Website Files

Copy files to Nginx directory:

sudo cp -r <folder-name>/* /var/www/html/

Remove default Nginx page:

sudo rm /var/www/html/index.nginx-debian.html

Verify files:

cd /var/www/html

ls


### Step 9: Access Live Website

Open:

http://<public-ip>

Your website should now be live.


<img width="1348" height="698" alt="image" src="https://github.com/user-attachments/assets/0600502a-a492-447d-b60e-78cdda93da39" />



<img width="1318" height="669" alt="image" src="https://github.com/user-attachments/assets/9ea78df8-d06a-4658-8715-146259a69c41" />




### Step 10: Configure Domain (Namecheap)

Login to Namecheap

Go to Domain → Manage → Advanced DNS

Add Record:

Type	Host	Value

A Record	@	Public IP

Save changes


<img width="1320" height="332" alt="image" src="https://github.com/user-attachments/assets/2ab4af3d-abf9-4602-a1b9-a9f96c8f461d" />



### Step 11: Verify DNS Propagation

Use DNS Checker to confirm global propagation.


<img width="1361" height="597" alt="image" src="https://github.com/user-attachments/assets/b55fc746-87fb-4738-9feb-e369c75861e8" />



### Step 12: Final Testing

Access via:

Public IP

Domain name

Ensure:

Website loads correctly

Assets display properly


<img width="1311" height="680" alt="image" src="https://github.com/user-attachments/assets/7f37a9c3-9e14-43bf-9b67-188376bf9f8d" />




### Step 13: Cleanup (Cost Optimization)

To avoid charges:

Delete Virtual Machine

Delete associated resources:

Public IP

NIC

Disk

--------------------------------------------------------------------------

## Project Outcome

By completing this project, you have:

Built and configured a cloud-based VM

Implemented networking (VNET, Subnet, NSG)

Deployed a production-like web server

Hosted a live website

Configured DNS for domain access

-------------------------------------------------------------------------------------------------

## Key Learnings

Infrastructure provisioning in Azure

Linux server administration

Web server configuration (Nginx)

File transfer and deployment

DNS management and propagation

--------------------------------------------------------------------------------------------

## Notion Link
https://swamp-diadem-74c.notion.site/Hosting-a-simple-website-in-Virtual-Machine-Azure-or-AWS-2ff5e80cc23580b5b66fdcf946fdab53?source=copy_link

---------------------------------------------------------------------------------------

## Author

Momica Agwu

Cloud Engineering and DevOps

https://www.linkedin.com/in/agwumonica/
