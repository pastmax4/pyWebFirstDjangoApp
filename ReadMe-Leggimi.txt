01Aprile2019
------------------------------------------------------------------------

https://docs.djangoproject.com/en/2.1/intro/tutorial01/

Ecco i passi per creare un progetto django

------------------------------------------------------------------------
-)Creating a project
Auto-generate some code that establishes a Django project – 
a collection of settings for an instance of Django, including 
database configuration, Django-specific options and application-specific settings.

Supponiamo che il progetto si chiami "mysite".
Andare nella directory che contiene i progetti e lanciare il comando:

django-admin startproject mysite

This will create a mysite directory in your current directory.

Ecco come appare la directory:

mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
        
-----------------------------------------------------------
-) Creating the Polls app
Now that your environment is set up, you’re set to start doing work.

Each application you write in Django consists of a Python package 
that follows a certain convention. 

Django comes with a utility that automatically generates 
the basic directory structure of an app, so you can focus 
on writing code rather than creating directories.

What’s the difference between a project and an app? 
An app is a Web application that does something 
A project is a collection of configuration and apps for a particular website. 
A project can contain multiple apps.
An app can be in multiple projects.
-----------------------------------------------------------
-) Create your app

To create your app, make sure you’re in the same directory as manage.py 
and type this command:

python manage.py startapp polls

    Per windows dovrebbe esser questo io ho usato quello sopra e funziona
    py manage.py startapp polls


That’ll create a directory polls, which is laid out like this:

polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
    
    
-----------------------------------------------------------
-) Write your first view

 Open the file:
 
 ..\DjangoProjects\mysite\polls\views.py
 
 put the following Python code in it:
 ... see file ...
  
 To call the view, we need to map it to a URL 
 and for this we need a URLconf.
 To create a URLconf in the polls directory, 
 create a file called urls.py. 
 Your app directory should now look like:
 
  polls/
     __init__.py
     admin.py
     apps.py
     migrations/
         __init__.py
     models.py
     tests.py
     urls.py  <----------------
     views.py

   
In the polls/urls.py file include the following code:   
...


The next step is to point the root URLconf at the polls.urls module. 
In mysite/urls.py, add an import for django.urls.include 
and insert an include() in the urlpatterns list, so you have:

mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py     <----------------------
        wsgi.py



The include() function allows referencing other URLconfs. Whenever Django encounters include(), it chops off whatever part of the URL matched up to that point and sends the remaining string to the included URLconf for further processing.
The idea behind include() is to make it easy to plug-and-play URLs. Since polls are in their own URLconf (polls/urls.py), they can be placed under “/polls/”, or under “/fun_polls/”, or under “/content/polls/”, or any other path root, and the app will still work.

When to use include()
You should always use include() when you include other URL patterns. admin.site.urls is the only exception to this.
------------------------------------------------------------------------


You have now wired an index view into the URLconf. 
Lets verify it’s working, run the following command:

$ python manage.py runserver


questo fa partire il web server di prova:

http://127.0.0.1:8000/

