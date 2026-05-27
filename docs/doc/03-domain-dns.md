# Domain & DNS

## Registrar
(e.g. Namecheap, GoDaddy, Cloudflare)

## DNS Configuration
Added an A record pointing to the Azure VM public IP:

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A | @ | xxx.xxx.xxx.xxx | Auto |
| A | www | xxx.xxx.xxx.xxx | Auto |

DNS propagation was verified using:
\```
nslookup yourdomain.com
\```
