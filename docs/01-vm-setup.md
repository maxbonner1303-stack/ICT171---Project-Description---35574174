# VM Setup

## Provider
Amazon Web Services (AWS) EC2

## VM Specifications
- OS: Ubuntu 24.04 LTS
- Instance Type: m4.4xlarge
- Region: Asia Pacific (Sydney) ap-southeast-2

## Steps

### 1. Launch EC2 Instance
- Log into AWS Console at https://aws.amazon.com
- Navigate to EC2 → Instances → Launch Instance
- Selected Ubuntu 24.04 LTS as the OS
- Created a new key pair named `KeyKeyPairPair` and downloaded the `.pem` file
- Configured Security Group to allow inbound traffic on port 80 (HTTP), 443 (HTTPS), and 22 (SSH)
- Launched the instance

### 2. Allocate Elastic IP
Assigned a static Elastic IP to ensure the server address does not change between restarts:
- Navigate to EC2 → Elastic IPs → Allocate Elastic IP
- Associate the Elastic IP with the running instance

### 3. Connect via SSH
```bash
ssh -i "KeyKeyPairPair.pem" ubuntu@13.54.175.127
```

### 4. Update the System
```bash
sudo apt update && sudo apt upgrade -y
```
