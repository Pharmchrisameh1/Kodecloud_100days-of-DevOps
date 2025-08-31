**TASK**

Day by day traffic is increasing on one of the websites managed by the Nautilus production support team. Therefore, the team has observed a degradation in website performance. Following discussions about this issue, the team has decided to deploy this application on a high availability stack i.e on Nautilus infra in Stratos DC. They started the migration last month and it is almost done, as only the LBR server configuration is pending. Configure LBR server as per the information given below:

a. Install nginx on LBR (load balancer) server. 

b. Configure load-balancing with the an http context making use of all App Servers. Ensure that you update only the main Nginx configuration file located at /etc/nginx/nginx.conf. 

c. Make sure you do not update the apache port that is already defined in the apache configuration on all app servers, also make sure apache service is up and running on all app servers. 

d. Once done, you can access the website using StaticApp button on the top bar.

**Steps**

```bash
ssh loki@stlb01
```
Installed and started Nginx

```bash
sudo yum install -y nginx
sudo systemctl enable nginx
sudo systemctl start nginx
```
Confirmed the port(8087) Apache was running on the app servers

```bash
ssh tony@stapp01
```
```bash
sudo systemctl status httpd
sudo ss -tulnp | grep httpd
```
Reverted back to loki@stlb01 and updated /etc/nginx/nginx.conf file

```bash
sudo vi /etc/nginx/nginx.conf file
```
Saved the changes and restarted Nginx 

```bash
sudo nginx -t
sudo systemctl restart nginx
```
Checked the status

```bash
sudo systemctl status nginx
```
