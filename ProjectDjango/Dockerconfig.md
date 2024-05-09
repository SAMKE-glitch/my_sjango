Containerizing the app using Docker
Docker is a powerful tool that makes it easy to run applications regardless of the machine you wrote the code on and the machine you want to run it on. It is widely used in practice as it allows developers to avoid the “But it runs on my laptop!” problem when their code doesn’t work.

You will need to install Docker first from this link(https://docs.docker.com/desktop/) if you are working locally.

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



Now lets start working with Docker.
First we need to create the requirements.txt file, which we use to tell Docker what python packages it needs to install. Run the following command in the main /firstproject folder.

pip install pipreqs
pipreqs .


Next, we want to create a Dockerfile which instructs Docker how to build your application (in the same directory):

Run the following command to create an empty Dockerfile
touch Dockerfile


Then open the newly created Dockerfile and copy the following contents to it.

# syntax=docker/dockerfile:1
FROM python:3
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
WORKDIR /code
COPY requirements.txt /code/
RUN pip install -r requirements.txt
COPY . /code/
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]


The code above will be run line by line. The FROM line indicates what base container image we want to build on, and in this case we want to use a python 3 image. You can find more details on how this code works here.

Now we can run the following command to create and run the container image:

docker build . -t my-django-app:latest && docker run -e PYTHONUNBUFFERED=1 -p  8000:8000 my-django-app 


You should see something like:
docker-c-up

You can launch the application the same way you have previously in this project as well, through Launch Application and specifying port 8000.

Alternatively, you can launch the application directly by clicking on this button


Checker this link https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/django/ and see The code above will be run line by line. The FROM line indicates what base container image we want to build on, and in this case we want to use a python 3 image. You can find more details on how this code works here.




Deploying to Code Engine
If you would like to host your application and have it be available for anyone to use, you can follow these steps in order to deploy it. The deployment will be to IBM Cloud’s Code Engine. IBM Cloud Code Engine is a fully managed, cloud-native service for running containerized workloads on IBM Cloud. It allows developers to deploy and run code in a secure, scalable and serverless environment, without having to worry about the underlying infrastructure.

The following steps in Part 1 allow you to test deploy to a IBM Skills Network Code Engine environment to test if everything is working just fine, which is deleted after a few days. Part 2 shows the steps to deploy for real to your own account.

Part 1: Deploying to Skills Network Code Engine
Step 1. Create Code Engine Project
In the left hand navigation pannel, there is an option for the Skills Network Toolbox. Simply open that and that expand the CLOUD section and then click on Code Engine. Finally cick on Create Project


