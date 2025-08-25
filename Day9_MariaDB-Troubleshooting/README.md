**TASK**

There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server. 

Look into the issue and fix the same.

**Steps**

SSH into the Database Server

From the jump host:

```bash
ssh tony@stapp01
```
Checked the MariaDB service status

```bash
sudo systemctl status mariadb
```

If it’s inactive/dead/failed, we need to start it.

If it shows errors, we’ll need to check logs.

Tried starting the service

```bash
sudo systemctl start mariadb
```

Then enabled it to start on boot:

```bash
sudo systemctl enable mariadb
```
Verified

Tested with:

```bash
mysql -u root -p
```
```bash
sudo systemctl status mariadb
```
Still resulted in failure

Checked logs for the reason:

```bash
sudo journalctl -xeu mariadb
```

Common issues:

Checked for corrupted /var/lib/mysql permissions and fixed with

```bash
sudo chown -R mysql:mysql /var/lib/mysql
```

Checked whether port already in use 

```bash
sudo lsof -i :3306
```
Checked detailed logs

Run:

```bash
sudo journalctl -xeu mariadb | tail -30
```
Checked error log file

MariaDB writes detailed errors in /var/log/mariadb/mariadb.log or /var/log/mysql/mysqld.log depending on distro. Checked with:

```bash
sudo cat /var/log/mariadb/mariadb.log | tail -30
```

Common quick fixes

Permission issue with data directory

```bash
sudo chown -R mysql:mysql /var/lib/mysql
sudo chmod -R 755 /var/lib/mysql
```

Corrupted PID or socket file

```bash
sudo rm -f /var/lib/mysql/*.pid
sudo rm -f /var/lib/mysql/*.sock
```

Port conflict(already in use)

```bash
sudo lsof -i :3306
```

Restarted the service

After applying the fix:

```bash
sudo systemctl restart mariadb
sudo systemctl status mariadb
```
Still resulted in failure

```bash
sudo cat /var/log/mariadb/mariadb.log | tail -30
```
Relevant Output:

[ERROR] InnoDB: Operating system error number 13 in a file operation.
[ERROR] InnoDB: The error means mysqld does not have the access rights to the directory.
[ERROR] InnoDB: Cannot open datafile './ibtmp1'

This means MariaDB (mysqld) cannot access its data directory or temp files due to permission issues.

Checked MariaDB data directory ownership
By default, it should be /var/lib/mysql.

Run:

```bash
ls -ld /var/lib/mysql
```
```bash
sudo chown -R mysql:mysql /var/lib/mysql
```

Check the ibtmp1 file and temp files

```bash
ls -l /var/lib/mysql/ibtmp1
ls -ld /var/lib/mysql
```

Checked If ibtmp1 exists but has wrong owner

```bash
sudo chown mysql:mysql /var/lib/mysql/ibtmp1
```

Checked If it is corrupted, and removed it (MariaDB will recreate it):

```bash
sudo rm -f /var/lib/mysql/ibtmp1
```

Checked SELinux (if enabled)
Sometimes SELinux blocks mysqld. 

Run:

```bash
getenforce
```

Tested with:

```bash
sudo setenforce 0
```
Output:

gentforce Disabled

That means the problem is purely filesystem permissions/ownership.

Fixing the problem:

1. Verified MariaDB data directory permissions

Run:

```bash
ls -ld /var/lib/mysql
ls -l /var/lib/mysql | head -20
```
```bash
sudo chown -R mysql:mysql /var/lib/mysql
```
2. Fixed ibtmp1 issue

If ibtmp1 exists with wrong ownership or corruption:

```bash
sudo rm -f /var/lib/mysql/ibtmp1
```

3. Restart MariaDB

```bash
sudo systemctl restart mariadb
sudo systemctl status mariadb -l
```
