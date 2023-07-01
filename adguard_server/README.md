# installing and configuring AdGuard on a Linux (Ubuntu) server

## bring system up to date
```
sudo apt-get update && sudo apt-get upgrade -y
``` 
## easy way to install AdGuard Home automatically using the following script
```
sudo apt install curl
curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
```
## To start or stop the AdGuard Home service, Change to the Home directory of the AdGuard service
```
cd /opt/AdGuardHome/
```
# Then run the following commands to manage the service

### Start AdGuard Home service 
sudo ./AdGuardHome -s start

### Stop AdGuard Home service 
sudo ./AdGuardHome -s stop

### Restart AdGuard Home service 
sudo ./AdGuardHome -s restart

### Install AdGuard Home service. This registers it as a service#
sudo ./AdGuardHome -s install

### Uninstall AdGuard Home service 
sudo ./AdGuardHome -s uninstall

## To check the status of the service
```
sudo ./AdGuardHome -s status
``` 
## AdGuard Home service updates automatically when a new version is released by showing a notification message and the “Update Now” button on the interface. You can also do it on the terminal by running the following command
```
sudo ./AdGuardHome --update
```
## accessible via the browser
```
http://<localhost/IP address>:3000
```
