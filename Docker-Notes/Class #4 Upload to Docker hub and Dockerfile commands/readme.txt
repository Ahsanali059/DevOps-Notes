//login to docker hub first create account the run this command 

docker login // then enter username and password 

// add tag to image 

docker tag myImage1 ahsan/myImage1

//then push this image to docker hub 
docker push ahsan/myImage1

==================================================================
Can we use user defined name for Dockerfile
==================================================================
Ans) Yes,we can do it but we need to add some addition in build command 

docker build -f sbi_dockerfile -t myImage .

==========
ENTRYPOINT
==========

-> It is used to execute instructions while creating docker container

Syntax:

ENTRYPOINT ["echo","container created Successfully"]
ENTRYPOINT ["Java","-jar","target/springboot.jar"]

=====================================================
What is the difference between CMD And ENTRYPOINT ? 
=====================================================
=> CMD instructions we can override while creating container
=> ENTRYPOINT instructions we can't override

-----------------------------------------------------------------------------------
WORKDIR

-> It is used to specify working directory for image and container

Syntax:
   WORKDIR /app/usr 

-----------------------------------------------------------------------------------
ENV

-> ENV is used to set Environment variables

Example:
  ENV java /etc/softwares/jdk

-----------------------------------------------------------------------------------
EXPOSE

-> It is used to specify on which port number our docker container will run 

EX: 
  EXPOSE 8080

-----------------------------------------------------------------------------------
ARG
-> By using ARG we can take dynamic value from CLI
-> It is used to remove hardcoded values form docker file 

Ex:

ARG branch

RUN git clone -b $branch <repo-url>

NOTE: When i building the image then i need to specify branch name and this branch name
is setted here.

docker build -t imageName --build-arg branch=master

----------------------------------------------------------------------------------
USER 
=> It is used to specify username for creating image / container

Ex:

USER root

----------------------------------------------------------------------------------
VOLUME

=> It is used to specify docker VOLUME Storage location 
=> Volumes are used for storage purpose

Note: Bydefault docker storage is non-persistent if i went to store data in persistent
way we are using docker Volumes

----------------------------------------------------------------------------------
LABEL 
=> It is used to add METADATA to docker Objects in key-value format
EX: 
  LABEL name="spring-rest-image"