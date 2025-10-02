**TASK**

The Nautilus DevOps team is diving into Kubernetes for application management. One team member has a task to create a pod according to the details below:

Create a pod named pod-httpd using the httpd image with the latest tag. Ensure to specify the tag as httpd:latest.

Set the app label to httpd_app, and name the container as httpd-container.

Note: The kubectl utility on jump_host is configured to operate with the Kubernetes cluster.

**Steps**

Created the pod manifest 

```bash
 vi pod-httpd.yaml
```

Applied the manifest with kubectl

```bash
kubectl apply -f /tmp/pod-httpd.yaml
```

Verified the pod

```bash
kubectl get pods -o wide
kubectl describe pod pod-httpd
```





