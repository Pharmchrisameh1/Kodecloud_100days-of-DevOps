**TASK**

The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure the thor user on jump host has password-less SSH access to all app servers through their respective sudo users (i.e tony for app server 1).

Based on the requirements, perform the following:

Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.

**Steps**

Generated an SSH key pair

```bash
ssh-keygen -t rsa -b 2048
```

Pressed Enter for all prompts (use default file path ~/.ssh/id_rsa and no passphrase).

Copied the public key to each App Server’s sudo user

Used ssh-copy-id to push thor’s public key to the sudo user on each app server.

```bash
ssh-copy-id tony@stapp01
```
```bash
ssh-copy-id steve@stapp02
```
```bash
ssh-copy-id banner@stapp03
```
Entered the password for each sudo user when prompted

Tested the password-less access

From jump host as thor:

```bash
ssh-copy-id tony@stapp01
```
```bash
ssh-copy-id steve@stapp02
```
```bash
ssh-copy-id banner@stapp03
