# Django tutorial layout for HTML files 

This a simple tutorial for django with two HTML files and one layout.

## Prerequisites

`py` command should point to python3

```shell

py -V
# 3.10.0

```

## Install Git

```

git ---v or git -version

```

## Create a new folder

```shell

mkdir template && template

```

## Add .gitignore and start git

Add the following .gitignore

```shell

.venv
*.sqlite3
__pycache__

```

## Add your file to your git 

```shell

git init
git add . && git commit -m "first commit"

```

## Create virtual environment for Python and activate it

```shell

py -m venv .venv
source .venv/bin/activate

```


## Install django 

```shell

py -m pip install django

```

## Build django skeleton

Below, "core" means the core of our app, "." means build skeleton inside the current folder :

```shell

django-admin startproject core .
git add . && git commit -m "django first files"

```

## Change settings.py

Inside settings.py, add localhost to the list of allowed hosts, like this :

```shell

ALLOWED_HOSTS = ['localhost', '127.0.0.1']

```


## Django comes with default tables (to manage users and authorizations notably), so let's inject them into our new db :

```shell

py manage.py makemigrations 
py manage.py migrate 

```
## git commit

```shell

git add . && git commit -m "django first files"

```

## Run local server ##

```shell

py manage.py runserver

```
Now open your browser at localhost:8000

## Create templates folder

This folder add to your files structure your HTML'S for your views

After the folder apparing, add new file to your TEMPLATES folder and create a new files named -> `Home.html` and `About.hmtl`.

For create the structure of your HTML fastly, use this trick -> write - `!` - and press Enter, your HTML structures is ready.

Add a text in the body and links `<p>About<a href="/">about</a></p>`  `<p>Go to Home<a href="/">Home</a>page.</p>` to see later the interaction of your link page.

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
</head>
<body>
    <h1>Hello-World</h1>
    <p>About<a href="/">about</a></p>
</body>
</html>

```
```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About</title>
</head>
<body>
    <h1>About Us</h1>
    <p>Go to Home<a href="/">Home</a>page.</p>
</body>
</html>

```

## Import HTTP response for views

For a view rendering you need to include the imports of the HTML.

Go to Views file, and add the Import.

```shell

from django.http import HttpResponse


def homepage(request):
        return HttpResponse("Hello-World.")

def about(request):
        return HttpResponse("About.")

```

And go to Url's file, and add the Url's.

```shell

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.homepage,),
    path('about/', views.about),
    path('posts/', include.posts.urls),

```

## commit

```shell

git add . && git commit -m "add html imports"

```

## Create a Layout file.

The Layout file html defined template inheritence.
Load the css file with `{% load static %}`and by ` {% block %}` ` {% endblock %}`


```html

<!DOCTYPE html>
{% load static %}
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>

    {% block %}
        Django App
    {% endblock %}
    
    </title>
     <link rel="stylesheet" href="{% static 'css/style.css' %}">
</head>
<body>
    <nav>
    <a href="/">🏡</a> 
    <a href="/about">👀</a> 
    <a href="/">📰</a> 
    <main>
    {% block content %}
    {% endblock %}
    </main>
    </nav>
</body>
</html>

```
