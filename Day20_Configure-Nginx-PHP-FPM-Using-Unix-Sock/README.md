**TASSK**

The Nautilus application development team is planning to launch a new PHP-based application, which they want to deploy on Nautilus infra in Stratos DC. The development team had a meeting with the production support team and they have shared some requirements regarding the infrastructure. Below are the requirements they shared:

a. Install nginx on app server 2 , configure it to use port 8096 and its document root should be /var/www/html.

b. Install php-fpm version 8.1 on app server 2, it must use the unix socket /var/run/php-fpm/default.sock (create the parent directories if don't exist).

c. Configure php-fpm and nginx to work together.

d. Once configured correctly, you can test the website using curl http://stapp02:8096/index.php command from jump host.

NOTE: We have copied two files, index.php and info.php, under /var/www/html as part of the PHP-based application setup. Please do not modify these files.

**Steps**

ssh steve@stapp02

Installed nginx

```bash
sudo yum install -y nginx
sudo systemctl enable nginx
```

Configured NGINX for the app

```bash
sudo vi /etc/nginx/nginx.conf
```

server {
    listen 8096;
    server_name stapp02;
    root /var/www/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php-fpm/default.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }

}


Restarted Nginx

```bash
sudo systemctl restart nginx
```

Install PHP-FPM

```bash
sudo yum install php php-fpm php-cli -y
```

Configured PHP-FPM

```bash
sudo vi /etc/php-fpm.d/www.conf
```
listen = /var/run/php-fpm/default.sock
listen.owner = apache
listen.group = apache
listen.mode = 0660

Create the directory 

```bash
sudo mkdir -p /var/run/php-fpm
sudo chown -R apache:apache /var/run/php-fpm
```
Restarted PHP-FPM:

```bash
sudo systemctl restart php-fpm
```

Verified the php from the jump host

```bash
curl http://stapp02:8096/index.php
curl http://stapp02:8096/info.php
```

