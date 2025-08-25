**TASK**

Our monitoring tool has reported an issue in Stratos Datacenter. One of our app servers has an issue, as its Apache service is not reachable on port 6200 (which is the Apache port). The service itself could be down, the firewall could be at fault, or something else could be causing the issue.

Use tools like telnet, netstat, etc. to find and fix the issue. Also make sure Apache is reachable from the jump host without compromising any security settings. Once fixed, you can test the same using command curl http://stapp01:6200 command from jump host.

**Steps**

```bash
ssh tony@stapp01
```
**Checked if Apache is running**

```bash
sudo systemctl status httpd
```
Started the Apache

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```
**Checked if Apache is listening on port 6200**

```bash
sudo netstat -tulnp | grep httpd
```
Installed netstat

```bash
sudo yum install -y net-tools
```
Re-run the command after the installation

```bash
sudo netstat -tulnp | grep 6200                    
```
Output:

tcp 0 0 127.0.0.1:6200 0.0.0.0:* LISTEN 440/sendmail: accept

The process sendmail (PID 440) is already listening on port 6200, which is why Apache (httpd) can’t bind to it.

**Fixing the problem**

Stopped/disabled sendmail

```bash
sudo systemctl stop sendmail
sudo systemctl disable sendmail
```
Then restarted Apache:

```bash
sudo systemctl restart httpd
sudo systemctl status httpd
```
