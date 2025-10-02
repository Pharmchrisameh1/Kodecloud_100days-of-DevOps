**TASK**

An application currently running on the Kubernetes cluster employs the nginx web server. The Nautilus application development team has introduced some recent changes that need deployment. They've crafted an image nginx:1.19 with the latest updates.

Execute a rolling update for this application, integrating the nginx:1.19 image. The deployment is named nginx-deployment.

Ensure all pods are operational post-update.

Note: The kubectl utility on jump_host is set up to operate with the Kubernetes cluster

**Steps**

Checked the actual container name

```bash
kubectl get deployment nginx-deployment -o yaml | grep -A2 "Containers:"
```

Performed the rolling update with the actual container name

```bash
kubectl set image deployment/nginx-deployment nginx-container=nginx:1.19
```

Checked the rollout status

```bash
kubectl rollout status deployment/nginx-deployment
```

Verified the pods are updated and running successfuly

```bash
kubectl get pods -l app=nginx
kubectl describe deployment nginx-deployment | grep Image:
```



