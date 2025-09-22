**TASK**

One of the Nautilus developer was working to test new changes on a container. He wants to keep a backup of his changes to the container. A new request has been raised for the DevOps team to create a new image from this container. Below are more details about it:

a. Create an image news:nautilus on Application Server 2 from a container ubuntu_latest that is running on same server.


**Steps**

ssh steve@stapp02


Checked the running container

```bash
sudo docker ps | grep ubuntu_latest
```

Commited the container to a new image

```bash
sudo docker commit ubuntu_latest news:nautilus
```

Verified the image was created

```bash
sudo docker images | grep news
```
