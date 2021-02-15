# Django Commands
- First run the django command to initialize the project
`C:> django-admin startproject telusko`
Open with visual studio
To initalize the app
`C:> python manage.py startapp calc`
To start the server of django
`C:> python manage.py runserver`

In calc, create a urls.py file just like in the main project
`path ('', views.home, name = 'home')`
Include the calc.urls in main projects urls.py
Django template language
Ginga

`{% extends 'base.html' %}`
`{% block content %}`
`<h1>Hello </h1>`
`{% endblock %}` 	

We use  MVT Framework
**Model** - Data
**View** - Connected with URL (write business logic)
**Template** - HTML, DTL, CSS

**In urls.py**
views.home
home refers to function defined in views.py

To copy files from from static folder to assets folder

    C:\>python manage.py collectstatic

In settings.py we have:

    STATIC_URL = '/static/'
    STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]
    STATIC_ROOT = os.path.join(BASE_DIR, 'assets')


Use *djangify* inorder to map urls in src in HTML for static django files
For passing multiple variables, use class in models.py
and use initialize the class in view.py

**Object Relational Mapping**
ORM creates table and adds rows on the bases of classes and objects.
Installing PostgreSQL
pgAdmin for User Interface

    C:> pip install psycopg2

install pillow to perform migration on database

To check sql command from powershell

    C:> python manage.py makemigration

     python .\manage.py sqlmigrate travello 0001 python .\manage.py sqlmigrate travello 0001

To create superuser enter command:

    C:> python manage.py createsuperuser

Then go to `localhost:8000/admin` 
and enter details

To register your model into the admin panel,
go to admin.py and add following lines:

    from django.contrib import admin
    from .models import BestTours

    # Register your models here.
    
    admin.site.register(BestTours)


In settings.py (for images path for admin.py) add:

    MEDIA_URL  = '/media/'
    MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
    Also change path in .html file:
    Add {{b.img.url}} instead

In urls.py add:

    from django.conf import settings
    from django.conf.urls.static import static

User registration
Create seperate app for accounts :

    C:> python manage.py startapp accounts

    if request.method == 'POST':
    first_name = request.POST['first_name']
    last_name = request.POST['last_name']
    username = request.POST['username']
    password1 = request.POST ['password1']	
    
    return redirect('/') #Redirects to homepage

header file 	for using inbuilt username, auth_user database

    from django.contrib.auth.models import User, auth


To create username and save it in database (pgadmin4)	

    user = User.objects.create_user(username = username, password = password1, email = email, first_name = first_name, last_name = last_name)
    user.save()

To send messages to html form
messages.info(request, 'Username taken')

To customize admin

    Install django suit
    pip install  django-suit

Create apps.py in main folder and add following code:
from suit.apps import DjangoSuitConfig

    class SuitConfig(DjangoSuitConfig):
    	layout = 'horizontal'

Also modify Installed apps in settings.py

       'timetable.apps.SuitConfig',

   

to dumpdata
>python manage.py dumpdata > data.json

to loaddata
> python manage.py loaddata "data.json"

In case, of uniqueviolation error while loading data to postgresql
gotto dbshell:
> python manage.py dbshell
> Truncate table django_content_type cascade;
> Select  * from django_content_type;

To clear whole data:
> python manage.py flush

Then run loaddata




