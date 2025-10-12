**TASK**

The Nautilus DevOps team is working on a Kubernetes template to deploy a web application on the cluster. There are some requirements to create/use persistent volumes to store the application code, and the template needs to be designed accordingly. Please find more details below:

Create a PersistentVolume named as pv-datacenter. Configure the spec as storage class should be manual, set capacity to 5Gi, set access mode to ReadWriteOnce, volume type should be hostPath and set path to /mnt/dba (this directory is already created, you might not be able to access it directly, so you need not to worry about it).

Create a PersistentVolumeClaim named as pvc-datacenter. Configure the spec as storage class should be manual, request 1Gi of the storage, set access mode to ReadWriteOnce.

Create a pod named as pod-datacenter, mount the persistent volume you created with claim name pvc-datacenter at document root of the web server, the container within the pod should be named as container-datacenter using image httpd with latest tag only (remember to mention the tag i.e httpd:latest).

Create a node port type service named web-datacenter using node port 30008 to expose the web server running within the pod.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.


**Steps**

Created the required resource files

```bash
pv-datacenter.yaml
pvc-datacenter.yaml
pod-datacenter.yaml
service-datacenter.yaml
```

Applied the resources sequentially and ensured the volume and claim were ready before creating the pod

```bash
kubectl apply -f pv-datacenter.yaml
kubectl apply -f pvc-datacenter.yaml
kubectl apply -f pod-datacenter.yaml
kubectl apply -f service-datacenter.yaml
```

Checked the PersistentVolume and PersistentVolumeClaim

```bash
kubectl get pv
kubectl get pvc
```

Checked the Pod and Service

```bash
kubectl get pods -o wide
kubectl get svc
```

Clicked on the link provided in the environment to verify the status
