**TASK**

The Nautilus system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in Stratos DC on a set schedule
.
Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below: 

a. Install cronie package on all Nautilus app servers and start crond service. 

b. Add a cron */5 * * * * echo hello > /tmp/cron_text for root user.

**Steps**

SSH into each App Server into each app server 

```bash
ssh tony@stapp01
```
Installed cronie

```bash
sudo yum install -y cronie
```

Enabled & start the cron service

```bash
sudo systemctl enable crond
sudo systemctl start crond
```

Checked:

```bash
systemctl status crond
```


Added the cron job for root

Edited root’s crontab:

```bash
sudo crontab -e
```

Added

```bash
*/5 * * * * echo hello > /tmp/cron_text
```

Saved and exited

Verified

```bash
sudo crontab -l
```
