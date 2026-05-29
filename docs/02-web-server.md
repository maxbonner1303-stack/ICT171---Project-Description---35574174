# Web Server Setup

## Install Nginx
\```
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
\```

## Configure Nginx
Edit the default config:
\```
sudo nano /etc/nginx/sites-available/default
\```

Verify config and restart:
\```
sudo nginx -t
sudo systemctl restart nginx
\```

## File Location
Website files are served from:
\```
/var/www/html/
\```
