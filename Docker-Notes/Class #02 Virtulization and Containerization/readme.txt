Virtualization

-> Installing Multiple Guest Operating systems in one Host Operating System
-> Hypervisor S/W will be used to achieve this
-> we need ti install all required softwares in HOST OS to run our application
-> It is old technique to run our application
-> System performance will be slow in this process 
-> To overcome this problem we use Containerization

----------------
Containerization
----------------
-> It is used to package all the softwares and application code in one container 
execution 
-> Container will take care of everything which is required to run our application
-> We can run containers in Multiple Machines easily
-> Docker is a containerization software
-> Using Docker we will create container to our application
-> Using Docker we will create image for our application
-> Docker images we can share easily to Multiple machines
-> Using Docker image we can create docker container and we can execute it.

---------
Commands 
---------

sudo apt update
sudo apt install docker.io
docker info 
docker --version

// to see docker images to execute below command
docker images

// pulling docker image from docker hub
docker pull hello-world

// Running hello world image
docker run hello-world

// to see running containers
docker ps

// to see running and stopped containers
docker ps -a