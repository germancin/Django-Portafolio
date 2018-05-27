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

**Ex.** Our project is called ``portfolio`` but beside we will have apps related to this project like ``blog`` and ``jobs``  
so ``blog`` and ``jobs`` are the apps which belong to the ``portfolio`` project.

**This is extremely important to understand because is the way Django framework thinks.** 

```
project/
    ├── blogApp
    ├── portfolioApp
    └── storeApp
```
These apps belong to a one project and can be reused in other projects.

** That been said let's create our first app.**

### Creating our first APP

Be sure you are inside our folder ``portfolio-project`` then...

``python manage.py startapp blog``

And

``python manage.py startapp jobs``

So now the structure so far should look like this

```
portfolio-project/
├── blog
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
├── db.sqlite3
├── jobs
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
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
```

As you can see we have 2 new folders "Apps" ``blog`` and ``jobs`` these are our new apps.

To simplify the view we should have this structure

```
portfolio-project/
            ├── blog
            ├── db.sqlite3
            ├── jobs
            ├── manage.py
            └── portfolio
```
If you haven't commit this is a good moment to do it.

# Let's talk about Models and Databases.

Django give us several other apps we can interact with out of the box
apps like Admin, Users, Sessions etc.. these let us manipulate our Database
within a visual UI and the way of activate this is:

Lets locate where the manage.py file is at and type.

```python manage.py migrate```

This what would do is creating the all the objects related to users, sessions, and admin

After running the above you should see this:

```
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK
```

Now go to your browser and paste ``` http://127.0.0.1:8000/admin/``` you should see the following UI

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/admin.png" alt="admin-ui" width="555" >

If you can see this **!!congratulations!!**

So far we just activate the Admin section which will let us manage our information related to our project.

**The next step is create a SUPERUSER and its credentials to be able to interact with the database**

``python manage.py createsuperuser``

After this you should be getting a prompt to add user, email and password

```
(myenv) machina:portfolio-project user$ python manage.py createsuperuser
Username (leave blank to use 'germangonzalez'): germancin
Email address: elmaildegerman@gmail.com
Password:
Password (again):
Superuser created successfully.
```
Go back to your browser and paste ``http://127.0.0.1:8000/admin/``

Insert your just created credentials and access to the front page of the admin

You should see this

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/admin-front.png" alt="admin-ui"  >

But now we have to create a database/tables/objects for our jobs app in order to 
dynamically add new jobs and automatically be populated in our page.

So there are several things we have to be aware of

    1. We have to create our models within each app
    2. We have to connect our model app to our project
    3. We have also to connect our whole app to our main project
    4. After all of this We need to migrate this new created models
    
**So let's create our model**
Here basically we are setting the fields of the jobs "table"

In order to do that lets open the models.py file located at jobs app

``jobs/models.py``

The file looks like this in the beginning

```
from django.db import models

# Create your models here.
```

Here what are we going to do is adding the fields we will be filling up as information for our jobs

Let's create a python class called ``Job``

```python
from django.db import models

# This will allow us to create class called job with all the functionality that we need to save
# this object into the database
class Job(models.Model):
    image = models.ImageField(upload_to = 'images/')
    sumary = models.CharField(max_length=400, ${blank=True, null=True})
    technology = models.CharField(max_length=400, ${blank=True, null=True})
```

You can go here: https://docs.djangoproject.com/en/2.0/ref/models/fields/#field-types
and check more about Field Types


After this we have to connect our ``Jobs`` App to our project and we do that going to 
the project folder ``portfolio`` and open file called ``settings.py`` 

look for this section
```python

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

```angular2html

Here we are going to add our apps so our project knows about the existence of these ones
Also you can see in this piece of code that we have admin, auth, sessions, messages etc..
well these are the apps that Django give us out of the box and if you won't need some of them then you can delete them
but for this project we will use them so what we have to do is adding the job app.
So our code will look like this after adding it.

```

```python
INSTALLED_APPS = [
    'jobs.apps.JobsConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

```

So what ```'jobs.apps.JobsConfig',``` means is 

the first part ``jobs`` is the name of our app 

then `apps` is making reference to the ``apps.py`` file

And `JobsConfig` if you open the file ``apps.py `` you'll see a auto generated ``class`` by Django called ```JobsConfig```


Also we have to set where our ``media/images`` files are going to be saved so at the end 
of this same ``settings.py`` file add this

```python
# This is how Django knows where to save
MEDIA_ROOT = os.path.join(BASE_DIR, 'resources')

# This is how we will call it in our app
MEDIA_URL = '/resources/'
```



There you have now We have to run 





Now all the image are going to be saved in one single place of source so maje sure to create the folder
