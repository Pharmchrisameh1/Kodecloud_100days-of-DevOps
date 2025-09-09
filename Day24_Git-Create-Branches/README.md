**TASK**

Nautilus developers are actively working on one of the project repositories, /usr/src/kodekloudrepos/ecommerce. Recently, they decided to implement some new features in the application, and they want to maintain those new changes in a separate branch. Below are the requirements that have been shared with the DevOps team:

On Storage server in Stratos DC create a new branch xfusioncorp_ecommerce from master branch in /usr/src/kodekloudrepos/ecommerce git repo.

Please do not try to make any changes in the code.

**Steps**

Logged in to the Storage server

ssh natasha@ststor01

Navigated to the ecommerce repo

```bash
cd /usr/src/kodekloudrepos/ecommerce
```

Notified the Git this path is safe (avoids “dubious ownership” error)

```bash
git config --global --add safe.directory /usr/src/kodekloudrepos/ecommerce
```

Fixed any leftover root-owned files so natasha can write

```bash
sudo chown -R natasha:natasha /usr/src/kodekloudrepos/ecommerce
```

Ensured we’re on master since task requires the branch be created from master

```bash
git checkout master
```

Created the new branch from master 

```bash
git checkout -b xfusioncorp_ecommerce
```

Verified branches

```bash
git branch
```
Output:

xfusioncorp_ecommerce

  master





