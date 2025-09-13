**TASK**

The Nautilus application development team was working on a git repository /opt/ecommerce.git which is cloned under /usr/src/kodekloudrepos directory present on Storage server in Stratos DC. The team want to setup a hook on this repository, please find below more details:

Merge the feature branch into the master branch`, but before pushing your changes complete below point.

Create a post-update hook in this git repository so that whenever any changes are pushed to the master branch, it creates a release tag with name release-2023-06-15, where 2023-06-15 is supposed to be the current date. For example if today is 20th June, 2023 then the release tag must be release-2023-06-20. Make sure you test the hook at least once and create a release tag for today's release.

Finally remember to push your changes.
Note: Perform this task using the natasha user, and ensure the repository or existing directory permissions are not altered.

**Steps**

ssh natasha@ststor01

Entered the cloned repo

```bash
cd /usr/src/kodekloudrepos/ecommerce
```

Merged the feature branch into master

```bash
sudo git checkout master
sudo git pull origin master        
sudo git merge feature
```

Created the post-update hook in the bare repo

```bash
cd /opt/ecommerce.git/hooks
vi post-update
```

Made the file executable

```bash
sudo chmod +x post-update
```

Navigated back to the local repository and pushed the merge to trigger the hook

```bash
cd /usr/src/kodekloudrepos/ecommerce
sudo git push origin master
```
