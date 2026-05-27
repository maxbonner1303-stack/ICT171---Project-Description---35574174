# SSL/TLS Setup

## Tool Used
Let's Encrypt via Certbot

## Installation
\```
sudo apt install certbot python3-certbot-nginx -y
\```

## Certificate Generation
\```
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
\```

## Auto-Renewal Test
\```
sudo certbot renew --dry-run
\```

## Azure Port 443
Opened inbound port 443 in Azure VM Networking settings.

Site is now accessible at https://yourdomain.com
