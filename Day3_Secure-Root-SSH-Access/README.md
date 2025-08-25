**TASK**


Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.

Your task is to disable direct SSH root login on all app servers within the Stratos Datacenter.

**Steps to disable direct SSH root login**

```bash
ssh tony@stapp01
```

Edited the SSH configuration file:

```bash
sudo vi /etc/ssh/sshd_config
```
Found and updated the line by changing the permission from yes to no:

- PermitRootLogin yes
+ PermitRootLogin no

Saved the file and restarted the SSH service:

```bash
sudo systemctl restart sshd
```

Verified that root login is disabled:

```bash
sudo grep PermitRootLogin /etc/ssh/sshd_config
```
The same procedures were repeated for server2 and server3
