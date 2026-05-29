# Domain & DNS

## Registrar
Namecheap — https://www.namecheap.com

## Domain
subtrackr.online

## DNS Configuration
Configured an A record in Namecheap to point the domain to the AWS EC2 Elastic IP:

- Log into Namecheap → Domain List → Manage → Advanced DNS
- Add the following records:

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A Record | @ | 13.54.175.127 | Automatic |
| A Record | www | 13.54.175.127 | Automatic |

## Verify DNS Propagation
Check that the domain resolves to the correct IP:
```bash
nslookup subtrackr.online
```

Expected output should show `13.54.175.127` as the address.

## Result
Site is accessible at:
- http://subtrackr.online
- http://www.subtrackr.online
