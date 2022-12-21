# Kubernetes Monitoring

---
## Monitoring Cluster Components
```bash
kubectl top node
```

```bash
kubectl top pods
```

---
## Managing Application Logs

running docker in detach mode obscures the logs from view
```bash
# running docker in detach
docker run -d <docker_image>
# get docker logs using -f to stream logs live
docker logs -f <docker_image>
```


```bash
# create pods using
kubectl create -f <yaml_file>
# observe pods using
kubectl logs -f <pod_name> <container_name>
```