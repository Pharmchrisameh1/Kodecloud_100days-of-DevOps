**TASK**

A python app needed to be Dockerized, and then it needs to be deployed on App Server 2. We have already copied a requirements.txt file (having the app dependencies) under /python_app/src/ directory on App Server 2. Further complete this task as per details mentioned below:

Create a Dockerfile under /python_app directory:

Use any python image as the base image.

Install the dependencies using requirements.txt file.

Expose the port 8085.

Run the server.py script using CMD.

Build an image named nautilus/python-app using this Dockerfile.

Once image is built, create a container named pythonapp_nautilus:

Map port 8085 of the container to the host port 8093.

Once deployed, you can test the app using curl command on App Server 2.

curl http://localhost:8093/


**Steps**

ssh steve@stapp02

Created the Dockerfile

```bash
cd /python_app

sudo vi Dockerfile
```

Built the Docker image

```bash
sudo docker build -t nautilus/python-app /python_app
```

Ran the container

```bash
sudo docker run -d --name pythonapp_nautilus -p 8093:8085 nautilus/python-app
```

Tested the app

```bash
curl http://localhost:8093/
```




