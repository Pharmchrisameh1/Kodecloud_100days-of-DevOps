**TASK**

An issue has arisen with a static website running in a container named nautilus on App Server 1. To resolve the issue, investigate the following details:



Check if the container's volume /usr/local/apache2/htdocs is correctly mapped with the host's volume /var/www/html.


Verify that the website is accessible on host port 8080 on App Server 1. Confirm that the command curl http://localhost:8080/ works on App Server 1.

**Steps**

```bash
ssh tony@stapp01
```
***Check if /usr/local/apache2/htdocs is mapped to /var/www/html**

First, listed the running containers and confirmed nautilus is up:

```bash
sudo docker ps
```

**Looked for a container named nautilus in the list**
Then inspected it:

```bash
sudo docker inspect nautilus
```

From the output of the docker inspect nautilus command, the "state" shows:

"Status": "exited",
"Running": false,
"ExitCode": 0

This implies that the container is not running. Therefore curl http://localhost:8080 on App Server 1 resulted in failure.

**Fixing the Problem**

```bash
sudo docker start nautilus
```
or

```bash
sudo docker run -d --name nautilus \
  -p 8080:80 \
  -v /var/www/html:/usr/local/apache2/htdocs \
  httpd
```


**Verified website accessibility on port 8080**

Run:

```bash
curl http://localhost:8080/
```
