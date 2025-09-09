**TASK**

The Nautilus development team has provided requirements to the DevOps team for a new application development project, specifically requesting the establishment of a Git repository. Follow the instructions below to create the Git repository on the Storage server in the Stratos DC:

Utilize yum to install the git package on the Storage Server.

Create a bare repository named /opt/ecommerce.git (ensure exact name usage).

**Steps**

Logged into the Storage Server

ssh natasha@ststor01

Installed Git using yum

```bash
sudo yum install -y git
```

Verified Git is installed

```bash
git --version
```

Created the bare repo at /opt/ecommerce.git

```bash
sudo git init --bare /opt/ecommerce.git
```
Confirmed the repo exists

```bash
ls -ld /opt/ecommerce.git
cd /opt/ecommerce.git
ls
```




