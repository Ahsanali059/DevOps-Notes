==================
What is Kubernetes
==================

*) K8S is an open source orchestration platform.
*) K8S used to manage containers.
*) K8S developed in Google using GO Language.
*) K8S v1.0 released in 2015

Note: Kubernetes will use Docker internally.Using K8S we will manage our 
      Docker containers

2) Docker Swarm vs Kubernetes
   
   -> Docker Swarm doesn't have auto scaling (Scaling is manual process).
   -> K8S supports auto-scaling 
   -> For Production deployments K8S is highly recommended 
   -> Kubernetes is replacement of Docker Swarm 

Auto-Scaling: Increasing and Decreasing containers count based on incoming 
requests for our app.

===============
What is Cluster
===============
   -> Group of servers 
   -> Master Node 
   -> Worker Node 
   -> DevOps Engineer / Developer will give task to K8S Master Node 
   -> Master Node will manage worker nodes. 
   -> Our containers will be created in Worker Nodes.
   -> Using Cluster we can achieve high availability.

Note: Master not can be multiple for high availability.
-> Master Node in Kubernetes is called control plane

==================================
Kubernetes Architecture Components
==================================
Control plane: It is called as master node (responsible to handle K8S related work)

=> API Server: It is responsible to handle incoming requests of control 
Plane (to deployments our application).

=> Etcd: It is internal database in K8S cluster,API Server will store 
requests / tasks info in Etcd.

=> Schedular: It is responsible to Schedule pending tasks available in Etcd.
-> It will decide in which worker node our task execute. Schedular will 
decide that by communicating with Kubelet.

=> Kubelet: It is worker node agent.It will maintain all the information related 
to Worker Node.

=> Controller Manager: After Scheduling completed,Controller Manager will 
manage our task execution in Worker Node.

=> Kube-Proxy: It will provide network for K8S cluster communication 
(Master Node<---------->Worker Node)

=> Docker Engine: To run our container Docker engine is required.containers will be 
created in worker Node.

=> Container: It is runtime instance of our application.
=> POD: It is a smallest building block that we will create in K8S to 
run our container.

=> Containers will run inside the POD.
  
=================|
Why we need POD ?|
=================|
-> Pods are needed because they provide a shared context for containers, 
including network and storage, simplifying deployments and resource management. 
-> They allow for tightly coupled containers to communicate easily and efficiently 
within the same network namespace.  