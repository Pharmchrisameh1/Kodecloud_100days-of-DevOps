**TASK**

Sarah and Max were working on writting some stories which they have pushed to the repository. Max has recently added some new changes and is trying to push them to the repository but he is facing some issues. Below you can find more details:

SSH into storage server using user max and password Max_pass123. Under /home/max you will find the story-blog repository. Try to push the changes to the origin repo and fix the issues. The story-index.txt must have titles for all 4 stories. Additionally, there is a typo in The Lion and the Mooose line where Mooose should be Mouse.

Click on the Gitea UI button on the top bar. You should be able to access the Gitea page. You can login to Gitea server from UI using username sarah and password Sarah_pass123 or username max and password Max_pass123.

Note: For these kind of scenarios requiring changes to be done in a web UI, please take screenshots so that you can share it with us for review in case your task is marked incomplete. You may also consider using a screen recording software such as loom.com to record and share your work.


**Steps**

ssh max@ststor01

Navigated to the repo

```bash
cd /home/max/story-blog
```

Checked the branch 

```bash
git branch
```

Switched to master

```bash
git checkout master
```

Fetched and synced with remote master before making edits

```bash
git fetch origin
```

```bash
git pull origin master --rebase
```

Fixed Required Issues

Corrected the typo in "The Lion and the Mooose" story file

```bash
vi the-lion-and-the-mooose.txt
```

Changed Mooose to Mouse

Renamed the file

```bash
git mv the-lion-and-the-mooose.txt the-lion-and-the-mouse.txt
```

Fixed story-index.txt to contain all 4 titles

```bash
vi story-index.txt
```

Replaced its contents with this final corrected version:

The Lion and the Mouse
The Frogs and the Ox
The Fox and the Grapes
The Donkey and the Dog


Staged and Commited Fixes

```bash
git add story-index.txt
git add the-lion-and-the-mouse.txt
git commit -m "Fix typo and update story index with all 4 titles"
```

Pushed Changes to Remote

```bash
git push origin master
```
Verified on Gitea UI

Opened the Gitea portal (top bar in the lab environment)

Signed in as max

Opened the story-blog repository and confirmed the story-index.txt shows all 4 titles correctly


