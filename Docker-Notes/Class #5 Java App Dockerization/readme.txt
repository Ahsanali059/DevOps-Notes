==============================
Java Application Dockerization
==============================

=> We can see two types of applications in companies 
   
   1) Java Application without springBoot
   2) Java Application with springBoot

=> Normal Java applications will be packaged as WAR file and they will deployed in webserver
(Ex:tomcat)

=> springBoot applications will be packaged as jar file and we need to run jar file.
It will take care ok internally(Embedded server)

------------------------> Dockerfile for Normal Java App<---------------------

FROM tomcat:8.0.20-jre8

COPY target/app.war /user/local/tomcat/webapps/app.war

EXPOSE 8080

=========================================================================
In remote Machine

sudo service docker start

sudo apt install git 
sudo apt install maven
sudo git clone url 

cd maven-web-app
mvn clean package 

// Run container on specific port number 
docker run -p 8080:8080 maven-web-app // first port represent host port number and second container port number

then access this in url -> publicId:8080/appName

-------------------------------------------------------------------------------------------------------------------------------
Open Container on detached Mode means our terminal is ready for next command
docker run -d -p 8080:8080 maven-web-app

Important Note: Enable 8080 Port in Security Group Inbound rules (Custom TCP - 8080) 
                Type: Custom TCP
                Port Range: 8080
                Source : Anywhere IPV4  

=> Access your Application in Browser
   URL: http://ec2-vm-public-vm-publicId:8080/maven-web-app

====================================
Dockerization springBoot application
====================================

=> Spring boot app will be packaged as Jar file (even if it is web app)
=> Spring boot will have Embedded tomcat server to run
=> We no need to deploy spring boot in server manually
=> We Just need to spring boot app jar file,it will take care of server and deployment    

FROM openJdk: 11
COPY target/APP.jar  usr/app/app.jar

WORKDIR /usr/app

EXPOSE 8080

ENTRYPOINT ["Java","-jar","app.jar"]