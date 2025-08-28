**TASK**

We have one of our websites up and running on our Nautilus infrastructure in Stratos DC. Our security team has raised a concern that right now Apache’s port i.e 6400 is open for all since there is no firewall installed on these hosts. So we have decided to add some security layer for these hosts and after discussions and recommendations we have come up with the following requirements: 

1. Install iptables and all its dependencies on each app host. 

2. Block incoming port 6400 on all apps for everyone except for LBR host. 

3. Make sure the rules remain, even after system reboot.

**Steps**

```bash
ssh tony@stapp01
```

```bash
sudo yum install -y iptables-services

sudo systemctl enable --now iptables
```
Flushed existing rules

```bash
sudo iptables -F
```
Allowed loopback traffic

```bash
sudo iptables -A INPUT -i lo -j ACCEPT
```
Allowed established and related connections

```bash
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```
Allowed  traffic from LBR host (172.16.238.14) to port 6400

```bash
sudo iptables -A INPUT -p tcp -s 172.16.238.14 --dport 6400 -j ACCEPT
```
Blocked everyone else from accessing port 6400

```bash
sudo iptables -A INPUT -p tcp --dport 6400 -j DROP
```
Saved the changes made

```bash
sudo service iptables save
```

```bash
sudo systemctl restart iptables
```

The same procedures above were repeated for server2 and server3 respectively
