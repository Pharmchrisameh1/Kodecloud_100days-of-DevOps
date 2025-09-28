**TASK**

As per recent requirements shared by the Nautilus application development team, they need custom images created for one of their projects. Several of the initial testing requirements are already been shared with DevOps team. Therefore, create a docker file /opt/docker/Dockerfile (please keep D capital of Dockerfile) on App server 2 in Stratos DC and configure to build an image with the following requirements:

a. Use ubuntu:24.04 as the base image.

b. Install apache2 and configure it to work on 8086 port. (do not update any other Apache configuration settings like document root etc).

**Steps**

ssh steve@stapp02

Navigated to the directory

```bash
cd /opt/docker
```

Created the Dockerfile

```bash
sudo vi Dockerfile
```

Built the image

```bash
sudo docker build -t nautilus-apache .
```

Run the container

```bash
sudo docker run -d -p 8086:8086 nautilus-apache
```

Verified Apache is running

```bash
sudo docker ps
curl http://localhost:8086
```
