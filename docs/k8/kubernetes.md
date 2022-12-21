# Kubernetes

## Table of Contents



## Common commands


```bash
# exam tips
Create an NGINX Pod

kubectl run nginx --image=nginx

Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)

kubectl run nginx --image=nginx --dry-run=client -o yaml

Create a deployment

kubectl create deployment --image=nginx nginx

Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)

kubectl create deployment --image=nginx nginx --dry-run=client -o yaml

Generate Deployment YAML file (-o yaml). Don't create it(--dry-run) with 4 Replicas (--replicas=4)

kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml

Save it to a file, make necessary changes to the file (for example, adding more replicas) and then create the deployment.

kubectl create -f nginx-deployment.yaml

OR

In k8s version 1.19+, we can specify the --replicas option to create a deployment with 4 replicas.

kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml

kubectl replace --force -f nginx.yaml
```


kubectl run hello-minikube
kubectl cluster-info
kubectl get nodes

## YAML in kubernetes
apiVersion
kind
metadata
spec

## Core Concepts

## Replica sets
replica set

- labels and selectors
  - can use labels to tell the replicaset which containers to monitor
  - keep template section even if pods already created, as replicaset needs the info if all pods go down

```bash
kubectl create -f replicaset-definition.yml # replicaset-definition,yml
kubectl get replicaset #replicationcontroller
kubectl delete replicaset myapp-replicaset
```

scaling
either of the below, note that 2/3 does not replace the yaml file
```bash
kubectl replace -f replicaset-definition.yml # replace content of replicaset file
kubectl scale --replicas=6 -f replicaset-definition.yml
kubectl scale --replicas=6 replicaset myapp-replicaset # type name
```

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-replicaset
  labels:
    app: myapp
    type: front-end
spec:
  template:
    metadata: myapp-pod
    labels:
      app: myapp
      type: front-end
    spec:
      containers:
      - name: nginx-container
        image: nginx
  replicas: 3
  selector:
    matchLabels:
      type: front-end
```

## Deployments
- upgrade definition seamlessly (kind: Deployment)
- upgrading on rolling basis, rollback of changes, multiple changes

```bash
kubectl create -f deployment-definition.yml
kubectl get deployments

```

## etcd

### etcd v2
etcdctl backup
etcdctl cluster-health
etcdctl mk
etcdctl mkdir
etcdctl set

### etcd v3
etcdctl snapshot save 
etcdctl endpoint health
etcdctl get k1 v1
etcdctl put k1

set the right version of etcd api for the correct commands to be used
export ETCDCTL_API=3
export ETCDCTL_API=3 ./etcd version

Specify path to certificates files for etcdctl to authenticate etcd api server
```bash
kubectl exec etcd-master -n kube-system -- sh -c "ETCDCTL_API=3 etcdctl get / 
--prefix --keys-only --limit=10 --cacert /etc/kubernetes/pki/etcd/ca.crt 
--cert /etc/kubernetes/pki/etcd/server.crt  
--key /etc/kubernetes/pki/etcd/server.key" 
```