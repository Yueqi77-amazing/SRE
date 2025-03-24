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
