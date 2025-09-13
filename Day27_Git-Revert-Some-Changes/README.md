**TASKS**

The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/apps present on Storage server in Stratos DC. However, they reported an issue with the recent commits being pushed to this repo. They have asked the DevOps team to revert repo HEAD to last commit. Below are more details about the task:

In /usr/src/kodekloudrepos/apps git repository, revert the latest commit ( HEAD ) to the previous commit (JFYI the previous commit hash should be with initial commit message ).

Use revert apps message (please use all small letters for commit message) for the new revert commit.

**Steps**

Logged in to the storage server

ssh natasha@ststor01

Moved into the repo

```bash
cd /usr/src/kodekloudrepos/apps
```

Marked the repo as safe and avoided dubious ownership error

```bash
git config --global --add safe.directory /usr/src/kodekloudrepos/apps
```

Viewed commits and confirmed HEAD and initial commit exists

```bash
git log --oneline
```

Reverted the latest commit (HEAD)

```bash
sudo git revert HEAD --no-edit
```

Amended the revert commit message to match checker requirement

```bash
sudo git commit --amend -m "revert apps"
```

Confirmed the last 2 commits

```bash
git log --oneline | head -2
```
