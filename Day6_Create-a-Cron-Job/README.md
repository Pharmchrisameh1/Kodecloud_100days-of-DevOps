**TASK**:

The Nautilus DevOps team possesses confidential data on App Server 1 in the Stratos Datacenter. A container named ubuntu_latest is running on the same server.


Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /usr/src/. 

Ensure the file is not modified during this operation.

**Steps**:

**SSH into App Server 1**

```bash
ssh tony@stapp01
```
**Confirmed the running container**

```bash
docker ps
```

**Copied the file into the container**

```bash
docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src/
```
**Verified inside the container**

Access the container shell:

```bash
docker exec -it ubuntu_latest bash
```

**Then checked if the file is in place**:

```bash
ls -l /usr/src/nautilus.txt.gpg
```
