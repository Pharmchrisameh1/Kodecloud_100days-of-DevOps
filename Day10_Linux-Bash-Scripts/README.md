**TASK**

The production support team of xFusionCorp Industries is working on developing some bash scripts to automate different day to day tasks. One is to create a bash script for taking websites backup. They have a static website running on App Server 2 in Stratos Datacenter, and they need to create a bash script named blog_backup.sh which should accomplish the following tasks. (Also remember to place the script under /scripts directory on App Server 2). 

a. Create a zip archive named xfusioncorp_blog.zip of /var/www/html/blog directory. 

b. Save the archive in /backup/ on App Server 2. This is a temporary storage, as backups from this location will be clean on weekly basis. Therefore, we also need to save this backup archive on Nautilus Backup Server. 

c. Copy the created archive to Nautilus Backup Server server in /backup/ location. 

d. Please make sure script won't ask for password while copying the archive file. 
Additionally, the respective server user (for example, tony in case of App Server 1) must be able to run it.

**Steps**
```
Login to App Server 2

```bash
ssh steve@stapp02
```
Ensured zip package is installed

```bash
yum install -y zip
```
Created the script file

```bash
vi /scripts/media_backup.sh
```

Added the following content

#!/bin/bash

# Created /backup if it does not exist
mkdir -p /backup

# Created zip archive of the media website
zip -r /backup/xfusioncorp_media.zip /var/www/html/media

# Copied the archive to Nautilus Backup Server (stbkp01)
scp /backup/xfusioncorp_media.zip clint@stbkp01:/backup/

# Check status
if [ $? -eq 0 ]; then
    echo "Backup successful! File copied to stbkp01:/backup/xfusioncorp_media.zip"
else
    echo "Backup failed!"
fi



Gave execute permissions

```bash
chmod +x /scripts/media_backup.sh
```

Set up passwordless SSH to backup server

```bash
ssh-keygen -t rsa -b 2048 -f ~/.ssh/id_rsa -N ""
ssh-copy-id clint@stbkp01
```

Tested:

```bash
ssh clint@stbkp01
```
exit

Run the script

```bash
/scripts/media_backup.sh
```

Ouptput:

Backup successful! File copied to stbkp01:/backup/xfusioncorp_media.zip


With this setup:

media_backup.sh exists under /scripts on App Server 2.


It zips /var/www/html/media → /backup/xfusioncorp_media.zip.


It copies the archive to /backup/ on Nautilus Backup Server (stbkp01).


SSH keys ensure no password prompt.


steve (App Server 2 user) can run the script directly.


