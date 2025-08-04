# Print container logs 
docker logs <container-id>

# Get into docker container
docker exec -it <container-id> /bin/bash

# then press exit back from container 

===================
React Js Dockerfile
===================

FROM node:latest

COPY package.json /app

WORKDIR /app 

RUN npm install 

COPY .. 

ENTRYPOINT ["npm","start"]