
Docker by web dev.

1) docker build -t php-app .

2) docker run -d -p 80:80 -v $(pwd)/src:/var/www/app --name=php-app-container php-app

check state
3) docker ps

php newtwork create 
4) docker network create -d bridge php-app-network

find mysql https://hub.docker.com/_/mysql
5) docker run -d -v $(pwd)/.data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=secret --network=php-app-network --name=mysql mysql:5.7.24 

node newtwork create 
6) docker network create -d bridge node-app-network

7) docker run -d -v $(pwd)/src:/usr/src/app --name=node-app-container node:10.15.0 bash

8) npm install mongodb -save

run mongodb container

9) docker run -d -v $(pwd)/.data/mongo:/data/db --network=node-app-network --name=mongo mongo:4.1.6 

---------

check work db
docker exec -it mongo bash

stop container
$ docker stop php-app-container

remove container
$ docker rm php-app-container