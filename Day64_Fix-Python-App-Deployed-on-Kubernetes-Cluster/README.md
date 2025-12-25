**TASK**

Day64
One of the DevOps engineers was trying to deploy a python app on Kubernetes cluster. Unfortunately, due to some mis-configuration, the application is not coming up. Please take a look into it and fix the issues. Application should be accessible on the specified nodePort.



The deployment name is python-deployment-devops, its using poroko/flask-demo-appimage. The deployment and service of this app is already deployed.

nodePort should be 32345 and targetPort should be python flask app's default port.


Note: The kubectl on jump_host has been configured to work with the kubernetes cluster.


**Steps**

Checked the pod's status

```
kubectl get pods
```

Described the pod to confirm details

```
kubectl describe pod python-deployment-devops-b856d4d4d-ljlzr
```

Verified service configuration

```
kubectl get svc python-service-devops
```
Output:


NAME                    TYPE       CLUSTER-IP     PORT(S)          AGE
python-service-devops   NodePort   10.96.5.7      8080:32345/TCP   20m


Edited the deployment to correct the image name:

```
kubectl edit deployment python-deployment-devops
```
containers:
- name: python-container-devops
  image: poroko/flask-demo-app:latest
  ports:
    - containerPort: 5000


Verified the pod status:

```
kubectl get pods -l app=python_app -w
```

Checked container logs:

```
kubectl logs python-deployment-devops-b856d4d4d-ljlzr
```

Tested the application internally:

```
kubectl exec -it python-deployment-devops-b856d4d4d-ljlzr -- curl http://localhost:5000
```


