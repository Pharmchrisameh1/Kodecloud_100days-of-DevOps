**TASK**

The Nautilus application development team shared static website content that needs to be hosted on the httpd web server using a containerised platform. The team has shared details with the DevOps team, and we need to set up an environment according to those guidelines. Below are the details:

a. On App Server 2 in Stratos DC create a container named httpd using a docker compose file /opt/docker/docker-compose.yml (please use the exact name for file).

b. Use httpd (preferably latest tag) image for container and make sure container is named as httpd; you can use any name for service.

c. Map 80 number port of container with port 5004 of docker host.

d. Map container's /usr/local/apache2/htdocs volume with /opt/data volume of docker host which is already there. (please do not modify any data within these locations).

**Steps**

ssh steve@stapp02

Created the directory for the compose file

```bash
sudo mkdir -p /opt/docker
cd /opt/docker
```

Created the docker-compose file

```bash
docker-compose.yml
```

Downloaded docker-compose binary

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose
```

Made it executable

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

Ran docker-compose

```bash
cd /opt/docker
sudo docker-compose up -d
```



