**TASK**

One of the Nautilus DevOps team members was working to configure services on a kkloud container that is running on App Server 3 in Stratos Datacenter. Due to some personal work he is on PTO for the rest of the week, but we need to finish his pending work ASAP. Please complete the remaining work as per details given below:

a. Install apache2 in kkloud container using apt that is running on App Server 3 in Stratos Datacenter.

b. Configure Apache to listen on port 3001 instead of default http port. Do not bind it to listen on specific IP or hostname only, i.e it should listen on localhost, 127.0.0.1, container ip, etc.

c. Make sure Apache service is up and running inside the container. Keep the container in running state at the end.

**Steps**

Installed Apache2 in kkloud container

```bash
docker exec -it kkloud bash
apt-get update
apt-get install -y apache2
```

Used sed to directly replace port 80 with 3001

```bash
sed -i 's/Listen 80/Listen 3001/' /etc/apache2/ports.conf
sed -i 's/<VirtualHost \*:80>/<VirtualHost *:3001>/' /etc/apache2/sites-enabled/000-default.conf
```

Restarted Apache

```bash
apache2ctl configtest
service apache2 restart
```

Confirmed Apache is listening on port 3001

```bash
apt-get update
apt-get install -y lsof
lsof -i -P -n | grep LISTEN | grep 3001
```

Tested with curl inside container

```bash
curl http://localhost:3001
```
