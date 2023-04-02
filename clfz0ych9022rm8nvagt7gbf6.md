---
title: "Project 1:Create your own Weather App in 5 Minutes with Django and OpenWeatherAPI"
datePublished: Sun Apr 02 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clfz0ych9022rm8nvagt7gbf6
slug: project-1create-your-own-weather-app-in-5-minutes-with-django-and-openweatherapi
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680265966253/5fc5793b-f1f8-40de-a4ce-f3a82325d107.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1680266005076/5ccc29ef-d5eb-4e89-b769-ba883272b387.png
tags: web-development, projects, wemakedevs, mayankaggarwal, mayank

---

# **Introduction**

In today's world, knowing the weather conditions has become a crucial aspect of our daily lives. With the advancements in technology, it has become easier to access weather information from anywhere in the world. OpenWeatherAPI is one such tool that provides accurate and up-to-date weather information for any location in the world. In this tutorial, we will be using OpenWeatherAPI to create a weather app. By the end of this tutorial, you will have a fully functional weather app that can display weather information for any location in the world. So, let's get started!

<mark>This is my first project in which I Will be telling how I made this weather app.</mark>

<mark>You can check My </mark> [<mark>Github repository</mark>](https://github.com/mayank-0407/clearsky) <mark> for the same.</mark>

### Requirements:

1. Account on [OpenWeatherAPI](https://openweathermap.org/).
    
2. Some Knowledge of HTML, CSS, Python.
    
3. Requests dependency
    

### Getting Started

1. Firstly Create an Account on the [OpenWeather API website](https://openweathermap.org/).
    
2. Now you can copy your API key from the MY API keys tab to your notepad.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680263312390/60c2d0b6-8ae9-4aa3-a07e-9e472dcc42fd.png align="center")
    
    Let's understand a bit about this API.
    

### How Weather API Works

1. To understand this you need to click on API in the Navbar.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680263418494/660544a2-35ac-4745-a5e1-f2bfb7533ef7.png align="center")
    
    Now scroll a bit and select API doc in current weather data.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680263457244/a0c9e899-edc4-4d62-be66-af8c9895950a.png align="center")
    
    Now you can see here how to use this API.
    
4. What are we using is getting weather from the city name.
    
5. So scroll down till you get this link with the city name and API key.
    
6. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680263553837/d2d0ce30-9962-411f-b652-563ecf05cb8f.png align="center")
    
    Here just erase {city name} and {API KEY} and enter the city you want to and your API key.
    
7. Now you will be able to a dictionary of weather information like this.
    
8. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680263649550/26b65e29-0154-4181-ad39-55367ae9a253.png align="center")
    
    Now we Will create a Django project and extract this data.
    

### Creating Django Project

1. Make sure you are having Django installed on your desktop.
    
2. Naming my project skyclear.
    
    ```python
    python-admin startproject skyclear
    ```
    
3. Now go into the folder cd skyclear.
    
4. Now make a home app in this.
    
    ```python
    python manage.py createapp home
    ```
    
5. Now add home in settings.py.
    
    ```python
    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'home',
    ]
    ```
    
6. Now in urls.py of skyclear add the path to home.
    
    ```python
    from django.contrib import admin
    from django.urls import path,include
    
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('',include('home.urls')),
    ]
    ```
    
7. Now create a file named urls.py in home and this data.
    
    ```python
    from django.urls import path,include
    from . import views
    
    urlpatterns = [
        path('', views.home, name="showhome"),
    ]
    ```
    
8. Now in views.py add a function that renders our home page.
    
    ```python
    from django.shortcuts import render
    
    # Create your views here.
    def home(request):
        
        return render(request,"home/home.html",context={})
    ```
    
9. Now the first test is it working or not.
    
    ```python
    python manage.py runserver
    ```
    

### Creating our Front end

1. Create a folder in home templates/home.
    
2. Now create a file named home.html.
    
3. Now Create the Front end according to you.
    
4. In this project, I have used bootstrap.
    
5. And Code for the same is:
    
    ```xml
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>SkyClear</title>
        <link rel="icon" href="./13d.png">
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
        <style>
            .card {
            margin: 10% auto;
            float: none; 
            margin-bottom: 10px;
    }
        </style>
    </head>
    <body>
        <nav class="navbar navbar-light bg-light">
            <div class="container-fluid">
              <a class="navbar-brand">SkyClear</a>
              <form class="d-flex">
                <input class="form-control me-2" name="entered_city" type="search" placeholder="Search" aria-label="Search">
                <button class="btn btn-outline-success" type="submit">Search</button>
              </form>
            </div>
          </nav>    
          <div class="card mb-3 " style="max-width: 440px;">
            <div class="row g-0">
              <div class="col-md-4 mx-auto" style = "{backgroundImage : http://openweathermap.org/img/wn/{{}}.png}">
                <img src="http://openweathermap.org/img/wn/{{}}.png" class="img-fluid rounded-start" alt={{city}}>
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">  -  </h5>
                  <p class="card-text">Temperature(°C): °C</p>
                  <p class="card-text">Temperature(K):  K</p>
                  <p class="card-text"><small class="text-muted">Humidity:  - Pressure: Pa </small></p>
                </div>
              </div>
            </div>
          </div>
          <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
    </body>
    </html>
    ```
    

Now our Front end is also ready. Now, let's start adding the data from API.

### Fetching data from API

1. For getting data we need a requests library.
    
2. You can check their [Documentation](https://pypi.org/project/requests/).
    
3. Type **pip install requests** in the terminal to install requests.
    
4. Now just import requests in views.py.
    
5. Now let's write code for fetching data.
    
    ```python
    from django.shortcuts import render
    import requests
    
    # Create your views here.
    def home(request):
        
        city="patiala"
        url=f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={apikey}'
        data = requests.get(url).json()
        
        print(data)
        return render(request,"home/home.html",context={})
    ```
    
6. Now we got data from API you can check it in the terminal after refreshing the home page.
    

### Fetching Required information

1. Now you can see all the data in your terminal.
    
2. Now as we do in a python dictionary fetch the data in the same manner.
    
3. My code for the same is given below.
    
    ```python
    from django.shortcuts import render
    import requests
    
    # Create your views here.
    def home(request):
        
        city="patiala"
        url=f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={apikey}'
        data = requests.get(url).json()
        
        payload={'city':data['name'],
                 'weather':data['weather'][0]['main'],
                 'icon':data['weather'][0]['icon'],
                 'celcius_temperature':data['main']['temp'],
                 'kelvin_temperature':int(data['main']['temp'])-273,
                 'pressure':data['main']['pressure'],
                 'humidity':data['main']['humidity'],
                 'description':data['weather'][0]['description'],
                 }
        return render(request,"home/home.html",context={'data':payload})
    ```
    
4. So we got all the data in the payload we required for a weather app.
    
5. Now just send this data in context to our front end.
    

### Displaying data on the front end

1. Now we got all the data on our HTML page.
    
2. Just use Ginger Coding and add all the data in HTMLpage as I did below in this code.
    
    ```xml
       <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>SkyClear</title>
        <link rel="icon" href="./13d.png">
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
        <style>
            .card {
            margin: 10% auto;
            float: none; 
            margin-bottom: 10px;
    }
        </style>
    </head>
    <body>
        <nav class="navbar navbar-light bg-light">
            <div class="container-fluid">
              <a class="navbar-brand">SkyClear</a>
              <form class="d-flex">
                <input class="form-control me-2" name="entered_city" type="search" placeholder="Search" aria-label="Search">
                <button class="btn btn-outline-success" type="submit">Search</button>
              </form>
            </div>
          </nav>    
          <div class="card mb-3 " style="max-width: 440px;">
            <div class="row g-0">
              <div class="col-md-4 mx-auto" style = "{backgroundImage : http://openweathermap.org/img/wn/{{data.icon}}.png}">
                <img src="http://openweathermap.org/img/wn/{{data.icon}}.png" class="img-fluid rounded-start" alt={{data.city}}>
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">{{data.city}}  -  {{data.description}}</h5>
                  <p class="card-text">Temperature(°C): {{data.celcius_temperature}}°C</p>
                  <p class="card-text">Temperature(K): {{data.kelvin_temperature}} K</p>
                  <p class="card-text"><small class="text-muted">Humidity: {{data.humidity}} - Pressure:{{data.pressure}} Pa </small></p>
                </div>
              </div>
            </div>
          </div>
          <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
    </body>
    </html>
    ```
    
3. So we are Good to go just run the server and you will see the data.
    
4. But here we are manually adding the city in our code, So to get user input let's to start a get request service.
    

### How to get weather information of the city dynamically

1. Just write a simple code as you write for getting a GET requests.
    
2. As in the navbar, we are already having a form.
    
3. Just name the form and in views.py fetch the data.
    
4. And add this data in URLAs I did below.
    
    ```python
    from django.shortcuts import render
    import requests
    
    # Create your views here.
    def home(request):
        
        city=request.GET.get('entered_city')
        # city="patiala"
        url=f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={apikey}'
        data = requests.get(url).json()
        
        payload={'city':data['name'],
                 'weather':data['weather'][0]['main'],
                 'icon':data['weather'][0]['icon'],
                 'celcius_temperature':data['main']['temp'],
                 'kelvin_temperature':int(data['main']['temp'])-273,
                 'pressure':data['main']['pressure'],
                 'humidity':data['main']['humidity'],
                 'description':data['weather'][0]['description'],
                 }
        return render(request,"home/home.html",context={'data':payload})
    ```
    
5. So our project has been finished Successfully. Just Run the server and you are good to go.
    

How our project now looks like?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680265205874/4fd9d4e6-8c4f-46a7-98cf-28137a77994e.png align="center")

So this is what our project looks like. I think being a basic project this will also help you in learning more about Django.

> Make Sure to follow me on [**hashnode**](https://blog.mayankaggarwal.live/).
> 
> Having any Querry? [**Ask me**](https://mayankaggarwal.live/).