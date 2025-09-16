**TASK**

Nautilus project developers are planning to start testing on a new project. As per their meeting with the DevOps team, they want to test containerized environment application features. As per details shared with DevOps team, we need to accomplish the following task:

a. Pull busybox:musl image on App Server 3 in Stratos DC and re-tag (create new tag) this image as busybox:media.


**Steps**

ssh banner@stapp03

Pulled the image

```bash
sudo docker pull busybox:musl
```

Re-tagged the image as busybox:media

```bash
sudo docker tag busybox:musl busybox:media
```

Verified both tags exists

```bash
sudo docker images | grep busybox
```
