---
title: "What Are GET, POST, PUT & DELETE Requests!!"
datePublished: Fri Mar 03 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: cles5qrzi0ar70onv23k15knd
slug: what-are-get-post-put-delete-requests
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677322289560/08bc6d83-35b7-4840-b383-0e04dbb78106.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1677322342292/3e7042be-6b7c-43a8-ac84-69e1bd79cacd.png
tags: python, django, wemakedevs, mayankaggarwal, mayank

---

In this blog, we will explore the four main HTTP requests used in Django: GET, POST, PUT, and DELETE. We will cover the basics of each request and provide code examples for each.

1. ### GET Request
    

A GET request is used to retrieve data from a server. When a user visits a web page, their browser sends a GET request to the server to retrieve the HTML, CSS, and JavaScript files that make up the page. In Django, you can handle GET requests using the `HttpRequest` object.

Example:

```python
from django.http import HttpResponse

def my_view(request):
    if request.method == 'GET':
        # Code to retrieve data
        data = {'name': 'John', 'age': 30}
        return HttpResponse(data)
```

1. ### POST Request
    

A POST request is used to send data to a server. When a user fills out a form on a web page and clicks the submit button, their browser sends a POST request to the server with the form data. In Django, you can handle POST requests using the `HttpRequest` object.

Example:

```python
from django.http import HttpResponse

def my_view(request):
    if request.method == 'POST':
        # Code to process data
        name = request.POST.get('name')
        age = request.POST.get('age')
        # Code to save data to database
        return HttpResponse('Data saved successfully')
```

1. ### PUT Request
    

A PUT request is used to update an existing resource on the server. In Django, you can handle PUT requests using the `HttpRequest` object.

Example:

```python
from django.http import HttpResponse

def my_view(request, id):
    if request.method == 'PUT':
        # Code to update resource with ID=id
        return HttpResponse('Resource updated successfully')
```

1. ### DELETE Request
    

A DELETE request is used to delete an existing resource on the server. In Django, you can handle DELETE requests using the `HttpRequest` object.

Example:

```python
from django.http import HttpResponse

def my_view(request, id):
    if request.method == 'DELETE':
        # Code to delete resource with ID=id
        return HttpResponse('Resource deleted successfully')
```

### Conclusion

In conclusion, understanding the various HTTP requests used in Django is essential for building web applications. With the examples provided in this blog, you should be able to handle GET, POST, PUT, and DELETE requests in your Django application.