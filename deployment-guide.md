# Complete Deployment Guide

## Step 1: Create EC2 Server

1. Open AWS Console
2. Search EC2
3. Click Launch Instance
4. Name: internee-cloud-task
5. Select Ubuntu
6. Select t2.micro or t3.micro
7. Create/download key pair
8. Allow:
   - SSH 22
   - HTTP 80
   - HTTPS 443
9. Launch instance

## Step 2: Connect to Server

```bash
chmod 400 your-key.pem
ssh -i your-key.pem ubuntu@your-ec2-public-ip
```

## Step 3: Install Server Packages

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install nginx git unzip curl -y
sudo systemctl enable nginx
sudo systemctl start nginx
```

## Step 4: Deploy Website

Upload or clone this repository on the server.

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
sudo rm -rf /var/www/html/*
sudo cp -r index.html style.css script.js /var/www/html/
sudo systemctl reload nginx
```

Now open:

```text
http://your-ec2-public-ip
```

## Step 5: Add Domain

In your domain DNS, add an A record:

```text
Type: A
Name: @ or subdomain
Value: EC2 Public IP
```

Example:

```text
task.yourdomain.com → EC2 Public IP
```

## Step 6: Enable SSL

```bash
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d yourdomain.com
```

For subdomain:

```bash
sudo certbot --nginx -d task.yourdomain.com
```

## Step 7: Test SSL Renewal

```bash
sudo certbot renew --dry-run
```

## Final Submission

Submit:

- LinkedIn Post URL
- GitHub Repository Link
- Live Deployment URL
