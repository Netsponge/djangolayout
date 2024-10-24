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