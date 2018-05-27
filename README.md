# Django-Portfolio
Nice Portfolio with Python Django 2.0.2

### Step by Step - How to build your own portfolio with Django.

**Here some of the commands we will use for this project:**

**Creating virtual environment (Mac)**

``pip3 install virtualenv``

**Creating a new project**
   
```django-admin startproject projectname```

**Add an app to a project**

```python3 manage.py startapp appname```

**Starting the server**

``python3 manage.py runserver``

**Creating migrations**

``python3 manage.py makemigrations``

**Migrate the database**

``python3 manage.py migrate``

**Creating a Super User for the admin panel**

``python3 manage.py createsuperuser``

**Collecting static files into one folder**

``python3 manage.py collectstatic``

    
# The following instructions response to Mac OS

**Let's start our project**

Create a folder called ``Django-Project``

``cd Django-Project``

To install virtualenv type. 

``pip3 install virtualenv`` Here I am assuming you have pip3 installed.

Create a virtual environment

``virtualenv myenv``

Activate your virtual environment

`` source myenv/bin/activate ``

You should see something like this: ``(myenv) yourmachina:Django-Project yourusername$``

**Note** if you want to get out from your environment type: ``deactivate``

**Now let's create our Django project**

``django-admin startproject portfolio``

At this point you should see this tree:

```
portfolio/
├── manage.py
└── portfolio
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

If you see we have 2 folders called portfolio and this could cause confusion.

Let's rename the first folder as ``portfolio-project``

You can achieve this typing: ``mv portfolio/ portfolio-project``

Now you should have something like this:

```
portfolio-project/
  ├── manage.py
  └── portfolio
      ├── __init__.py
      ├── settings.py
      ├── urls.py
      └── wsgi.py
```

Is time to install Django

``pip install django==2.0.2`` 

Notice we are not using ``pip3`` but ``pip`` this is due to we are inside the our environment.

Now is important to know which files we have to send to our repository.

Create ``.gitignore`` file.

``vim .gitignore``

if you go to ``https://www.gitignore.io/`` type Django and will give you a basic 
gitignore files for a Django project.

To this point I have something like this:

```
### Django ###
*.log
*.pot
*.pyc
__pycache__/
local_settings.py
db.sqlite3
/media
/static
```
We will be modifying this file during the project

Now let's run our python django server

``cd portfolio-project``

``python manage.py runserver``

**Notice** again we are not using ``python3 manage.py runserver`` as I mention in the top
and this is because We are inside our environment.

We would use ``python3 manage.py runserver`` if we had used ``pipenv`` only and not 
``virtualenv``

You should see something like this

```
May 27, 2018 - 18:00:55
Django version 2.0.2, using settings 'portfolio.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

Open your browser and paste ```http://127.0.0.1:8000/```

At this point you should see the basic Django app 

**!!Congratulations!!**

If everything have gone well so far then you should see now this tree

````
portfolio-project/
├── db.sqlite3
├── manage.py
└── portfolio
    ├── __init__.py
    ├── __pycache__
    │   ├── __init__.cpython-36.pyc
    │   ├── settings.cpython-36.pyc
    │   ├── urls.cpython-36.pyc
    │   └── wsgi.cpython-36.pyc
    ├── settings.py
    ├── urls.py
    └── wsgi.py
````

Now we can see more files like  ``db.sqlite3`` etc..

# Let's get into Django lands

How Django structure a website is: the top level is Django project and a project is composed by several apps

**Ex.** Our project is called ``portfolio`` but beside we will have apps related to this project like ``blog`` 
so ``blog`` is and app that belongs to the ``portfolio`` project.

**This is extremely important to understand because is the way Django framework thinks.** 

```
project/
    ├── blogApp
    ├── portfolioApp
    └── storeApp
```
These apps belong to a one project and can be reused in other projects.
















