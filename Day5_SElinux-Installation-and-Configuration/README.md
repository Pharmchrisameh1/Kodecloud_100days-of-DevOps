**TASK**:

Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.


Your task is to disable direct SSH root login on all app servers within the Stratos Datacenter.

**Steps**

```bash
ssh tony@stapp01
```

**Edited the SSH configuration file**:
```bash
sudo vi /etc/ssh/sshd_config
```

Found and updated this line and changed the permission to "no":

- PermitRootLogin yes
+ PermitRootLogin no


**Saved the file and restarted the SSH service**:
```bash
sudo systemctl restart sshd
```

**Verified that root login was succeffuly disabled**:
```bash
sudo grep PermitRootLogin /etc/ssh/sshd_config
```
The above procedures were repeated for app server2 and app server3 
