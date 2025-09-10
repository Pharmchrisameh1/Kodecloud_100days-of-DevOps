**TASK**

The Nautilus application development team has been working on a project repository /opt/news.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with DevOps team:

Create a new branch datacenter in /usr/src/kodekloudrepos/news repo from master and copy the /tmp/index.html file (present on storage server itself) into the repo. Further, add/commit this file in the new branch and merge back that branch into master branch. Finally, push the changes to the origin for both of the branches.

**Steps**

Changed directory to the working repo

```bash
cd /usr/src/kodekloudrepos/news
```

Created a branch

```bash
sudo git checkout -b datacenter
```

Copied the file

```bash
cp /tmp/index.html .
```

Staged & commit

```bash
sudo git add index.html
sudo git commit -m "Add index.html to datacenter branch"
```

Pused both branches

```bash
sudo git push origin datacenter
sudo git checkout master
sudo git merge datacenter
sudo git push origin master
```







