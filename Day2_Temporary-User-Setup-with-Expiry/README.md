**Day2 of 100 days of DevOps**

The Nautilus DevOps team is conducting application deployment tests on selected application servers. They require a nginx container deployment on Application Server 2. Complete the task with the following instructions: On Application Server 2 create a container named nginx_2 using the nginx image with the alpine tag. Ensure container is in a running state.

**Steps**

**SSH into Application Server 2**

```bash
ssh steve@stapp02
```

**Pulled the nginx:alpine image**
```bash
docker pull nginx:alpine
```

**Created and ran the container named nginx_2**
```bash
docker run -d --name nginx_2 nginx:alpine
```
**Rationale:**

-d runs the container in detached mode.

--name nginx_2 sets the container name.

nginx:alpine is the image with the alpine tag.

**Verified the container is running**
```bash
docker ps
```
