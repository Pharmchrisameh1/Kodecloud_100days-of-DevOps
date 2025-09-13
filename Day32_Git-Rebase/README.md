**TASK**

The Nautilus application development team has been working on a project repository /opt/cluster.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with DevOps team:

One of the developers is working on feature branch and their work is still in progress, however there are some changes which have been pushed into the master branch, the developer now wants to rebase the feature branch with the master branch without loosing any data from the feature branch, also they don't want to add any merge commit by simply merging the master branch into the feature branch. Accomplish this task as per requirements mentioned.

Also remember to push your changes once done.

**Steps**

ssh natasha@ststor01

Entered the cloned repo

```bash
cd /usr/src/kodekloudrepos/cluster
```

Marked the repo safe to avoid ownership errors

```
git config --global --add safe.directory /usr/src/kodekloudrepos/cluster
```

Ensured the latest updates were available

```bash
sudo git fetch --all
```

Switched to the feature branch

```bash
sudo git checkout feature
```

Rebased feature branch with master

```bash
sudo git rebase master
```

Pushed updated feature branch back to origin

```bash
sudo git push origin feature --force
```

