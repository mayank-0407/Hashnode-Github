---
title: "Getting Started with Web Development!!"
datePublished: Thu Feb 23 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clegq7ytz02hr4pnvhl8v9qka
slug: getting-started-with-web-development
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1676991963442/233adb81-8834-441b-87f9-33c2fd3e130d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1676992012010/ac9f9829-49d5-4170-bece-46b8e8d9bbd1.png
tags: django, web-development, wemakedevs, mayankaggarwal, mayank

---

If you're looking to build web applications using Python, then Django is a great framework to get started with. Django is a powerful, open-source framework that makes it easy to build web applications quickly. In this blog, we will provide you with a beginner's guide to starting with Django, including some tips and resources to help you get started.

You can go ahead without installing a virtual Environment on your PC. But it is preferred to use a virtual environment for Django because otherwise, it can cause a bit of a problem if you work with multiple projects. Which I will explain later.

### Step 1: Install virtualenv

The first step in getting started with Django is to install it on your environment on your computer. Django requires Python, so make sure that Python is installed on your computer first. You can check if Python is installed by typing "python --version" in the command prompt. If you don't have Python installed, you can download it from the official website. Once you have Python installed, Now you can install Django by typing:

```python
pip3 install virtualenv
```

### Step 2: Checking if the env is installed or not.

You can use the following command to see if virtualenv is installed successfully.

```python
pip3 freeze
```

### Step 3: Now create an environment for your project

Now we had installed virtual env on our PC. Now we need to create an environment for our project. To do so use this command:

```python
virtualenv vnv
```

### Step 4: Using the Environment

Now we had Successfully created an environment for our project. So now we need to activate it before using our project. Note: we need to start our environment every time before we start our project as we install all the requirements on our environment.

And after you had done your work you need to deactivate your environment. So that it may not get crashed.

```python
source ./vnv/bin/activate
deactivate
```

Where vnv in the first command is our environment name. And second command is to deactivate our environment.

Now let's start with Django.

### Step 1: Install Django

Now you can install Django by typing the following command in the command prompt:

```python
pip install django
```

This will install the latest version of Django.

### Step 2: Create a New Django Project

After installing Django, you can create a new Django project by typing the following command in the command prompt:

```python
django-admin startproject projectname
```

Replace "project-name" with the name of your project. This command will create a new Django project in a folder with the same name as the project name.

### Step 3: Create a New Django App

Once you have created a new Django project, you can create a new Django app by typing the following command in the command prompt:

```python
python manage.py startapp appname
```

Replace "appname" with the name of your app. This command will create a new Django app in a folder with the same name as the app name.

Step 4: Configure Your Django App

Now that you have created a new Django app, you can configure it by adding models, views, and templates. Models define the structure of your data, views handle requests and return responses, and templates define the look and feel of your website. You can create new models, views, and templates by adding them to the relevant folders in your app.

### Step 5: Run Your Django App

Once you have configured your Django app, you can run it by typing the following command in the command prompt:

```python
python manage.py runserver
```

This command will start a development server on your computer, which you can access by opening your web browser and navigating to [**http://localhost:8000/**](http://localhost:8000/). You should see the default Django welcome page.

### Conclusion

Django is a powerful framework that makes it easy to build web applications quickly. In this blog, we have provided you with a beginner's guide to starting with Django, including how to install Django, create a new Django project and app, configure your app, and run your app. With these basic steps, you can start building your own web applications using Django. There are many resources available online to help you learn more about Django, so don't be afraid to explore and experiment with the framework.