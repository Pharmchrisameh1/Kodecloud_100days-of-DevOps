**TASK**

The Nautilus application development team observed some performance issues with one of the application that is deployed in Kubernetes cluster. After looking into number of factors, the team has suggested to use some in-memory caching utility for DB service. After number of discussions, they have decided to use Redis. Initially they would like to deploy Redis on kubernetes cluster for testing and later they will move it to production. Please find below more details about the task:


Create a redis deployment with following parameters:

Create a config map called my-redis-config having maxmemory 2mb in redis-config.

Name of the deployment should be redis-deployment, it should use
redis:alpine image and container name should be redis-container. Also make sure it has only 1 replica.

The container should request for 1 CPU.

Mount 2 volumes:

a. An Empty directory volume called data at path /redis-master-data.

b. A configmap volume called redis-config at path /redis-master.

c. The container should expose the port 6379.

Finally, redis-deployment should be in an up and running state.
Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

**Steps**

Created ConfigMap

```
vi redis-config.yaml
```

The configmap was applied after it was created

```
kubectl apply -f redis-config.yaml
```

It was verified

```
kubectl get configmap my-redis-config
```

Created Redis Deployment

```
vi redis-deployment.yaml
```

Applied the deployment

```
kubectl apply -f redis-deployment.yaml
```

Verified Deployment and Pod

```
kubectl get deployments
kubectl get pods
```

```
Output:

NAME                                READY   STATUS    RESTARTS   AGE
redis-deployment-68fbd4467-q72w9    1/1     Running   0          2m
```

Verified ConfigMap Mount

```
kubectl exec -it redis-deployment-68fbd4467-q72w9 -- cat /redis-master/redis-config
```

```
Output:

maxmemory 2mb
```

Verified Port and Resource Requests

```
kubectl describe pod redis-deployment-68fbd4467-q72w9
```

