**TASK**

There are some applications that need to be deployed on Kubernetes cluster and these apps have some pre-requisites where some configurations need to be changed before deploying the app container. Some of these changes cannot be made inside the images so the DevOps team has come up with a solution to use init containers to perform these tasks during deployment. Below is a sample scenario that the team is going to test first.


Create a Deployment named as ic-deploy-datacenter.

Configure spec as replicas should be 1, labels app should be ic-datacenter, template's metadata lables app should be the same ic-datacenter.

The initContainers should be named as ic-msg-datacenter, use image ubuntu with latest tag and use command '/bin/bash', '-c' and 'echo Init Done - Welcome to xFusionCorp Industries > /ic/ecommerce'. The volume mount should be named as ic-volume-datacenter and mount path should be /ic.

Main container should be named as ic-main-datacenter, use image ubuntu with latest tag and use command '/bin/bash', '-c' and 'while true; do cat /ic/ecommerce; sleep 5; done'. The volume mount should be named as ic-volume-datacenter and mount path should be /ic.

Volume to be named as ic-volume-datacenter and it should be an emptyDir type.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

**Steps**


Created YAML manifest

```bash
ic-deploy-datacenter.yaml
```

Applied the deployment file

```bash
kubectl apply -f ic-deploy-datacenter.yaml
```

Checked that the deployment and pod were created

```bash
kubectl get deployments
kubectl get pods
```

verified the init container ran successfully

```bash
kubectl describe pod ic-deploy-datacenter-5f6b49d9b5-4rt9r
```

Checked the main container logs and confirmed it printed the message written by the init container

```bash
kubectl logs ic-deploy-datacenter-5f6b49d9b5-4rt9r
```



