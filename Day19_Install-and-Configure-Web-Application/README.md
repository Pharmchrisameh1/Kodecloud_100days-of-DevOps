**TASK**

xFusionCorp Industries is planning to host two static websites on their infra in Stratos Datacenter. The development of these websites is still in-progress, but we want to get the servers ready. Please perform the following steps to accomplish the task:

a. Install httpd package and dependencies on app server 2.

b. Apache should serve on port 6300.

c. There are two website's backups /home/thor/blog and /home/thor/demo on jump_host. Set them up on Apache in a way that blog should work on the link http://localhost:6300/blog/ and demo should work on link http://localhost:6300/demo/ on the mentioned app server.

d. Once configured you should be able to access the website using curl command on the respective app server, i.e curl http://localhost:6300/blog/ and curl http://localhost:6300/demo/

**Steps**

ssh steve@stapp02

Installed httpd

```bash
sudo yum install -y httpd
sudo systemctl enable httpd
sudo systemctl start httpd
```

Configured Apache to serve on port 6300

```bash
sudo vi /etc/httpd/conf/httpd.conf
```

Created a new VirtualHost config file:

```bash
sudo vi /etc/httpd/conf.d/static_sites.conf
```

<VirtualHost *:6300>
    DocumentRoot /var/www/html
    ServerName localhost

    Alias /blog /var/www/html/blog
    <Directory /var/www/html/blog>
        AllowOverride All
        Require all granted
    </Directory>

    Alias /demo /var/www/html/demo
    <Directory /var/www/html/demo>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>


Navigated to the jump_host and Copied the website backups

```bash
scp -r /home/thor/blog /home/thor/demo steve@172.16.238.11:/tmp/
```
Navigated back to the server2 terminal

```bash
sudo mv /tmp/blog /var/www/html/blog
sudo mv /tmp/demo /var/www/html/demo
sudo chown -R apache:apache /var/www/html/blog /var/www/html/demo
```

Restarted Apache

```bash
sudo systemctl restart httpd
```

Verified the curl

```bash
curl http://localhost:6300/blog/
curl http://localhost:6300/demo/
```



