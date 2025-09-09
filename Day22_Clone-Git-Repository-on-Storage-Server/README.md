**TASK**

The DevOps team established a new Git repository last week, which remains unused at present. However, the Nautilus application development team now requires a copy of this repository on the Storage Server in the Stratos DC. Follow the provided details to clone the repository:

The repository to be cloned is located at /opt/beta.git

Clone this Git repository to the /usr/src/kodekloudrepos directory. Perform this task using the natasha user, and ensure that no modifications are made to the repository or existing directories, such as changing permissions or making unauthorized alterations.

**Steps**

ssh natasha@ststor01

Navigated to the target directory

```bash
cd /usr/src/kodekloudrepos
```

Cloned the repository as natasha

```bash
git clone /opt/beta.git
```

Then verified

```bash
ls -ld /usr/src/kodekloudrepos/beta
ls -lah /usr/src/kodekloudrepos/beta
```

Navigated into the repo directory

```bash
cd /usr/src/kodekloudrepos/beta
```

Confirmed the status

```bash
git status
```

Double confirmed the remote origin points to the right place

```bash
git remote -v
```
Output: 
origin  /opt/beta.git (fetch)
origin  /opt/beta.git (push)


