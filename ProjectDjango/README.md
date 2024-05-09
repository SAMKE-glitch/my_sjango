Create Your First Django Project
Before starting the lab, make sure your current directory is /home/project.

Install these must-have packages and setup the environment.

pip install --upgrade distro-info
pip3 install --upgrade pip==23.2.1
pip install virtualenv
virtualenv djangoenv
source djangoenv/bin/activate

First, we need to install Django related packages.

Go to terminal and run:
pip install Django

Once the installation is finished, you can create your first Django project by running:
django-admin startproject firstproject

A folder called firstproject will be created which is a container wrapping up settings and configurations for a Django project.

If your current working directory is not /home/project/firstproject, cd to the project folder
cd firstproject

and create a Django app called firstapp within the project
python3 manage.py startapp firstapp

Django created a project scaffold for you containing your first firstapp app.

Your CloudIDE workspace should look like the following:


The scaffold contains the fundamental configuration and setting files for a Django project and app:

For project-related files:

manage.py is a command-line interface used to interact with the Django project to perform tasks such as starting the server,
migrating models, and so on.
firstproject/settings.py contains the settings and configurations information.
firstproject/urls.py contains the URL and route definitions of your Django apps within the project.
For app-related files:

firstapp/admin.py: is for building an admin site
firstapp/models.py: contains model classes
firstapp/views.py: contains view functions/classes
firstapp/urls.py: contains URL declarations and routing for the app
firstapp/apps.py: contains configuration meta data for the app
firstapp/migrations/: model migration scripts folder
Before starting the app, you will to perform migrations to create necessary database tables:
python3 manage.py makemigrations

and run migration


python3 manage.py migrate

Then start a development server hosting apps in the firstproject:
python3 manage.py runserver

To see your first Django app from Theia,

Click on the Skills Network button on the left, it will open the “Skills Network Toolbox”. Then click the Other then Launch Application. From there you should be able to enter the port 8000 and launch.

When developing Django apps, in most cases Django will automatically load the updated files and restart the development server. However, it might be safer to restart the server manually if you add/delete files in your project.

Let's try to stop the Django server now by pressing:

Control + C or Ctrl + C in the terminal
