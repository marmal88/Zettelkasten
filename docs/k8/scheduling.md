




## 2. Daemon set
A DaemonSet manages groups of replicated Pods which to adhere to a one-Pod-per-node either across the entire cluster or a subset of nodes 


## 3. Replicaset
ReplicaSet ensures that a specified number of pod replicas are running at any given time
However, a Deployment is a higher-level concept that manages ReplicaSets and provides declarative updates to Pods along with a lot of other useful features

## 4. Configmaps
A ConfigMap is an API object used to store non-confidential data in key-value pairs.
```bash
kubectl get cm
kubectl get cm --all-namespaces -o yaml
```

## Taints and tolerances
```bash
kubectl taint <node_name><taint_name>
```

## Labels
```bash
kubectl label <node_name> disktype=ssd
kubectl label <pod_name> env=prod
```