**TASK**

The Nautilus DevOps team possesses confidential data on App Server 2 in the Stratos Datacenter. A container named ubuntu_latest is running on the same server.

Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /opt/. Ensure the file is not modified during this operation.

**Steps**

ssh steve@stapp02

Verified the container is running

```bash
sudo docker ps | grep ubuntu_latest
```

Copied the encrypted file into the container

```bash
sudo docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/opt/
```

Confirm the file exists inside the container

```bash
sudo docker exec -it ubuntu_latest ls -l /opt/
```
