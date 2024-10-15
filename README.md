# Crud_App

docker ps 
docker ps -a


# building docker
docker build .


# image building
docker build -t express-image

# container building 
docker run -p 3000:3000 --name express-container express-image

# detach mode
docker run -d -p 3000:3000 --name express-container express-image

# Stoping container
docker stop express-container

#Remove container (-f forcefully)
docker remove express-container -f

# To get inside docker environment
docker exec -it express-container bash

# to run on powershell
docker run -v ${pwd}:/app -p 3000:3000 -d --name express-container express-image

# To print logs of running container
docker logs express-container

#Mount anonymous Volume
docker run -v ${pwd}:/app -v /app/node_modules  -p 3000:3000 -d --name express-container express-image

#Docker remove container and Volume
docker rm express-container -fv

#Read only mount Volume
docker run -v ${pwd}:/app:ro -v /app/node_modules  -p 3000:3000 -d --name express-container express-image





(Docker file me )
Expose 3000 ko comment krke 

ENV PORT 3000
EXPOSE ${PORT}

Pass environment variable
docker run -v ${pwd}:/app:ro -v /app/node_modules -env PORT=4000  -p 3000:3000 -d --name express-container express-image

#Execute docekr compose
docker-compose up -d                                                                                Q


#remove container
docker-compose down
docker-compose down -v


# For New image
docker-compose up -d --build


RUN dev ENV
docker-compose -f docker-compose.yaml -f docker-compose.dev.yaml up -d

#rebuild the image
docker-compose -f docker-compose.yaml -f docker-compose.dev.yaml up -d --build


DOWN dev ENV
docker-compose -f docker-compose.yaml -f docker-compose.dev.yaml down 

Run prod ENV
docker-compose -f docker-compose.yaml -f docker-compose.prod.yaml up -d

#rebuild the image
docker-compose -f docker-compose.yaml -f docker-compose.prod.yaml up -d --build

Down prod ENV
docker-compose -f docker-compose.yaml -f docker-compose.prod.yaml down 

#Setup MongoDB with Express and Docker
#FIRST DELETE ALL THE CONTAINERS ,IMAGES AND Volume

#TO RUN
docker-compose -f docker-compose.yaml -f docker-compose.dev.yaml up -d

#to check both the containers are running or not.
docker ps

#go inside mongodb container
docker exec -it crud-app-mongo-1 bash
#then 
ls 

#then go inside bin
cd bin

#then go inside mongodb shell
mongosh -u "root" -p "root"

#then to see how many dbs are there inside mongodb
show dbs;

#then create dbs
use crud_db;

#then after creating db create collecion
db.createCollection("employees");

#to see collection
show collections;


#easy way 
docker exec -it crud-app-mongo-1 /bin/mongosh -u "root" -p "root"



#SETUP MONGOOSE

npm install MONGOOSE

#to get IP of mongo container
docker inspect crud-app-mongo-1
