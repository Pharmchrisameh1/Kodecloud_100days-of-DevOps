**TASK**

The Nautilus DevOps team is planning to host an application on a nginx-based container. There are number of tickets already been created for similar tasks. One of the tickets has been assigned to set up a nginx container on Application Server 2 in Stratos Datacenter. Please perform the task as per details mentioned below:

a. Pull nginx:alpine docker image on Application Server 2.

b. Create a container named demo using the image you pulled.

c. Map host port 3003 to container port 80. Please keep the container in running state.

**Steps**

ssh steve@stapp02

Pulled the nginx:alpine image

```bash
sudo docker pull nginx:alpine
```

Ran the container named demo

Mapped host port 3003 → container port 80, and ensured it stays running:

```bash
sudo docker run -d --name demo -p 3003:80 nginx:alpine
```

Verified the container was running

```bash
sudo docker ps
```

Tested with curl

```bash
curl http://localhost:3003
```


