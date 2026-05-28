# VM Setup

## Provider
Microsoft Azure

## VM Specifications
- OS: Ubuntu Linux LTS
- Size: Standard D2s v3
- Region: Australia East (Zone 1)

## Steps
Create the VM in the Azure portal with the following settings...

Connect via SSH:
\```
ssh azureuser@your-ip-address
\```

Update the system:
\```
sudo apt update && sudo apt upgrade -y
\```
