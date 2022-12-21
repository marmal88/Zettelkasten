# Kubernetes Core Concepts




## 1. Clusters and Nodes
- Kubernetes cluster is a set of nodes that run containerized applications.
- A Node is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster

## 2. Pods
- Pod represents a single instance of a running process in your cluster
generating the yaml file and creating with pod definition file

```bash
kubectl run redis --image=redis123 --dry-run=client -o yaml > redis.yaml
cat redis.yaml
vi redis.yaml
```

## 3. Namespaces
Namespaces provides a mechanism for isolating groups of resources within a single cluster


## 4. Deployment 
Kubernetes Deployment tells Kubernetes how to create or modify instances of the pods that hold a containerized application



## 5. Service
Service in Kubernetes is an abstraction which defines a logical set of Pods and a policy by which to access them
