**TASK**

The Nautilus DevOps team aims to containerize various applications following a recent meeting with the application development team. They intend to conduct testing with the following steps:

Install docker-ce and docker compose packages on App Server 1.

Initiate the docker service.

**Steps**

ssh tony@stapp01

Installed dependencies

```bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```

Added the official Docker repo

```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

Started and enabled Docker service

```bash
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker
```

```bash
Verified the installation
docker --version
docker compose version
```
