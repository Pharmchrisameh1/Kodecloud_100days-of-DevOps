**TASK**

Some of the Nautilus team developers are developing a static website and they want to deploy it on Kubernetes cluster. They want it to be highly available and scalable. Therefore, based on the requirements, the DevOps team has decided to create a deployment for it with multiple replicas. Below you can find more details about it:

Create a deployment using nginx image with latest tag only and remember to mention the tag i.e nginx:latest. Name it as nginx-deployment. The container should be named as nginx-container, also make sure replica counts are 3.

Create a NodePort type service named nginx-service. The nodePort should be 30011.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

**Steps**

Created the manifest

```bash
vi nginx-deployment.yaml
```

```bash
nginx-service.yaml
```

Applied it

```bash
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-service.yaml
```

Then verified

```bash
kubectl describe deployment nginx-deployment
kubectl describe service nginx-service
```



