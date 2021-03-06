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

**That been said let's create our first app.**

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

Django give us several other apps we can interact with 
like Admin, Users, Sessions etc.. these let us manipulate our Database
within a visual interface and the way of activate this is:

Lets locate where the manage.py file is at and type.

```python manage.py migrate```

What this would do is creating all the objects related to users, sessions, and admin

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

If you can see that **!!congratulations!!**

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

# Let's work on our first App (Jobs)
Now we have to create a database/tables/objects for our jobs app in order to 
dynamically add new jobs and automatically be populated in our page.

So there are several things we have to be aware of

    1. We have to create our models within each app
    2. We have to connect our model app to our project
    3. We have also to connect our whole app to our main project
    4. After all of these We need to migrate this new created models
    
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
    sumary = models.CharField(max_length=400)
    technology = models.CharField(max_length=400)
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

Before hit migrations we have to install ``Pillow`` so we can handle images

```pip install Pillow```

There you have now run

``` python manage.py makemigrations ``` 

You should get this

```angularjs
Migrations for 'jobs':
  jobs/migrations/0001_initial.py
    - Create model Job
```

After this we have to register our job app in the admin

Go to the the folder ``jobs/admin.py`` and add this code 

```python
from django.contrib import admin

# import the Job class
from .models import Job

# register the Job class into Admin section
admin.site.register(Job)
```

Now let's test this going to our app paste ``http://127.0.0.1:8000/admin/``

You should see this

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/admin-jobs.png" alt="admin-jobs"  >

As you see there now we have the Jobs Object and from here we can execute any CRUD action

If you find any problem with migrations and decide to re-do everything you can follow this article very usefull
https://simpleisbetterthancomplex.com/tutorial/2016/07/26/how-to-reset-migrations.html

# Let's set the media/resources images

We have to go to the ``urls.py`` file on our project folder ``portfolio``
and look for this pice of code

```python
urlpatterns = [
    path('admin/', admin.site.urls),
]
```

We need to modify this piece of code and should end it up like this

```python
# must import settings
from django.conf import settings
# must import static
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

```

# Let's move to POSTGRES

**Why moving to postgress?**

Well in a local environment sqlite works just fine but if we want to take this to production then 
we better use a more robust DB to handle a vast amount of work.

Go to https://postgresapp.com/ for MAC and Download the app

Open it and initiate it 

then select the postgres DB and it will open a terminal

type: ``\password postgres``

enter your password

then create a database so for this project we will create a database called ``portfoliodb``

type: ``CREATE DATABASE portfoliodb;``

And this is it we won't need to come back to this app

**Let's update setting.py**

Open ``settings.py`` and look for the piece of code ``DATABASES`` that looks like this

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```

Your code now have to looks like this

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'portfoliodb',
        'USER': 'postgres',
        'PASSWORD': 'secure123',
        'HOST':'127.0.0.1',
        'PORT':'5432',
    }
}
```

Now we need to install ``psycopg2`` in order to communicate with our DB

``pip install psycopg2-binary``

Then you will have to migrate the models to the mew postgresdb 

``python manage.py migrate``

We will have to re-create the SUPERUSER so run 

```python manage.py createsuperuser```

After this run server and should be working normally

if so **!!congratulations!!**

# Go and create Blog

**Follow the same steps above as practice**

Here are the steps:

```angularjs
    1. Create a Blog models
    2. Add the BLog app to the settings
    3. Create a migration
    4. Migrate
    5. Add to the Admin
```
You can check the commits as I was creating the steps above:

**1. Create a Blog models**

https://github.com/germancin/Django-Portfolio/commit/4f6bd8fd8c76a31e55b6fab9a802d908d14ddb6e
     
**2. Add the BLog app to the settings**

``'blog.apps.BlogConfig'``

**3. Create a migration** make sure to be placed at hte level of ``manage.py`` file

``python manage.py makemigrations``

You should see this in your terminal:
```angularjs
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model Blog
```
**4. Migrate**

``python manage.py migrate``

You should see this in your terminal:
```angularjs
Operations to perform:
  Apply all migrations: admin, auth, blog, contenttypes, jobs, sessions
Running migrations:
  Applying blog.0001_initial... OK
```

**5. Add to the Admin**

Go to ``blog/admin.py`` and add 

```python
from .models import Blog

admin.site.register(Blog)
```

Now go to your admin section and you should see the Blog object:

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/admin-blog.png" alt="admin-blog" />

If you try to add a new record for blog should look like this:

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/admin-blog-add.png" alt="admin-blog-add" />

**!!Congratulations!!**

# It's time for our home page

To do things quite different we are going to add our home page into the blog app since 
this is the most important app in our project so to achieve this we will have to go to 
the jobs app to the ``views.py`` file and add some code there.

So add this code and I explain what this is

```python
from .models import Job

def home(request):
    jobs = Job.objects
    return render(request, 'jobs/home.html')
```
As we can see there is a class called ``home`` which we'll call it from the ``urlpatterns`` section in our ``urls.py`` file
so let's do that.

In ``urls.py`` file first we have to import ``import jobs.views`` and after that your ``urlpatterns`` list should look like this

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', jobs.views.home, name='home-page'),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
``` 

so we added  ``path('', jobs.views.home, name='home-page'),``

where ``jobs.views.home`` job.views is the obviously views from jobs and the .home is the class we just create.

``name='home-page'`` name is just the identifier to called later in the urls.


**Create the home.html**

Go to the jobs app and create the template with a home.html

your folder structure should look like this

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/jobs-template.png" />

Now add some html into the ``home.html`` file and we should now have a home page.


# Bootstrap integration for a nice looking portfolio

**Let's integrate bootstrap in our Django project**

Go to https://getbootstrap.com/docs/4.1/examples/album/ 

Go to the code behind Copy and Paste it in our just created ``home.html``
and later we will start replacing the elements with a dynamic info.

Now we need to replace the urls of the bootstrap files and in this case for simplicity we will use the CDN (Content Delivery Network)

So go to the home page of the bootstrap site: https://getbootstrap.com
and look for the CDN section and copy the required links.
 
You can see this commit 

https://github.com/germancin/Django-Portfolio/commit/4d667026db6e6b529eddcaece950869ee1769f42

just make sure to change the info in the bottom and the top message.

# Let's add the jobs to our home

Django makes this extremely easy 

In our ``jobs/views.py`` we already already called the Job model like this 
``from .models import Job`` 

and right after the home class we have ``jobs = Job.objects`` so what iis happening here is we are getting the objects from Job and assigning it to the jobs variable

and now we are going to pass this whole object to the request so we wil end it up with a code like this

```python
from django.shortcuts import render
from .models import Job

def home(request):
    jobs = Job.objects
    return render(request, 'jobs/home.html', {'jobs':jobs})
```

Now we can go to ``home.html`` and loop it up

**Let's loop jobs**

Template syntax in Django is quite easy and straightforward so please have as a look this section to see how the loop 
is implemented.

https://github.com/germancin/Django-Portfolio/commit/40f01fe08f0afe99d44943062905281b37a5e894#diff-2b18d7445be0676f86b4aa70c30a7110R60

I am adding here the Built-in tag reference from Django Documentation

https://docs.djangoproject.com/en/2.0/ref/templates/builtins/

# URL include() for our Blog App

In Django We can have a url path that forwards the request to another url path App structure
within our project and that is exactly what we will do here.

**Create the url path for blog**

Let's open ```portfolio/urls.py``` and lets add another path to our ``urlpatterns`` list

Here we will add this code ``path('blog/', include('blog.urls')),``

which make reference to the urls from blog so this means that we must have something
into ``urls.py`` from blog app 

So your ``portfolio/urls.py`` should look like this 

**Notice** that we have to import include

```python
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', jobs.views.home, name='home'),
    path('blog/', include('blog.urls')),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

Now let's create the file ``blog/urls.py``  and add this code 

```python
from django.urls import path

from . import views

urlpatterns = [
    path('', views.allblogs, name='blog-page'),
]
```

As you see we are making reference to ``views.allblogs`` so as you could imagine 
this means ``allblogs`` is a class from views in blog app so our ``views.py``
should look like this

```python
from django.shortcuts import render

from .models import Blog

def allblogs(request):
    blogs = Blog.objects
    return render(request, 'blog/allblogs.html', {'blogs':blogs})
```

As you see this looks very similar to our ``jobs/views`` so is clear

**Create the allblogs.html**

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/blog-template.png"/>

Now create ``allblogs.html`` content please check the committed file.

https://github.com/germancin/Django-Portfolio/commit/12470ea3f7635e2d691faa41b65a2063ff642d92

Add some data into from the admin and you should have a page like this

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/blog-page.png"/>


# Let's do a blog details page

Here we wil present the content of the article

First we need to set the request in ``blog/views.py``

Here you have to add another path to handle this request

```python
from django.shortcuts import render, get_object_or_404

def detail(request, blog_id):
    blog_detail = get_object_or_404(Blog, pk=blog_id)
    return render(request, 'blog/detail.html', {'blog':blog_detail})
```

ok ``blog_id`` comes from the ``blog/urls.py`` which I'll explain it in a second.

``get_object_or_404`` is a Django shortcut function and what it does is 
get the object or 404 if does not finds it **I know!! is so cool!** so

we pass the object and ``pk`` means primary key which we pass the ``blog_id``

Here is the Django documentation definition
```Calls get() on a given model manager, but it raises Http404 instead of the model’s DoesNotExist exception.```

and the ``return`` we already know how that works ;)


**Let's pass the blog_id to our urls.py**

Open ``urls.py`` an add a new element to the ``urlpatterns`` list

``path('<int:blog_id>/', views.detail, name='detail-page'),``

So what this means is ``'<int:blog_id>/'`` Django look for ``blog_id`` after ``/blog`` 
which should be a ``integer`` 

``views.detail`` as we already learned means look for ``detail`` class in ``views.py``

``name='detail-page'`` is the reference url name

So in this way how ``urls.py``  communicate/send params to ``views.py`` 

so you should have ``blog/urls.py`` looking like this

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.allblogs, name='blog-page'),
    path('<int:blog_id>/', views.detail, name='detail-page'),
]
```

**Let's add the blog_id to the href attribute in blog page**

This is easy cheese just do the same we have done before 
```html 
href="{% url 'detail-page' blog.id %}"
```

The next step is telling Django look for any static file in 
 our project and combine it in one folder

To do this got o your ``settings.py`` file and add these:

```angularjs
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'portfolio/static/')
]

STATIC_ROOT = os.path.join(BASE_DIR, 'static')
STATIC_URL = '/static/'
```

We've seen this before so I won't go there.

Now go to your terminal and type : ``python manage.py collectstatic``

so now we have a new folder in our top level root called ``static``
make sure to don't push this to our repo.

<img src="https://github.com/germancin/Django-Portfolio/blob/master/readme_resources/static-folder.png" alt="admin-blog-add" />


**Done!**


# Now Let's deploy this bad boy to a server 

**Follow this steps on this link**

https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-16-04

# Now let's separate our credentials from local to the server.

In order to do this we have to add the following code into our ``settings.py``

```python
try:
    from .local_settings import *
except ImportError:
    pass
```

what this code does is import our .local_settings and if for reason there is an error go a pass that exception

**Create the local_settings.py file**

make sure you do not push this file to the repo so this should be added to the .gitignore

Push the changes to the repo and Pull it form the server

The next Step is Create the same file ``local_settings.py`` into the server 

Add all the credentials from settings.py file into this file with the secure, allowhost
and databases credentials different.


After adding all credentials in the server side on the ``local_settings.py`` file
**NOTE:** int he database HOST you have to set 127.0.0.1

**Let's create ``requirements.txt`` file in order to send it to the server and run 
all the project dependencies**

run: ``pip freeze > requirements.txt``

git push and git pull from server.

**Run requirements.txt from server side**

``pip install -r requirements.txt``


**Let's run migrations**

We have to run migrate ont he server side to run de database.

`` python manage.py makemigrations ``
`` python manage.py migrate ``

**Create superuser server side**

`` python manage.py createsuperuser  ``

**Collect static files**

``python manage.py collectstatic``

**Allow ufc firewall connect to :8000**

``sudo ufw allow 8000``

**Run server**

``python manage.py runserver 0.0.0.0:8000``

now you can test it with your online ip:8000

# Let's install Guinicorn**

``pip install gunicorn``

Since we installed gunicorn lets 

``pip freeze > requirements.txt``

Now run
``gunicorn --bind 0.0.0.0:8000 portfolio.wsgi``

# Is time to Create a Gunicorn systemd Service File

Follow this part here: 
https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-16-04



































