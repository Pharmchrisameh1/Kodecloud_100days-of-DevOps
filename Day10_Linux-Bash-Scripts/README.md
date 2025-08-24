**TASK**

The Nautilus team wants to create a debug container on Application Server 3. However, they had some specific requirements related to the CMD. Please complete the task as per details given below:


a. On Application Server 3 create a container named debug_3 using image ubuntu/apache2:latest. 


b. Overwrite the default CMD with command sleep 1000. 


c. Make sure the container is in running state.

**Steps**

**SSH into App Server 3**

```bash
ssh banner@stapp03
```

**Run the container with the overwritten CMD**:

```bash
sudo docker run -d --name debug_3 ubuntu/apache2:latest sleep 1000
```

-d → detached mode (runs in background)

--name debug_3 → sets the container name

sleep 1000 → replaces the image’s default CMD


**Verified the container by running**:

```bash
sudo docker ps
```
