**TASKS**

The xFusionCorp development team added updates to the project that is maintained under /opt/media.git repo and cloned under /usr/src/kodekloudrepos/media. Recently some changes were made on Git server that is hosted on Storage server in Stratos DC. The DevOps team added some new Git remotes, so we need to update remote on /usr/src/kodekloudrepos/media repository as per details mentioned below:

a. In /usr/src/kodekloudrepos/media repo add a new remote dev_media and point it to /opt/xfusioncorp_media.git repository.

b. There is a file /tmp/index.html on same server; copy this file to the repo and add/commit to master branch.

c. Finally push master branch to this new remote origin.


**Steps**

ssh natasha@ststor01

Navigated to the cloned repo

```bash
cd /usr/src/kodekloudrepos/media
```

Marked the repo safe

```bash
git config --global --add safe.directory /usr/src/kodekloudrepos/media
```

Added the new remote

```bash
sudo git remote add dev_media /opt/xfusioncorp_media.git
```

Verified it was added

```bash
git remote -v
```

Copied the index.html file into repo

```bash
sudo cp /tmp/index.html . 
```

Staged the file

```bash
sudo git add index.html 
```

Set Git identity

```bash
git config --global user.name "natasha" 
git config --global user.email "natasha@ststor01.stratos.xfusioncorp.com"
```

Commited the file

```bash
sudo git commit -m "Add index.html to master branch" 
```

Marked the remote repo safe to fix prospective push error for /opt

```bash
git config --global --add safe.directory /opt/xfusioncorp_media.git 
```

Pushed master branch to the new remote

```bash
sudo git push dev_media master
```
