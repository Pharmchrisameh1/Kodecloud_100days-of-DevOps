**Task**:

As part of the temporary assignment to the Nautilus project, a developer named javed requires access for a limited duration. To ensure smooth access management, a temporary user account with an expiry date is needed. Here's what you need to do:


Create a user named javed on App Server 2 in Stratos Datacenter.

Set the expiry date to 2024-01-28, ensuring the user is created in lowercase as per standard protocol.

**Steps**

```bash
ssh steve@stapp02
```
**Create the user with an expiry date**:

```bash
sudo useradd -e 2024-01-28 javed
```

**Verify that the account was created with the correct expiry date**:

```bash
sudo chage -l javed
```
