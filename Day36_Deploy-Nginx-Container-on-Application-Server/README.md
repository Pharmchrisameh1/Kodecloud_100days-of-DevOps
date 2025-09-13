**TASK**

The Nautilus DevOps team is conducting application deployment tests on selected application servers. They require a nginx container deployment on Application Server 1. Complete the task with the following instructions:

On Application Server 1 create a container named nginx_1 using the nginx image with the alpine tag. Ensure container is in a running state.


**Steps**

ssh tony@stapp01

Pulled the nginx alpine image

```bash
sudo docker pull nginx:alpine
```

Ran the container with name nginx_1

```bash
sudo docker run -d --name nginx_1 nginx:alpine
```

Verified that the container is running

```bash
sudo docker ps
```
