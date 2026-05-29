# Web Server Setup

## Install Nginx
Update package list and install Nginx:
```bash
sudo apt update
sudo apt install nginx -y
```

Enable Nginx to start automatically on reboot:
```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

Verify Nginx is running:
```bash
sudo systemctl status nginx
```

## Configure AWS Security Group
To allow web traffic, the following inbound rules were added in AWS EC2 → Security Groups:

| Port | Protocol | Source | Purpose |
|------|----------|--------|---------|
| 22 | TCP | My IP | SSH access |
| 80 | TCP | 0.0.0.0/0 | HTTP traffic |
| 443 | TCP | 0.0.0.0/0 | HTTPS traffic |

## Deploy Website Files
Website files are served from `/var/www/html/`. The `index.html` file was copied 
from a local machine to the server using `scp`:

```bash
scp -i "KeyKeyPairPair.pem" "index.html" ubuntu@13.54.175.127:/var/www/html/index.html
```

## Verify
Visit http://13.54.175.127 in a browser to confirm the site is live.
