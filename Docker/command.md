docker version
docker info
docker run -r -p 8800:80 httpd

An image is the app we want to run
A container is an instance of that image running as a proc
registry--->default image

docker container run --publish 80:80 nginx

1. Downloaded image nginx from docker hub
2. Start a new container from that image
3. Opened port 80 on the host IP
4. routes that triffic

docker container run --publish 80:80 --detach nginx
docker container ls
docker container stop b50

docker container run --publish 80:80 --detach --name webhost nginx
docker container rm 599 4a5 1c0 b50

### What happens in docker container run

1. looks for that image locally in image cache
2. then looks in remote image repo
3. Downl latest version
4. Creates new container based on that image and prepares to start
5. Gives it a virtual IP on a private network inside docker engine
6. opens up ports 80 on host and forwards to port 80 in container
7. start the image

px aux : show me all the running proc
docker run --name mongo --d mongo

docker container run -d -p 3306:3306 --name db --e MYSQL_RANDOM_ROOT_PASSWORD=yes mysql\\

docker ps -a all image
docker container ls

docker container run -it --name proxys nginx bash
ls -al
exit

docker container run -it --name ubuntu ubuntu
apt-get update
apt-get install -y curl
exit
docker container ls -a

3/26
docker container run -p 80:80 --name webhost -d nginx
-p publish to which port in format HOST:CONTAINER
C:\Users\Yueqi\Desktop\SRE\SRE\Docker>docker container port webhosta
80/tcp -> 0.0.0.0:80

docker network ls
docker network inspect
docker network create --driver
docker network connect

🧾 Assignment Overview
Since Docker Engine v1.11, containers on the same custom network can share a DNS alias and respond to the same name. This enables service discovery and basic load balancing.

🔧 Steps to Complete the Task
Create a Docker virtual network

bash
docker network create elastic-net
Run two containers from the elasticsearch:2 image, giving both the same DNS alias:

bash
docker run -d --name es1 --network elastic-net --network-alias search elasticsearch:2
docker run -d --name es2 --network elastic-net --network-alias search elasticsearch:2
Verify alias resolution using Alpine + nslookup:

bash
docker run --rm --network elastic-net alpine nslookup search
This should show two IPs (for es1 and es2) under the alias search.

Test access to the alias with CentOS + curl:

docker run -it --rm --network elastic-net centos:7
Inside the container:

bash
yum install -y curl
curl http://search:9200
🧠 Key Concepts
--network: attaches container to a specific Docker network
--network-alias: gives container an alternate DNS name in the network
--rm: automatically removes container after it exits
nslookup: used to check DNS resolution
Docker uses embedded DNS for containers on user-defined bridge networks
✅ Expected Result
You should see:

nslookup shows two IPs for the alias search
curl connects to both containers when repeated
