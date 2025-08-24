**TASK**:

A container named kke-container was created by one of the Nautilus project developers on App Server 3. It was solely for testing purposes and now requires deletion. Execute the following task: Delete the kke-container on App Server 3 in Stratos DC.

**Steps**

**SSH into App Server 3**

```bash
ssh banner@stapp03
```

**Check running containers**

```bash
docker ps -a
```

**Look for a container named kke-container**

Stop the container (if running)

```bash
docker stop kke-container
```

**Remove the container**

```bash
docker rm kke-container
```

**Verify it’s gone**

```bash
docker ps -a
```
