**TASK**

xFusionCorp Industries is planning to host a WordPress website on their infra in Stratos Datacenter. They have already done infrastructure configuration—for example, on the storage server they already have a shared directory /vaw/www/html that is mounted on each app host under /var/www/html directory. Please perform the following steps to accomplish the task:

a. Install httpd, php and its dependencies on all app hosts.

b. Apache should serve on port 6000 within the apps.

c. Install/Configure MariaDB server on DB Server.

d. Create a database named kodekloud_db1 and create a database user named kodekloud_rin identified as password 8FmzjvFU6S. Further make sure this newly created user is able to perform all operation on the database you created.

e. Finally you should be able to access the website on LBR link, by clicking on the App button on the top bar. You should see a message like App is able to connect to the database using user kodekloud_rin

**Steps**

ssh tony@stapp01

Instaledl Apache, PHP and dependencies

```bash
sudo yum install httpd php php-mysqlnd -y
sudo systemctl enable httpd
sudo systemctl start httpd
```

Configured Apache to serve on port 6000 by changing listen from 80 to 6000

```bash
sudo vi /etc/httpd/conf/httpd.conf
```
Added virtual host config

```bash
sudo vi /etc/httpd/conf.d/wordpress.conf
```
<VirtualHost *:6000>
    DocumentRoot /var/www/html
    ServerName localhost

    <Directory /var/www/html>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>

Restarted the apache

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl restart httpd
```

The above procedures were repeated for server2 and server3

Then logged into the database

ssh peter@stdb01

Installed and Configured MariaDB on DB Server

```bash
sudo yum install -y mariadb-server
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

Created database and user

```bash
sudo mysql -u root
```

CREATE DATABASE kodekloud_db1;

CREATE USER 'kodekloud_rin'@'%' IDENTIFIED BY '8FmzjvFU6S';

GRANT ALL PRIVILEGES ON kodekloud_db1.* TO 'kodekloud_rin'@'%';

FLUSH PRIVILEGES;

EXIT;
