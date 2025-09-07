**TASK**

The system admins team of xFusionCorp Industries needs to deploy a new application on App Server 2 in Stratos Datacenter. They have some pre-requites to get ready that server for application deployment. Prepare the server as per requirements shared below: 

1. Install and configure nginx on App Server 2. 

2. On App Server 2 there is a self signed SSL certificate and key present at location /tmp/nautilus.crt and /tmp/nautilus.key. Move them to some appropriate location and deploy the same in Nginx. 

3. Create an index.html file with content Welcome! under Nginx document root. 

4. For final testing try to access the App Server 2 link (either hostname or IP) from jump host using curl command. For example curl -Ik https://<app-server-ip>/.

**Steps**

ssh steve@stapp02

**Installed and enabled Nginx**

```bash
sudo yum install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
```

**Moved SSL certs to the proper location**

```bash
sudo mkdir -p /etc/nginx/ssl
sudo mv /tmp/nautilus.crt /etc/nginx/ssl/
sudo mv /tmp/nautilus.key /etc/nginx/ssl/
sudo chmod 600 /etc/nginx/ssl/nautilus.key
```

**Configured SSL in Nginx**

```bash
sudo vi /etc/nginx/conf.d/ssl.conf
```

server {
    listen 443 ssl;
    server_name stapp02;

    ssl_certificate /etc/nginx/ssl/nautilus.crt;
    ssl_certificate_key /etc/nginx/ssl/nautilus.key;

    root /usr/share/nginx/html;
    index index.html;
}


**Created index.html**

```bash
echo "Welcome!" | sudo tee /usr/share/nginx/html/index.html
```

**Tested Nginx config**

```bash
sudo nginx -t
sudo systemctl reload nginx
```

**Verified from the Jump host**

```bash
curl -Ik https://stapp02
```
