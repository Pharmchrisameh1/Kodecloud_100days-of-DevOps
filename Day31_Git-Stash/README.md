**TASK**

The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/official present on Storage server in Stratos DC. One of the developers stashed some in-progress changes in this repository, but now they want to restore some of the stashed changes. Find below more details to accomplish this task:

Look for the stashed changes under /usr/src/kodekloudrepos/official git repository, and restore the stash with stash@{1} identifier. Further, commit and push your changes to the origin.


**Steps**

ssh natasha@ststor01

Entered the repository

```bash
cd /usr/src/kodekloudrepos/official
```

Marked the repo as safe to avoid “dubious ownership” error

```bash
git config --global --add safe.directory /usr/src/kodekloudrepos/official
```

Checked the list of stashes

```bash
sudo git stash list
```

Applied the correct stash

```bash
sudo git stash apply stash@{1}
```

Staged the restored changes

```bash
sudo git add .
```

Commited with a message

```bash
sudo git commit -m "Restore stash@{1} changes"
```

Then Pushed to origin

```bash
sudo git push origin master
```

