# Django tutorial layout for HTML files 

This a simple tutorial for django with two HTML files and one layout.

## Prerequisites

`py` command should point to python3

```shell
py -V
# 3.10.0
```

postgresql 16+ must be up and running on your machine with `pg_ctl status` (Windows), or `pgrep -l postgres` (Mac), or `sudo systemctl status postgresql` (Linux)


Git 

## Create a new folder

```shell
mkdir your project && cd your project
```

## Add .gitignore and start git

Add the following .gitignore

```shell
.venv
*.sqlite3
__pycache__
```

## Add your folder to your git 

```shell
git init
git add . && git commit -m "first commit"
```

## Create virtual environment for Python and activate it

```shell
py -m venv .venv
source .venv/bin/activate
```

## Install django and pg driver

```shell
py -m pip install django psycopg2-binary
```

## Build django skeleton

Below, "core" means the core of our app, "." means build skeleton inside the current folder :

```shell
django-admin startproject core .
git add . && git commit -m "django first files"


## Change settings.py

Inside settings.py, add localhost to the list of allowed hosts, like this :


ALLOWED_HOSTS = ['localhost', '127.0.0.1']
```

And database settings like this :

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'webplus',
        'USER': 'webplususer',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```


## Django comes with default tables (to manage users and authorizations notably), so let's inject them into our new db :

```
py manage.py makemigrations 
py manage.py migrate 
```

## Create a superadmin locally
Create a super user, just enter the following command and enter some realistic values when asked :

```py manage.py createsuperuser```

## Run local server ##
```
py manage.py runserver
```
Now open your browser at localhost:8000/admin and log in with the credentials of the super user you just created.

## Commit
```
If everything is working well, you can commit changes

git add . && git commit -m "project ready"
```