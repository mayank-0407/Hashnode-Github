# Creating a Login Page in 2 min

In this tutorial, we will show you how to create a login page with Django, one of the most popular Python web frameworks. We will use Django's built-in authentication system to handle user authentication. Let's get started!

### Step 1: Create a New Django Project

First, we need to create a new Django project. Open up a terminal and navigate to the directory where you want to create your project. Once you are there, type the following command to create a new project:

```python
django-admin startproject myproject
```

This will create a new directory called myproject in your current directory.

### Step 2: Create a New Django App

Next, we need to create a new app within our project. An app is a modular component of a Django project that performs a specific function. In our case, we will create an app that handles user authentication. To create a new app, type the following command in the terminal:

```python
python manage.py startapp accounts
```

This will create a new directory called accounts within your project directory.

### Step 3: Configure Your Django App

Now that we have created our app, we need to configure it to handle user authentication. Open up the accounts/views.py file and add the following code:

```python
from django.shortcuts import render, redirect
from django.contrib.auth.forms import AuthenticationForm
from django.contrib.auth import login, logout

def login_view(request):
    if request.method == 'POST':
        form = AuthenticationForm(data=request.POST)
        if form.is_valid():
            user = form.get_user()
            login(request, user)
            return redirect('home')
    else:
        form = AuthenticationForm()
    return render(request, 'login.html', {'form': form})

def logout_view(request):
    logout(request)
    return redirect('home')
```

This code defines two views: login\_view and logout\_view. The login\_view displays a login form and handles user authentication. The logout\_view logs the user out and redirects them to the home page.

### Step 4: Create the Login HTML Template

Next, we need to create an HTML template for the login page. Create a new directory called templates within the accounts directory, and then create a new file called login.html. Add the following code to the file:

```python
{% extends 'base.html' %}

{% block content %}
    <h2>Login</h2>
    <form method="post">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Login</button>
    </form>
{% endblock %}
```

This code extends a base template and defines a login form. The form is rendered using Django's built-in AuthenticationForm.

### Step 5: Update Your URLs

Finally, we need to update our project's URLs to include the new views. Open up the myproject/urls.py file and add the following code:

```python
from django.contrib import admin
from django.urls import path, include
from accounts.views import login_view, logout_view

urlpatterns = [
    path('admin/', admin.site.urls),
    path('login/', login_view, name='login'),
    path('logout/', logout_view, name='logout'),
    # Include the default authentication URLs.
    path('accounts/', include('django.contrib.auth.urls')),
]
```

This code maps the login and logout views to URLs and includes Django's default authentication URLs.

### Step 6: Run Your Django App

Now that we have created our login page, we can run our Django app by typing the following command in the terminal:

```python
python manage.py runserver
```

This will start a local development server, and you can access your login page by navigating to [**http://localhost:8000/login/**](http://localhost:8000/login/).

### Conclusion

In conclusion, creating a login page with Django is a fairly simple task. We can accomplish this by defining a login view, creating a login template, and defining the URL for the login page. With these basic steps, we can quickly create a functional login page that allows users to authenticate themselves and access our application's protected content.

In addition to the basic functionality we covered in this tutorial, there are many other features that we can add to our login page, such as password reset functionality, user registration, and two-factor authentication. With Django's robust authentication framework and powerful built-in tools, we have the flexibility to build login pages that meet the specific needs of our application and our users.