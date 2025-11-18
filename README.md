# Docker-project-install
This is my process installing docker to my debian vm


Step 1:

updated my vm in the terminal using
sudo apt update
sudo apt upgrade -y

Step 2:

install all the prerequisites for this
sudo apt install -y ca-certificates curl gnupg lsb-release

Step 3:

added dockers gpg key 
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

Step 4:

added a docker repository
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/debian trixie stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Step 5:

installed the docker engine and the compose plugin
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin

Step 6: 

verified the installation 
docker --version
docker compose version
sudo docker run hello-world


Step 7:

created a repository for the kuma-uptime application
mkdir uptime-kuma && cd uptime-kuma

Step 8:

created a docker yml file and added some cod into it
sudo nano docker_compose.yml

services:
  
  uptime-kuma:
   
    image: louislam/uptime-kuma:latest
    
    container_name: uptime-kuma
    
    volumes:
    
      - ./data:/app/data
    
    ports:
    
      - "3001:3001"
    
    restart: always


Step 9:

started the application
sudo docker compose up -d

Step 10:

verified the container
sudo docker ps

Step 11:

Access web inter face in an open browser
http://<VM_IP>:3001
