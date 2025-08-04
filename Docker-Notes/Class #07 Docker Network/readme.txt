=> Network is all about communication 
=> Docker Network is used to provided isolated network Docker container
=> In Docker we have below 3 default networks
           1) bridge
           2) host 
           3) none

=> In Docker we have Network Drivers

1) Bridge --> This is default network driver 
2) Host
3) None 
4) Overlay -------> Docker Swarm
5) Macvlan

---------------------------------------------------------------------------------------------
-> Bridge driver is recommended driver when we are using standalone container.It will assign 
one IP for our docker container.

-> Host driver is also used to run standalone container but it will not any IP for container.
-> None means no network available for docker container.
-> Overlay network driver is used for Orchestration.Docker Swarm will use this Overlay driver 
-> Macvlan network driver provide Physical IP for container.
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
# list down all networks
  docker network ls

# create our own docker network
  docker network create my-network

# Inspect docker network
  docker network inspect my-network

# Run Docker container in our network
  docker run -d -p 9090:9090 --network my-network imageName

# delete docker network 
  docker network rm my-network
