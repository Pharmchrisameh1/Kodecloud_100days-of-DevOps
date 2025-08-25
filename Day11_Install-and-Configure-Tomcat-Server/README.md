**TASK**

The Nautilus application development team recently finished the beta version of one of their Java-based applications, which they are planning to deploy on one of the app servers in Stratos DC. 

After an internal team meeting, they have decided to use the tomcat application server. 

Based on the requirements mentioned below complete the task: 

a.Install tomcat server on App Server 3. 

b. Configure it to run on port 5004. 

c. There is a ROOT.war file on Jump host at location /tmp. 

Deploy it on this tomcat server and make sure the webpage works directly on base URL i.e curl http://stapp03:5004

**Steps**

```bash
scp /tmp/ROOT.war banner@stapp03:/tmp/
```

SSH into App Server 3

```bash
ssh banner@stapp03
```
Installed Tomcat

On CentOS/RHEL-based (which Stratos DC servers usually are):

```bash
sudo yum install -y tomcat tomcat-webapps tomcat-admin-webapps
```
Configured Tomcat to run on port 5004

Edited config file:

```bash
sudo vi /etc/tomcat/server.xml
```

Look for:

<Connector port="8080" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />


Changed 8080 → 5004:

<Connector port="5004" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />


Saved and exited

```bash
sudo systemctl restart tomcat
sudo systemctl enable tomcat
```
Checked status:

```bash
sudo systemctl status tomcat
```

One possible blocker: If firewall is enabled on stapp03, there may be need to allow port 5004:

```bash
sudo firewall-cmd --permanent --add-port=5004/tcp
sudo firewall-cmd --reload
```
Moved the WAR file into Tomcat’s webapps directory:

```bash
sudo mv /tmp/ROOT.war /usr/share/tomcat/webapps/
```
Restarted Tomcat:

```bash
sudo systemctl restart tomcat
```
Verified from Jump Host:

```bash
curl http://stapp03:5004
```
