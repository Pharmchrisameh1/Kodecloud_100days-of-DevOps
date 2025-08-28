**TASK**

The production support team of xFusionCorp Industries has deployed some of the latest monitoring tools to keep an eye on every service, application, etc. running on the systems. One of the monitoring systems reported about Apache service unavailability on one of the app servers in Stratos DC. 

Identify the faulty app host and fix the issue. Make sure Apache service is up and running on all app hosts. They might not have hosted any code yet on these servers, so you don’t need to worry if Apache isn’t serving any pages. Just make sure the service is up and running. Also, make sure Apache is running on port 3003 on all app servers.


**Steps**

```bash
ssh tony@stapp01
```

Checked Apache service status

```bash
sudo systemctl status httpd
```
Output:
Apache failed to start

Checked Apache error logs to know why it failed to start

```bash
sudo journalctl -xeu httpd --no-pager | tail -20
```
Output:

(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:3003

Checked what’s using port 3003

```bash
sudo netstat -tulpn | grep 3003
```
Output:

tcp 0 0 127.0.0.1:3003 0.0.0.0:* LISTEN 778/sendmail: accep

This means Sendmail is already bound to port 3003, which is why Apache can’t start on that port.

**Stopped Sendmail**

```bash
sudo systemctl stop sendmail
```
Disabled Sendmail from starting on boot

```bash
sudo systemctl disable sendmail
```
Restarted Apache

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```
Confirmed Apache is listening on 3003

```bash
sudo ss -tulpn | grep httpd
```
