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
This will give the virtual machine access to the website.

\```
ssh azureuser@20.211.147.206
\```

Update the system:
This will update the virtual machine with all the latest updates.

\```
sudo apt update && sudo apt upgrade -y
\```
