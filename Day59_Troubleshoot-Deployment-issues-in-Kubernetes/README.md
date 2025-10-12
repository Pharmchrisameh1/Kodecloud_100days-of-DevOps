**TASK**

Last week, the Nautilus DevOps team deployed a redis app on Kubernetes cluster, which was working fine so far. This morning one of the team members was making some changes in this existing setup, but he made some mistakes and the app went down. We need to fix this as soon as possible. Please take a look.

The deployment name is redis-deployment. The pods are not in running state right now, so please look into the issue and fix the same.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

**Steps**

Checked the pods

```bash
kubectl get pods
```

Edited the deployment

```bash
kubectl edit deployment redis-deployment

Output:

volumes:
  - name: config
    configMap:
      name: redis-conig
```


Fixed the typo error

The "redis-conig" was changed to "redis-config"


Identified the second failure

```bash
kubectl get pods
```

Edited the deplyment and rectified the image tag by changing "redis:alpin" to "redis:alpine"

```bash
kubectl edit deployment redis-deployment
```

Confirmed the status

```bash
kubectl get pods
```
