# Django Block

This is a blog app written in Django.

It is based on the steps from the [Code Institute code walkthrough](https://github.com/Code-Institute-Solutions/blog/tree/main/01_getting_set_up/01_create_project_app).

## Getting started

install Django LTS version ~=4.2.1.

Create a new project (the dot at the end to signify the current directory)

```sh
django-admin startproject codestar .
```

Create the blog app.

```sh
python manage.py startapp blog
```

The ```python3 manage.py startapp blog``` was used in the course, but when I used this instead of the above, I saw the error: *Python was not found; run without arguments to install from the Microsoft Store, or disable this shortcut from Settings > Manage App Execution Aliases.*

This app is then added to the installed apps array in codestar/settings.py and add localhost to the allowed hosts array.

```py
ALLOWED_HOSTS = ['localhost', '127.0.0.1']
```

Then in the blog/views.py:

```py
from django.shortcuts import render
from django.http import HttpResponse

def my_blog(request):
    return HttpResponse("Hello, Blog")
```

In codestar/urls.py import the my_blog view and add the path to the urlpatterns

```py
from django.contrib import admin
from django.urls import path
from blog.views import my_blog

urlpatterns = [
    path('admin/', admin.site.urls),
    path('blog/', my_blog, name='blog'),
]
```

Run the app:

```sh
python manage.py runserver
```

Go to http://127.0.0.1:8000/blog/ and see the "Hello Blog" message.
