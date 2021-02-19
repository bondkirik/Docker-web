
Docker by web dev.

1. docker build -t php-app .

2. docker run -d -p 80:80 -v $(pwd)/src:/var/www/app --name=php-app-container php-app

php newtwork create :
3. docker network create -d bridge php-app-network

find mysql https://hub.docker.com/_/mysql:
4. docker run -d -v $(pwd)/.data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=secret --network=php-app-network --name=mysql mysql:5.7.24 

Node newtwork create and mongo: 
5. docker network create -d bridge node-app-network

6. docker run -d -v $(pwd)/src:/usr/src/app --name=node-app-container node:10.15.0 bash

7. npm install mongodb -save

8. docker run -d -v $(pwd)/.data/mongo:/data/db --network=node-app-network --name=mongo mongo:4.1.6 

---------
check state:
docker ps

check work db:
docker exec -it mongo bash

stop container:
$ docker stop php-app-container

remove container:
$ docker rm php-app-container
