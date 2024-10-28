# Django tutorial layout for HTML files

This a simple tutorial for django with two HTML files and one layout.

## Prerequisites

### Python 3

`py` command should point to python3

```shell
py -V
# 3.10.0
```

### Check git is installed

```
git --version
```

## Create a new folder

```shell
mkdir myproj && cd myproj
```

## Add .gitignore and init git repository

Add the following .gitignore

```shell
.venv
*.sqlite3
__pycache__
```

Init repo with

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

Commit changes

```shell
git add . && git commit -m "allowed host in settings"
```

## Run migrations

```shell
py manage.py makemigrations
py manage.py migrate
```

## Run local server

```shell
py manage.py runserver
```

Now open your browser at localhost:8000

## Create templates folder

Create a new file under `templates/home.html` with content :

```html
<!-- inside templates/home.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Home</title>
  </head>
  <body>
    <h1>Hello-World</h1>
  </body>
</html>
```

Commit changes

```shell
git add . && git commit -m "added one HTML"
```

## Create controllers and routes

Create `core/views.py` with:

```shell
from django.shortcuts import render

def homepage(request):
    return render(request, 'home.html')
```

And go to `core/urls.py` :

```shell
from django.contrib import admin
from django.urls import path, include
from . import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.homepage),
]
```

```shell
git add . && git commit -m "add controller and route"
```

Check that home is displayed by re-running local server :

```shell
py manage.py runserver
```

## create the layout file

in your templates folder add `layout.html` and create new html squeleton.

```html
<!-- inside templates/layout.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{% block title %}{% endblock %}</title>
  </head>
  <body>
    {% block content %}{% endblock %}
  </body>
</html>
```

Add with git

```shell
git add . && git commit -m "add layout"
```

## modify the home.html

Modify `templates/home.html` like this :

```
{% extends "layout.html" %}

{% block title %}Home{% endblock %}

{% block content %}
    <h1>Hello-World</h1>
{% endblock %}
```

Commit & check

```shell
git add . && git commit -m "final layout"
```
