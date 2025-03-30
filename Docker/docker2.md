## What is an image?

1. docker pull nginx:11.1 indicate the version

#### Image Layers

1. docker history nginx:latest
2. docker image inspect

mysql/mysql-server
docker build -t customnginx .

# Container Lifetime and persistent data

VOLUME
用来储存一些数据 尽管 stop/rm container 依然存在的
docker volume create

docker container run -d --name nginx -p 80:80 -v %cd%:/usr/share/nginx/html nginx

docker container run -d --name psql -v ...
docker logs -f psql
Bind Mount（绑定挂载）是指：
把主机上的某个具体目录 映射（绑定）到 容器内部的某个目录。

👉 容器可以实时读取或写入这个主机目录中的文件。
3/29
RUNTIME and BUILDTIME
CMD is runtime : only the last

ENTRYPOINT complements the CMD
EXEC Form and Shell form

3/30
Docker Compose
to condigure relationships bet containers
save our docker container run setting s in easy to read file
create one liner developer env startups

YAML formatted file that describes our solution options for
container network volume

version
services:
volumes:
network:

docker-compose up #setip volumes /networks and start all containers
docker-compose down #stop the containers
