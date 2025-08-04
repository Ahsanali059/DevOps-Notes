========
Services
========

-> Services are used to expose the Pods 

1) Cluster Ip

2) Node Port

3) Load Balancer


*) PODS Empheral 
*) Pods are short lived objects 
*) When POD is recreated IP address will change

==========
Cluster IP
==========

-> When we create PODS, every POD will get the unique ip address
-> We can access POD inside cluster using its IP address

Note: PODS are short lived objects. When POD is re-created its ip will be changed
so we can't depend on POD IP to access.

-> To expose POD access with in the cluster we can use ClusterIP Service.
-> ClusterIP will generate one IP address to access our PODS with in cluster.

Note: ClusterIP will not changed when pods are re- created.

-> Where we use this cluster IP Service ? 

*) Database PODS 
*) Backend PODS 

We don't want to expose my db and backend API to browser or end-user. 

========================================
Combined Manifest file for POD & Service
========================================

---
apiVersion:v1
kind: Pod
metadata:
    name:javawebapppod
    labels:
       app:javawebapp # very Important
spec:
   containers:
    - name: javawebappcontainer
      image:ahsan/javawebapp
      ports:
         - containerPort:8080

---
apiVersion: v1
kind:Service
metadata:
   name: javawebappsvc
spec:
   type: NodePort
   selector:
       app:javawebapp # POD Label  
   ports:
       - port: 80
         targetPort: 8080
         nodePort: 30785

==========
Node Port
==========

=> NodePort service is used to expose pods outside cluster also.
=> When we use NodePort service we can specify Node Port number in
service manifest file.
=> If we don't specify Node Port number then k8s will assign 
random node port number for our service. 

Node port Range is: 30000 - 32767

----------------------------------------------------------------
# Delete all K8S Components we have created
$ kubectl delete all --all 

# Apply manifest file
$ kubectl apply -f <manifest.yml>

# Get Pods
$ kubectl get pods

# Get Services
$ kubectl get svc

# Check POD running in which Node
$ kubectl get pods -o wide

# Access application in browser (make sure node port number enabled in Security Group)

UTL: http://node-public-ip:node-port-no/javawebapp


