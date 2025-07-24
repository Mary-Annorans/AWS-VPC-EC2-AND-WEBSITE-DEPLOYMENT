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




<img width="2560" height="1344" alt="VPC_image" src="https://github.com/user-attachments/assets/4c32d1f7-1209-4b1a-8cdf-4177e57aa6bd" />




2.  Launch an EC2 Instance
Use Ubuntu AMI or Amazon Linux 2.

Select a public subnet, enable auto-assigned public IP.

Create a security group:

Allow HTTP (port 80) and SSH (port 22) from your IP.

Launch and SSH into the instance using MobaXterm.


<img width="2560" height="1440" alt="ec2 instance" src="https://github.com/user-attachments/assets/6fa841c7-b316-43d5-903c-7e2522ae3e72" />


3.  Install Nginx and Git

sudo apt update
sudo apt install nginx git -y
Enable Nginx:


sudo systemctl enable nginx
sudo systemctl start nginx
<img width="2560" height="1344" alt="terminal2" src="https://github.com/user-attachments/assets/b2f805a2-a4b7-40b4-89d5-6789807ab481" />

<img width="2560" height="1344" alt="terminal 1" src="https://github.com/user-attachments/assets/12b0165f-807e-478e-af55-d9a8e52486be" />



4.  Clone and Deploy the Website
Clone your website repo:

git clone  https://github.com/Mary-Annorans/realestate-portal1.git


cd realestate-portal1

sudo cp -r * /var/www/html/


Test locally:


curl http://localhost



<img width="1920" height="1032" alt="ip-url" src="https://github.com/user-attachments/assets/1d9e1d03-9ba5-42ac-a167-b1d758bbbcd7" />

5.  Connect Domain from GoDaddy


Go to GoDaddy DNS settings.


Edit the A Record:

Host: @

Points to: Your EC2 IP (e.g., 54.xx.xx.xx)

TTL: Default (600 seconds or 1 hour)




6.  Verify with DNSChecker
Visit dnschecker.org

Enter your domain name and select A Record.

Ensure IP propagation is complete globally.

<img width="1920" height="1032" alt="dnschecker" src="https://github.com/user-attachments/assets/d57ebb6b-0832-43e7-8edf-72ed6836a841" />



7.  Access Website Online
   
Open a browser and navigate to your domain:

http://basmarbies.com




<img width="1920" height="1032" alt="basmarbies" src="https://github.com/user-attachments/assets/ab68aa64-a25e-440a-b0ea-7402b41498e0" />


 Tools Used

 
Tool	Purpose


AWS VPC	Virtual network infrastructure


EC2	Hosting the web server


Nginx	Web server software


GitHub	Source code repository


GoDaddy	Domain name provider


MobaXterm	SSH client to access EC2


DNSChecker	Verify domain propagation

 
