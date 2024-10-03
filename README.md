# commands

## Create a docker volume

docker volume create postgres-vol

## create a docker netowrk

docker network create <network-name>

## start mongo db

docker run -d \  
-p 27017:27017 \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONDO_INITDB_ROOT_PASSWORD=passworkd \
--net <network-name> \
--name mongodb \
mongo:latest

## start mongo-express

docker run -d \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
--net <network-name> \
--name mongo-express \
mongo-express

## Run mongo in a container and expose it so it can be used outside the container

docker run --name mongodb -p 27017:27017 -d mongodb/mongodb-community-server

## To persist data saved in a database, you have to create a volumn to hold the data outside of the container

docker run --name mongodb -p 27017:27017 -v /Users/kennyc/Documents/dev/data -d mongodb/mongodb-community-server
