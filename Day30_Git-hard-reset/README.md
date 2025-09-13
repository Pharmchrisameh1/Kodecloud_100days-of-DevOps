**TASK**

The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/blog present on Storage server in Stratos DC. This was just a test repository and one of the developers just pushed a couple of changes for testing, but now they want to clean this repository along with the commit history/work tree, so they want to point back the HEAD and the branch itself to a commit with message add data.txt file. Find below more details:

In /usr/src/kodekloudrepos/blog git repository, reset the git commit history so that there are only two commits in the commit history i.e initial commit and add data.txt file.

Also make sure to push your changes.

**Steps**

ssh natasha@ststor01

Navigated to the repo

```bash
cd /usr/src/kodekloudrepos/blog
```


Marked the repo as safe to avoid Git ownership errors

```bash
git config --global --add safe.directory /usr/src/kodekloudrepos/blog
```

Checked commit history

```bash
git log --oneline
```
Output: 

380c5e1 (HEAD -> master, origin/master) Test Commit10
8aef733 Test Commit9
fb08c66 Test Commit8
aac8ad5 Test Commit7
fbe0456 Test Commit6
f670db3 Test Commit5
60e28e2 Test Commit4
34e25c0 Test Commit3
5fb112e Test Commit2
e85d97d Test Commit1
b4ee7f2 add data.txt file
ef4256a initial commit


Rebased from the root and deleted all the commits except " ef4256a initial commit
b4ee7f2" and "add data.txt file"

```bash
sudo git rebase -i --root
```

Force pushed cleaned history

```bash
sudo git push origin master --force
```

Then verified

```bash
git log --oneline
```

