# SSL/TLS Setup

## Tool Used
Let's Encrypt via Certbot

## Installation
Update package list and install Certbot with the Nginx plugin:
```bash
sudo apt update
sudo apt install certbot python3-certbot-nginx -y
```

## Certificate Generation
Run Certbot against your domain:
```bash
sudo certbot --nginx -d subtrackr.online -d www.subtrackr.online
```
Follow the prompts — enter your email and agree to the terms of service.
Certbot will automatically modify your Nginx config to enable HTTPS.

## Auto-Renewal Test
Verify that the auto-renewal process works:
```bash
sudo certbot renew --dry-run
```

## AWS Port 443
Opened inbound port 443 (HTTPS) in AWS EC2 Security Group inbound rules,
source set to Anywhere (0.0.0.0/0) to allow all users to access the site over HTTPS.

## Result
Site is now accessible at https://subtrackr.online
