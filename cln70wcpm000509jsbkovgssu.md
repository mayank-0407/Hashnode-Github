---
title: "Make Your First Project with User Authentication in Django"
datePublished: Sun Oct 01 2023 05:30:12 GMT+0000 (Coordinated Universal Time)
cuid: cln70wcpm000509jsbkovgssu
slug: make-your-first-project-with-user-authentication-in-django
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696099215176/3f394ede-269e-4fac-aba6-2e70f04a7cff.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696099399264/aadd9f9c-9a9a-4a67-aa44-deeac00961f8.png
tags: django, todoapp, wemakedevs, mayankaggarwal, mayank

---

In this tutorial, we will walk through the process of creating a feature-rich ToDo (Task Management) application using Django for the backend and HTML, CSS, and JavaScript for the front end. This app will include user authentication, allowing users to sign up, log in, create, edit, and delete tasks. By the end of this tutorial, you will have a fully functional ToDo app with a secure user management system.

## Prerequisites

Before we begin, ensure that you have the following prerequisites installed:

1. Python (3.6 or higher)
    
2. Django (latest version)
    
3. A code editor (e.g., Visual Studio Code, Sublime Text)
    
4. Basic knowledge of HTML, CSS, and JavaScript
    
5. A basic understanding of Django
    

## Step 1: Setting Up the Django Project

Start by creating a new Django project and a new app within that project.

```bash
# Create a new Django project
django-admin startproject todo_project

# Navigate to the project directory
cd todo_project

# Create a new Django app
python manage.py startapp todo_app
```

## Step 2: Define the Task Model

In the `todo_app` folder, open the [`models.py`](http://models.py) file and define the `Task` model. This model will represent our ToDo tasks.

```python
# todo_app/models.py
from django.db import models
from django.contrib.auth.models import User

class Task(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    completed = models.BooleanField(default=False)

    def __str__(self):
        return self.title
```

After defining the model, create and apply the migrations:

```bash
python manage.py makemigrations
python manage.py migrate
```

## Step 3: Create User Authentication Views and Templates

### 3.1 User Registration

We'll create views and templates for user registration, login, and logout.

In the `todo_app` folder, create a new folder named `templates` if it doesn't already exist. Inside the `templates` folder, create another folder named `registration`.

Inside the `registration` folder, create two HTML templates: `signup.html` and `login.html`. These templates will be used for user registration and login, respectively.

#### signup.html

```html
<!-- todo_app/templates/registration/signup.html -->
{% extends 'todo_app/base.html' %}

{% block content %}
  <h2>Sign Up</h2>
  <form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Sign Up</button>
  </form>
{% endblock %}
```

#### login.html

```html
<!-- todo_app/templates/registration/login.html -->
{% extends 'todo_app/base.html' %}

{% block content %}
  <h2>Log In</h2>
  <form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Log In</button>
  </form>
{% endblock %}
```

### 3.2 User Authentication Views

Create views for user registration, login, and logout in the [`views.py`](http://views.py) file within the `todo_app` folder:

```python
# todo_app/views.py
from django.shortcuts import render, redirect
from django.contrib.auth import login, authenticate, logout
from django.contrib.auth.forms import UserCreationForm, AuthenticationForm
from django.contrib import messages

def signup(request):
    if request.method == 'POST':
        form = UserCreationForm(request.POST)
        if form.is_valid():
            user = form.save()
            login(request, user)
            messages.success(request, 'Registration successful.')
            return redirect('todo-list')
    else:
        form = UserCreationForm()
    return render(request, 'registration/signup.html', {'form': form})

def user_login(request):
    if request.method == 'POST':
        form = AuthenticationForm(request, data=request.POST)
        if form.is_valid():
            user = form.get_user()
            login(request, user)
            messages.success(request, 'Login successful.')
            return redirect('todo-list')
    else:
        form = AuthenticationForm()
    return render(request, 'registration/login.html', {'form': form})

def user_logout(request):
    logout(request)
    messages.success(request, 'Logout successful.')
    return redirect('login')
```

### 3.3 URL Patterns for User Authentication

Define URL patterns for user authentication in the [`urls.py`](http://urls.py) file within the `todo_app` folder:

```python
# todo_app/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('signup/', views.signup, name='signup'),
    path('login/', views.user_login, name='login'),
    path('logout/', views.user_logout, name='logout'),
]
```

## Step 4: Create the ToDo Views and Templates

We'll create views and templates for creating, editing, and deleting tasks, as well as displaying the task list.

### 4.1 ToDo Views

In the [`views.py`](http://views.py) file within the `todo_app` folder, create views for creating, editing, and deleting tasks, as well as listing tasks:

```python
# todo_app/views.py
from django.shortcuts import render, redirect, get_object_or_404
from .models import Task
from .forms import TaskForm
from django.contrib import messages
from django.contrib.auth.decorators import login_required

@login_required
def task_list(request):
    tasks = Task.objects.filter(user=request.user)
    return render(request, 'todo_app/task_list.html', {'tasks': tasks})

@login_required
def task_create(request):
    if request.method == 'POST':
        form = TaskForm(request.POST)
        if form.is_valid():
            task = form.save(commit=False)
            task.user = request.user
            task.save()
            messages.success(request, 'Task created successfully.')
            return redirect('todo-list')
    else:
        form = TaskForm()
    return render(request, 'todo_app/task_form.html', {'form': form})

@login_required
def task_edit(request, task_id):
    task = get_object_or_404(Task, id=task_id, user=request.user)
    if request.method == 'POST':
        form = TaskForm(request.POST, instance=task)
        if form.is_valid():
            form.save()
            messages.success(request, 'Task updated successfully.')
            return redirect('todo-list')
    else:
        form = TaskForm(instance=task)
    return render(request, 'todo_app/task_form.html', {'form': form, 'task': task})

@login_required
def task_delete(request, task_id):
    task = get_object_or_404(Task, id=task_id, user=request.user)
    if request.method == 'POST':
        task.delete()
        messages.success(request, 'Task deleted successfully.')
    return redirect('todo-list')
```

### 4.2 ToDo Templates

Create HTML templates for displaying the task list and managing tasks:

#### task\_list.html

```html
<!-- todo_app/templates/todo_app/task_list.html -->
{% extends 'todo_app/base.html' %}

{% block content %}
  <h2>ToDo List</h2>
  <ul id="todo-list">
    {% for task in tasks %}
      <li>
        <span>{{ task.title }}</span>
        <a href="{% url

 'todo-edit' task.id %}">Edit</a>
        <a href="{% url 'todo-delete' task.id %}">Delete</a>
      </li>
    {% endfor %}
  </ul>
  <a href="{% url 'todo-create' %}" class="btn btn-primary">Create Task</a>
{% endblock %}
```

#### task\_form.html

```html
<!-- todo_app/templates/todo_app/task_form.html -->
{% extends 'todo_app/base.html' %}

{% block content %}
  <h2>{% if task %}Edit Task{% else %}Create Task{% endif %}</h2>
  <form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">{% if task %}Update Task{% else %}Create Task{% endif %}</button>
  </form>
{% endblock %}
```

## Step 5: Create Task Forms

Create a form for creating and editing tasks in the [`forms.py`](http://forms.py) file within the `todo_app` folder:

```python
# todo_app/forms.py
from django import forms
from .models import Task

class TaskForm(forms.ModelForm):
    class Meta:
        model = Task
        fields = ['title', 'completed']
```

## Step 6: Configure URL Patterns

Configure URL patterns for the ToDo views in the [`urls.py`](http://urls.py) file within the `todo_app` folder:

```python
# todo_app/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.task_list, name='todo-list'),
    path('create/', views.task_create, name='todo-create'),
    path('edit/<int:task_id>/', views.task_edit, name='todo-edit'),
    path('delete/<int:task_id>/', views.task_delete, name='todo-delete'),
]
```

## Step 7: Create User Authentication Templates

We need to create templates for the login, signup, and logout links in the `base.html` template.

#### base.html

```html
<!-- todo_project/todo_app/templates/todo_app/base.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ToDo App</title>
  <link rel="stylesheet" href="{% static 'todo_app/style.css' %}">
</head>
<body>
  <header>
    <h1>ToDo App</h1>
    <nav>
      {% if user.is_authenticated %}
        <a href="{% url 'todo-list' %}">Tasks</a>
        <a href="{% url 'logout' %}">Logout</a>
      {% else %}
        <a href="{% url 'login' %}">Login</a>
        <a href="{% url 'signup' %}">Sign Up</a>
      {% endif %}
    </nav>
  </header>
  <main>
    {% block content %}
    {% endblock %}
  </main>
</body>
</html>
```

## Step 8: Static Files (CSS and JavaScript)

In this step, we'll create CSS and JavaScript files for styling and functionality.

### 8.1 Style (CSS)

Create a CSS file named `style.css` inside the `static/todo_app` directory:

```css
/* todo_project/todo_app/static/todo_app/style.css */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f0f0f0;
}

header {
  background-color: #333;
  color: #fff;
  text-align: center;
  padding: 20px 0;
}

nav {
  margin-top: 10px;
}

nav a {
  color: #fff;
  text-decoration: none;
  margin: 0 10px;
}

nav a:hover {
  text-decoration: underline;
}

main {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

h2 {
  margin-bottom: 20px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #ccc;
}

a.btn {
  background-color: #333;
  color: #fff;
  text-decoration: none;
  padding: 5px 10px;
  border-radius: 4px;
}

a.btn:hover {
  background-color: #555;
}

#add-todo {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#new-todo {
  flex-grow: 1;
  padding: 5px;
  border: 1px solid #ccc;
}

#add-button {
  background-color: #333;
  color: #fff;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}

#add-button:hover {
  background-color: #555;
}
```

### 8.2 Script (JavaScript)

Create a JavaScript file named `script.js` inside the `static/todo_app` directory:

```javascript
// todo_project/todo_app/static/todo_app/script.js
document.addEventListener('DOMContentLoaded', function () {
  const todoList = document.getElementById('todo-list');
  const addButton = document.getElementById('add-button');
  const newTodoInput = document.getElementById('new-todo');

  // Function to create a new ToDo task
  function createTodoElement(task) {
    const li = document.createElement('li');
    li.innerHTML = `
      <span>${task.title}</span>
      <a href="{% url 'todo-edit' 0 %}">Edit</a>
      <a href="{% url 'todo-delete' 0 %}">Delete</a>
    `;
    todoList.appendChild(li);
  }

  // Function to fetch and display ToDo tasks
  function fetchTodos() {
    fetch('/api/todos/')
      .then((response) => response.json())
      .then((data) => {
        todoList.innerHTML = '';
        data.forEach((task) => createTodoElement(task));
      });
  }

  // Function to add a new ToDo task
  function addTodo() {
    const title = newTodoInput.value;
    if (title) {
      fetch('/api/todos/', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({ title }),
      })
        .then((response) => response.json())
        .then((data) => {
          createTodoElement(data);
          newTodoInput.value = '';
        });
    }
  }

  // Add click event listener for the Add button
  addButton.addEventListener('click', addTodo);

  // Fetch and display initial ToDo tasks
  fetchTodos();
});
```

## Step 9: Configure User Authentication URLs

In the project-level [`urls.py`](http://urls.py) file (`todo_project/urls.py`), add the following URL patterns for user authentication:

```python
# todo_project/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
   

 path('admin/', admin.site.urls),
    path('', include('todo_app.urls')),  # ToDo app URLs
    path('accounts/', include('django.contrib.auth.urls')),  # User authentication URLs
]
```

## Step 10: Run the Development Server

You're now ready to run the Django development server and see your ToDo app with user authentication in action:

```bash
python manage.py runserver
```

Visit [`http://localhost:8000/`](http://localhost:8000/) in your web browser, and you should be able to:

* Sign up for an account.
    
* Log in using your credentials.
    
* Create, edit, and delete tasks.
    
* Log out when you're done.
    

### Conclusion

By the end of this tutorial, you've acquired valuable skills and knowledge in web development, including:

1. **Django Fundamentals:** You've learned how to create a Django project and app, define models, and set up user authentication, making use of Django's built-in features for efficient web development.
    
2. **HTML, CSS, and JavaScript Integration:** We've seamlessly integrated HTML templates for rendering the user interface, styled the app with CSS, and added interactive functionality using JavaScript. This combination results in a dynamic and user-friendly web application.
    
3. **User Authentication:** The app includes a secure user authentication system, allowing users to sign up, log in, and log out. This is vital for protecting user data and providing personalized experiences.
    
4. **Task Management:** Users can efficiently manage their tasks, including creating, editing, and deleting them. The ToDo app is designed to help users stay organized and productive.
    
5. **Customization and Expansion:** You've gained the skills to customize and expand the app further. Whether it's adding more features, refining the design, or integrating additional technologies, the possibilities for growth are endless.
    

As you continue your journey in web development, remember that building projects like this ToDo app is an excellent way to refine your skills and gain hands-on experience. The combination of Django and frontend technologies empowers you to create versatile and robust web applications. Don't hesitate to explore new ideas and functionalities to make your project even more unique and valuable.