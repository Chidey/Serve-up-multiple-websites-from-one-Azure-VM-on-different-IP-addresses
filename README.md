# Serve-up-multiple-websites-from-one-Azure-VM-on-different-IP-addresses

## Introduction

This project demonstrates how to configure and host multiple websites on a single Azure virtual machine (VM) while assigning each website a unique public IP address.

## Features

- Multiple Website Hosting: Host several websites using different public IPs.
- Efficient Resource Management: Optimize server utilization without the need for multiple VMs.
- Scalable Solution: Easily add more websites as needed.


## Architecture

- Azure Virtual Machine: The core compute resource hosting the websites.
- Public IP Addresses: Assigned to the Azure VM for different websites.
- Web Server Software: Configured to serve multiple websites.

## Setup Instructions

<b>Step 1: Create an Azure VM </b>

1. Log in to the [Azure Portal](https://portal.azure.com/).
2. Create a Resource group.
<p align="center">
<img src="https://imgur.com/AcAk7eS.png" height="80%" width="80%" alt="Create a Resource group" />
</p>

3. Create public IP address.
<p align="center">
<img src="https://imgur.com/5ZtzT6r.png" height="80%" width="80%" alt="Create a puplic IP address" />
</p>

<p align="center">
<img src="https://imgur.com/e423D0E.png" height="80%" width="80%" alt="Puplic IP address" />
</p>

4. Navigate to Virtual Machines and click + Create.
<p align="center">
<img src="https://imgur.com/rFfW16z.png" height="80%" width="80%" alt="Create a VM" />
</p>

5. Configure the VM:
    -Choose an OS (e.g., Ubuntu or Windows Server).
   -Select a VM size based on your requirements.
    -Set up SSH or RDP for access.
<p align="center">
<img src="https://imgur.com/bQFdMfG.png" height="80%" width="80%" alt="Configure the VM" />
</p>
   
4. Deploy the VM.
<p align="center">
<img src="https://imgur.com/s8GCmnv.png" height="80%" width="80%" alt="Virtual Machine" />
</p>

<b>Step 2: Configure Multiple IP Addresses </b>
1. Navigate to the Networking section of your VM in the Azure Portal.
<p align="center">
<img src="https://imgur.com/DRn3lxz.png" height="80%" width="80%" alt="Navigate to the networking section" />
</p>

2. Under Network Interface, select the NIC associated with your VM.
3. Add additional Public IP Addresses:
      -Click IP Configurations.
   <p align="center">
<img src="https://imgur.com/3wH6eeB.png" height="80%" width="80%" alt="Click IP Configuration" />
</p>

<p align="center">
<img src="https://imgur.com/nN6x66m.png" height="80%" width="80%" alt="IP Configuration" />
</p>
      -Add new IP configurations with unique IP addresses.
<p align="center">
<img src="https://imgur.com/LUYyXRg.png" height="80%" width="80%" alt="IP for the websites" />
</p>

 
5. Save the changes.
<p align="center">
<img src="https://imgur.com/4wVrTY7.png" height="80%" width="80%" alt="IP for the websites" />
</p>
Repeat for the second IP.
  <p align="center">
<img src="https://imgur.com/6DTNpz5.png" height="80%" width="80%" alt="IP for the websites" />
</p>

It should look like this:
<p align="center">
<img src="https://imgur.com/Mha3emp.png" height="80%" width="80%" alt="IP for the websites" />
</p>

<b>Step 3: Install Web Server Software </b>
1. Connect to the VM using SSH or RDP.
2. Install your preferred web server:
Apache (Ubuntu):
bash

sudo apt update
sudo apt install apache2
Nginx (Ubuntu):
bash

sudo apt update
sudo apt install nginx


<b>Step 4: Bind Websites to IP Addresses </b>
1.Configure your web server to bind specific websites to the added IP addresses:

      - For Apache, modify the virtual host files in /etc/apache2/sites-available/.
      
      - For Nginx, update the server block configurations in /etc/nginx/sites-available/.

Example Apache Virtual Host Configuration:

apache
Copy code
<VirtualHost 123.123.123.1:80>
    ServerName www.site1.com
    DocumentRoot /var/www/site1
</VirtualHost>

<VirtualHost 123.123.123.2:80>
    ServerName www.site2.com
    DocumentRoot /var/www/site2
</VirtualHost>

<b>Step 5: Test the Setup </b>
1. Use a web browser or curl to access each website by its domain or IP.
2. Verify that the correct website loads for each IP address.
<p align="center">
<img src="https://imgur.com/9ZyY87e.png" height="80%" width="80%" alt="Website1" />
</p>

<p align="center">
<img src="https://imgur.com/wxTCny3.png" height="80%" width="80%" alt="Website2" />
</p>
