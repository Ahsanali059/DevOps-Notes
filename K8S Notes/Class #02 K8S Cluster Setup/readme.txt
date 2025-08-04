========================
Kubernetes Cluster Setup
========================

-> Kubernetes Cluster we can setup in multiple ways

1) Self Managed Cluster K8S cluster 
     *) Kubeadm (Multi Node Cluster)
     *) Mini Kube (Single Node Cluster)--> This is for beginners not for industry project 
     because all of the thing is available inside single cluster

2) Managed K8S Cluster
     *) AWS EKS 
     *) AZURE EKS 
     *) GCP GKE
     *) IBM IKE

-----------------------------------------------------------------------------------------------
In industry Multi Node Cluster will be used but when i use self managed cluster we need to handle 
everything manually so that why we are using self managed cluster

Step 1:

Create one EKS Client VM In this machine install this 3 softwares
   1) AWS Cli 
   2) eksctl(to create eks cluster)
   3) kubectl  

Client VM Contains Kube config file what this file contains 
  -> URL of the Cluster 
  -> What is the location of the cluster
  -> The cluster configuration data will be available in kube config file

=====================
Kubernetes Components
=====================

1) POD 
2) Services 
3) Namespaces
4) Replication Controller 
5) Replication Set 
6) DaemonSet
7) Deployment 
8) StatefulSet
9) Config Map & Secrets
10) IngressController
11) HELM Charts
12) K8S Volumes
13) Grafana & Promethues
14) ELK Setup (Log Aggregation)
15) RBAC
16) K8S Web Dashboard 

===========
What is POD
===========

=> POD is a smallest building block in k8s cluster
=> In K8S,every container will be created inside POD
=> POD always run inside the Node
=> POD represents running process
=> POD means group of containers running on a Node
=> We can create multiple PODS on a single Node
=> Every POD will have unique Ip address

=> We can Create PODS in 2 ways 
         1) Interactive Approach
            $kubectl run --name <pod-name> image=<image-name> --generate=pod/v1

         2) Declarative Approach (K8S Using Manifest YML) // In real time we are use this Approach

=================
K8S Manifest YML
=================

--- // starting point 
apiVersion:

kind:

metadata:

spec:

... //ending point 

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
===========================
Kubernetes POD Manifest YML
===========================

--- // it represents start point of the file 

apiVersion:v1 // apiVersion represents which version of the Kubernetes Manifest file we are using

kind: POD    // kind represents what is the purpose of this file (kind=POD means) to create the POD

metadata: 
    name:javawebapppod // pod name
    labels:            // label means id of the pod 
        app:javawebapp 

spec:                  // container info will be available inside spec
   containers:
   - name: javawebappcontainer
     image: ahsanDockerDubAccount/javawebapp
     ports: 8080


...// it represents end point of the file 

==============================================================================================
In Client VM Run this command 
kubectl get nodes 

// you can see created Nodes 

Q) How this VM get Nodes details ? 

A) When we create the Nodes kubeConfig file will be created inside this Nodes configuration
will be available.this file is available inside one hidden directory .kube in home directory

Important Note: Your dont need to handle or manage control plane this is completely handle by AWS.
*) We have control over worker node
=============================================================================================
Once Yaml file is Ready execute this commands

# get pods but with only status
$ kubectl get pods

# Create POD from yml file 
$ kubectl apply -f javawebapppod.yml

# Get the information about the POD
$ kubectl describe pod javawebapppod

# Check Pod Logs 
$ kubectl logs javawebapppod

# Get POD running on which worker node 
$ kubectl get pods -o wide 

************************************** Note: PODS we can't accessible outside ***************************************************
=> We need to expose PODS for outside access using Kubernetes Services Concept.

===========
K8S Service
===========

=> Kubernetes service is used to expose PODS outside cluster
=> We have 3 type of K8S Services

1) Cluster Ip
2) Node Port 
3) Load Balancer

=> We need to write service manifest yml to expose PODS 

---

apiVersion: v1

kind: Service

metadata: 
    name: javawebappsvc

spec:
  type: NodePort
  selector:
    app:javawebapp
  ports:
    - port: 80
      targetPort:8080

...

Note: When we run service provide random port number to my application get this port number and allow in inbound rule then 
access application
----------------------------------------------| Commands |------------------------------------------------------
# Display existing Services
$ kubectl get svc 

# Create K8S service
$ kubectl apply -f <svc.manifest.yml>


=================
Working Procedure
=================

1) Write POD Manifest yml
2) Create POD using kubectl apply command 
3) Check POD details and POD logs & In which worker node it is running
4) Write Service Manifest yml
5) Create Service to expose pod
6) Check services details and node port assigned by K8S
7) Enable Node Port number in Worker Node Security group
8) Access the application using worker node Ip


     
     