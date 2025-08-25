**TASK**

Following a security audit, the xFusionCorp Industries security team has opted to enhance application and server security with SELinux. To initiate testing, the following requirements have been established for App server 1 in the Stratos Datacenter:



Install the required SELinux packages.

Permanently disable SELinux for the time being; it will be re-enabled after necessary configuration changes.

No need to reboot the server, as a scheduled maintenance reboot is already planned for tonight.

Disregard the current status of SELinux via the command line; the final status after the reboot should be disabled.

**Steps**

```bash
ssh tony@stapp01
```
**Installed SELinux packages**

Since most CentOS/RHEL-based systems use yum or dnf. This was installed:

```bash
sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils
```

If yum is replaced by dnf on the system:

```bash
sudo dnf install -y selinux-policy selinux-policy-targeted policycoreutils
```
**Permanently disabled SELinux**

Edited the SELinux configuration file:

```bash
sudo vi /etc/selinux/config
```

Found this line "SELINUX=enforcing" and changed the "enforcing" to "disabled"

SELINUX=enforcing


Changed to:

SELINUX=disabled


