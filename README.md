# Internee.pk Cloud Deployment Task

This project was created for the Internee.pk internship task:

**Deploy the Internee.pk Website on a Cloud Server**

## Objective

Deploy a website on a cloud-based virtual machine using:

- AWS EC2
- Ubuntu Linux
- Nginx Web Server
- Let’s Encrypt SSL
- HTTPS

## Project Overview

This is a sample Internee.pk cloud deployment landing page. The main purpose of this project is to demonstrate cloud server deployment, Linux server configuration, Nginx setup, and SSL certificate installation.

## Deployment Architecture

```text
User Browser
    ↓
Domain / Public IP
    ↓
AWS EC2 Ubuntu Server
    ↓
Nginx Web Server
    ↓
Website Files
```

## Technologies Used

- HTML
- CSS
- JavaScript
- AWS EC2
- Ubuntu
- Nginx
- Let’s Encrypt SSL

## Deployment Steps

### 1. Launch AWS EC2 Instance

- AMI: Ubuntu
- Instance Type: t2.micro or t3.micro
- Security Group Rules:
  - SSH: Port 22
  - HTTP: Port 80
  - HTTPS: Port 443

### 2. Connect to Server

```bash
ssh -i your-key.pem ubuntu@your-ec2-public-ip
```

### 3. Install Nginx

```bash
sudo apt update
sudo apt install nginx git unzip -y
sudo systemctl enable nginx
sudo systemctl start nginx
```

### 4. Upload Website Files

```bash
sudo rm -rf /var/www/html/*
sudo cp -r * /var/www/html/
```

### 5. Configure Nginx

```bash
sudo nginx -t
sudo systemctl reload nginx
```

### 6. Install SSL Certificate

```bash
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx
```

## Live Deployment

Live URL: https://13-221-180-156.sslip.io

## Author

**Shehroz Amjad**

- LinkedIn: https://www.linkedin.com/in/shehrozamjad
- GitHub: https://github.com/Shehroz33
