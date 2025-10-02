**TASK**

We encountered an issue with our Nginx and PHP-FPM setup on the Kubernetes cluster this morning, which halted its functionality. Investigate and rectify the issue:

The pod name is nginx-phpfpm and configmap name is nginx-config. Identify and fix the problem.

Once resolved, copy /home/thor/index.php file from the jump host to the nginx-container within the nginx document root. After this, you should be able to access the website using Website button on the top bar.

Note: The kubectl utility on jump_host is configured to operate with the Kubernetes cluster.

**Steps**

Checked if the pod exists and its status

```bash
kubectl get pods | grep nginx-phpfpm
```

Inspected the pod details to know if any of the conainers is failing

```bash
kubectl describe pod nginx-phpfpm
```

Checked logs of both containers to know if nginx config is missing and if socket communication fails in PHP-FPM logs

```bash
kubectl logs nginx-phpfpm -c nginx-container
kubectl logs nginx-phpfpm -c php-fpm-container
```

Verified the ConfigMap and ensured the proper nginx.conf is in order

```bash
kubectl get configmap nginx-config -o yaml
```

Edited the configmap and listen was changed from 8099 to 80

```bash
kubectl edit configmap nginx-config
```

Updated service configuration and port: 8099, targetPort: 8099 were changed to 80 respectively 

```bash
kubectl edit service nginx-service
```

Edited the pod manifest and the mountPath: /usr/share/nginx/html changed to /var/www/html

```bash
k edit po nginx-phpfpm 
```
Output after saving the changes made from the edit above:

changes saved to "/tmp/kubectl-edit-3428308227.yaml"


Applied the fix

```bash
kubectl delete pod nginx-phpfpm
kubectl apply -f /tmp/kubectl-edit-3428308227.yaml --force
kubectl wait --for=condition=Ready pod/nginx-phpfpm --timeout=120s
```

Checked pod status and enured the pod was running and all containers were ready

```bash
kubectl get po
```

Checked and confirmed that the  volume mounts, containers, and configurations were correct after the fix

```bash
kubectl describe pod nginx-phpfpm
```

Copied the PHP file into the pod

```bash
kubectl cp /home/thor/index.php nginx-phpfpm:/var/www/html/index.php -c nginx-container
```

Accessed the container shell

```bash
kubectl exec -it nginx-phpfpm -c nginx-container -- sh
```

Verified the file

```bash
ls
cd /var/www/html
cat index.php
kubectl exec nginx-phpfpm -c nginx-container -- curl -s localhost:80/index.php
```
Finally clicked on the application link provided in the environment  


