# Demo: Install PowerShell Core on Ubunto WSL

### Prerequistes:
  * Install Windows Subsystem for Linux (WSL) on Windows 10 and Ubuntu Linux distribution. Instructions available [here](./../Lab-Setup.md)
  

### How to install PowerShell Core on Ubuntu WSL
 
```powershell
# Start WSL
wsl

# Switch user to root user (Superuser)
sudo su -

# Import the Microsoft public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Check your Ubuntu distribution version
lsb_release -a

# Register the Microsoft Ubuntu repository, change the <version> to the corresponding version of the installed Ubuntu
# Example: curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/<version>/prod.list
 
# Update the list of products
apt-get update
 
# Install PowerShell
apt-get install -y powershell

# Exit Superuser
exit
 
# Start PowerShell
pwsh

# Lest test :) 

Get-Module

Get-Command

Get-ComputerInfo

Get-Service

# Why Get-ComputerInfo and Get-Services doesn't work?
```
