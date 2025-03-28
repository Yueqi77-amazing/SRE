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
