**TASK**

The Nautilus DevOps team is testing some applications deployment on some of the application servers. They need to deploy a nginx container on Application Server 3.
 Please complete the task as per details given below:

On Application Server 3 create a container named nginx_3 using image nginx with alpine tag and make sure container is in running state.

**Steps**

**SSH into App Server 3

```bash
ssh banner@stapp03
```

**Pulled the required image 

```bash
sudo docker pull nginx:alpine
```

**Run the container:

```bash
sudo docker run -d --name nginx_3 nginx:alpine
```

-d → detached mode

--name nginx_3 → assigns container name

nginx:alpine → lightweight nginx image

**Verified it’s running:

```bash
sudo docker ps
```
