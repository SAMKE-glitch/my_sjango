Containerizing the app using Docker
Docker is a powerful tool that makes it easy to run applications regardless of the machine you wrote the code on and the machine you want to run it on. It is widely used in practice as it allows developers to avoid the “But it runs on my laptop!” problem when their code doesn’t work.

You will need to install Docker first from this link if you are working locally.

This is how it works for (basic) python applications:

Create a requirements.txt file
Create a Dockerfile which contains instructions on how to build a Docker image
Run docker compose up to create a container image, and run it
Commit and push the image to a remote repo so others can run it exactly as you’ve configured!
Docker images are commonly used in conjunction with Kubernetes, which is a service that manages containers.

You will be briefly introduced to how you can setup this Django application to run using Docker.

Before going into the technical stuff revolving around Docker, we just need to make one final change to our codebase. By deafult, django is configured to block all traffic from all hosts including the traffic coming from CloudIDE until we explicity define in them in settings.py.

Therefore, open the setting.py file and change the ALLOWED_HOSTS = [] code to:
ALLOWED_HOSTS = ['*','.us-south.codeengine.appdomain.cloud']
