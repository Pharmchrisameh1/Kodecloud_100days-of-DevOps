**TASK**

Day 62 challenge

 The Nautilus DevOps team is working to deploy some tools in Kubernetes cluster. Some of the tools are licence based so that licence information needs to be stored securely within Kubernetes cluster. Therefore, the team wants to utilize Kubernetes secrets to store those secrets. Below you can find more details about the requirements: 



We already have a secret key file blog.txt under /opt location on jump host. Create a generic secret named blog, it should contain the password/license-number present in blog.txt file.


Also create a pod named secret-nautilus.


Configure pod's spec as container name should be secret-container-nautilus, image should be fedora with latest tag (remember to mention the tag with image). Use sleep command for container so that it remains in running state. Consume the created secret and mount it under /opt/apps within the container.


To verify you can exec into the container secret-container-nautilus, to check the secret key under the mounted path /opt/apps. Before hitting the Check button please make sure pod/pods are in running state, also validation can take some time to complete so keep patience.


Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.



**Steps**

Created the Secret

We already have the file /opt/blog.txt on the jump host

Ran this command and created a generic secret named blog:

```
kubectl create secret generic blog --from-file=/opt/blog.txt

```

Verified using:

```
kubectl get secrets
kubectl describe secret blog
```

Created the Pod Manifest

```
vi secret-pod-nautilus.yaml

```

Applied the Manifest

```
kubectl apply -f secret-pod-nautilus.yaml

```

Verified Pod and Secret Mount by checking the pod's status

```
kubectl get pods

```

Then, exec into the container:

```
kubectl exec -it secret-nautilus -- sh

```

Checked the mounted secret inside the container

```
ls /opt/apps
cat /opt/apps/blog.txt
```

Then exited

```
exit
```
