**Day 1 of 100 days of DevOps**

Linux User Setup with Non-Interactive Shell:
To accommodate the backup agent tool's specifications, the system admin team at xFusionCorp Industries requires the creation of a user with a non-interactive shell. 
Here's your task: Create a user named siva with a non-interactive shell on App Server 2.

For a **non-interactive shell** user in Linux (meaning they can’t log in interactively), one can use /usr/sbin/nologin or /bin/false as their shell.

# Step 1: SSH into App Server2
ssh steve@stapp02

# Step 2: Created the user with a non-interactive shell
sudo useradd -m -s /usr/sbin/nologin siva
# Rationale:
-m → create the home directory /home/siva.

-s /usr/sbin/nologin → sets the shell so the user can’t log in interactively.
# Verification:
run the command:

getent passwd siva

Output of the command:

siva:x:UID:GID::/home/siva:/usr/sbin/nologin
