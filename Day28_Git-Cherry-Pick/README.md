**TASK**

The Nautilus application development team has been working on a project repository /opt/media.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with the DevOps team:

There are two branches in this repository, master and feature. One of the developers is working on the feature branch and their work is still in progress, however they want to merge one of the commits from the feature branch to the master branch, the message for the commit that needs to be merged into master is Update info.txt. Accomplish this task for them, also remember to push your changes eventually.

**Steps**

Logged into the storage server

ssh natasha@ststor01

Navigated to the cloned repo

```bash
cd /usr/src/kodekloudrepos/media
```

Marked the repo as safe to avoid ownership errors

```bash
git config --global --add safe.directory /usr/src/kodekloudrepos/media
```

Ensured both branches were there locally

```bash
sudo git fetch --all 
```

Switched to master branch

```bash
sudo git checkout master 
```

Identified the commit hash on 'feature' with message "Update info.txt"

```bash
git log feature --oneline | grep "Update info.txt"
```
 Output:

4070450 Update info.txt


Then cherry-picked the commit into master

```bash
sudo git cherry-pick 4070450 
```

Pushed the updated master to origin (/opt/media.git)

```bash
sudo git push origin master 
```
