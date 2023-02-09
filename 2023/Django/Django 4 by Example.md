# Enviroment Setup

## pyenv

https://realpython.com/intro-to-pyenv/

```
$ pyenv versions
```

## pypenv virtual enviroments

```
$ pyenv virtualenv <python_version> <environment_name>
```

```
$ pyenv activate <environment_name>
$ pyenv deactivate
```

# Django

https://docs.djangoproject.com/en/4.1/intro/tutorial01/

## Setup project

```
$ django-admin startproject mysite
```

```
$ python manage.py runserver
```

## Apply migrations

```
$ python manage.py migrate
```

## Create App

```
$ python manage.py startapp blog
```

## Activating the application

Edit the `settings.py` file and add "blog.apps.BlogConfig" to the INSTALLED_APPS setting.

## Create the models and migrate

```
$ python manage.py makemigrations blog
$ python manage.py sqlmigrate blog 0001
$ python manage.py migrate
```

## Creating an administration site for models

```
$ python manage.py createsuperuser
```

https://docs.djangoproject.com/en/4.1/ref/contrib/admin/

## Cretaing Objects

## Creating model managers

## Building list and detail views

Edit the `views.py `file in the blog application folder

## Adding URL patterns for your views

Create a `urls.py` file in the directory of the blog application

https://docs.djangoproject.com/en/4.1/topics/http/urls/#path-converters

Next, you have to include the URL patterns of the blog application in the main URL patterns of the project. Edit the urls.py file located in the mysite directory of your project

## Creating templates for your views

https://docs.djangoproject.com/en/4.1/ref/templates/language/
https://docs.djangoproject.com/en/4.1/ref/templates/builtins/



## Using canonical URLs for models

https://docs.djangoproject.com/en/4.1/ref/urlresolvers/

## Creating SEO-friendly URLs for posts

## Adding pagination

## Building class-based views

https://docs.djangoproject.com/en/4.1/topics/class-based-views/intro/

## Creating forms with Django

https://docs.djangoproject.com/en/4.1/ref/forms/fields/
