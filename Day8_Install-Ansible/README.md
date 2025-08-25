**TASK**

During the weekly meeting, the Nautilus DevOps team discussed about the automation and configuration management solutions that they want to implement. While considering several options, the team has decided to go with Ansible for now due to its simple setup and minimal pre-requisites. The team wanted to start testing using Ansible, so they have decided to use jump host as an Ansible controller to test different kind of tasks on rest of the servers. 

Install ansible version 4.7.0 on Jump host using pip3 only. Make sure Ansible binary is available globally on this system, i.e all users on this system are able to run Ansible commands.

**Steps**

Make sure pip3 is installed

```bash
sudo apt-get update && sudo apt-get install -y python3-pip
```

Installed Ansible 4.7.0 via pip3

Used --prefix=/usr/local so it’s available globally to all users.

```bash
sudo pip3 install ansible==4.7.0
```
Or       

If the system complains about permissions or location, explicitly set install path:

```bash
sudo pip3 install ansible==4.7.0 --upgrade --prefix=/usr/local
```
Ensure Ansible is in PATH for all users

```bash
echo 'export PATH=$PATH:/usr/local/bin' | sudo tee /etc/profile.d/ansible.sh
sudo chmod 755 /etc/profile.d/ansible.sh
```
Then reloaded the profile

```bash
source /etc/profile
```
