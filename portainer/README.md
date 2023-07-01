# installing and configuring portainer on a Linux (Ubuntu) server

## REQUIREMENTS

## bring system up to date
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` 
## make sure that old versions of docker are removed
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```
## be able to install packages over https
```
sudo apt-get install ca-certificates curl gnupg lsb-release
```
# installing docker on ubuntu
## add official GPG key from docker
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
``` 
## configure the docker repository
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
## update newly created package list and install docker engine & containerd 
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
## check installation
```
sudo docker version
sudo docker info
```
## create a dummy container
``` 	
sudo docker run hello-world
```
# installing portainer on ubuntu

## create volume for portainer
```
sudo docker volume create portainer_data
``` 
## define parameters, outgoing ports, names of the container and volumes
```
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
``` 
## accessible via the browser
```
http://IP_ADRESSE:9000/
```
