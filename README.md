Design and Deployment of a Virtual Network Architecture Using AWS VPC and Deployment of a Website


 Overview

 
This project documents the end-to-end process of designing a virtual network using AWS VPC, launching and configuring an EC2 instance, and deploying a static website using Nginx. It also covers domain name configuration using GoDaddy, with validation using DNSChecker. SSH access was performed using MobaXterm.



 Objectives

 
Design a custom Virtual Private Cloud (VPC) on AWS.

Launch and configure a web server using Amazon EC2.

Deploy a static HTML website from GitHub.

Map a custom domain name from GoDaddy to the EC2 instance.

Verify propagation and availability using DNSChecker.



 Requirements:
 

 
AWS Account

GoDaddy Domain

MobaXterm (or any SSH client)

Basic knowledge of Git, Linux, and Nginx

GitHub account for website code storage

Static website files (e.g., from HTML/CSS templates)




Steps


1.  Create and Configure VPC on AWS
Create a VPC with CIDR block (e.g., 10.0.0.0/16).

Add subnets (public & private).

Configure route tables and the internet gateway.

Enable auto-assign public IP on the public subnet.

📷Placeholder for VPC Network Diagram


![VPC Architecture](images/vpc-diagram.png)
2. 🚀 Launch an EC2 Instance
Use Ubuntu AMI or Amazon Linux 2.

Select a public subnet, enable auto-assigned public IP.

Create a security group:

Allow HTTP (port 80) and SSH (port 22) from your IP.

Launch and SSH into the instance using MobaXterm.

📷 Placeholder for EC2 Instance Screenshot

markdown
Copy
Edit
![EC2 Instance Setup](images/ec2-setup.png)
3. 🐧 Install Nginx and Git
bash
Copy
Edit
sudo apt update
sudo apt install nginx git -y
Enable Nginx:

bash
Copy
Edit
sudo systemctl enable nginx
sudo systemctl start nginx
4. 📂 Clone and Deploy the Website
Clone your website repo:

bash
Copy
Edit
git clone https://github.com/yourusername/your-repo.git
cd your-repo
sudo cp -r * /var/www/html/
Test locally:

bash
Copy
Edit
curl http://localhost
📷 Placeholder for Website Files in Server

markdown
Copy
Edit
![Website Files](images/files-in-server.png)
5. 🛜 Connect Domain from GoDaddy
Go to GoDaddy DNS settings.

Edit the A Record:

Host: @

Points to: Your EC2 IP (e.g., 54.xx.xx.xx)

TTL: Default (600 seconds or 1 hour)

📷 Placeholder for GoDaddy DNS Setup

markdown
Copy
Edit
![GoDaddy DNS Settings](images/godaddy-dns.png)
6. 🌐 Verify with DNSChecker
Visit dnschecker.org

Enter your domain name and select A Record.

Ensure IP propagation is complete globally.

📷 Placeholder for DNS Checker Result

markdown
Copy
Edit
![DNS Propagation](images/dnschecker.png)
7. ✅ Access Website Online
Open a browser and navigate to your domain:
http://yourdomain.com

📷 Placeholder for Final Website Preview

markdown
Copy
Edit
![Live Website](images/live-site.png)
📎 Tools Used
Tool	Purpose
AWS VPC	Virtual network infrastructure
EC2	Hosting the web server
Nginx	Web server software
GitHub	Source code repository
GoDaddy	Domain name provider
MobaXterm	SSH client to access EC2
DNSChecker	Verify domain propagation

📁 Folder Structure (Example)
css
Copy
Edit
mediplus/
├── index.html
├── style.css
├── img/
├── js/
├── fonts/
├── contact.html
└── ...
