---
title: "Decorators in Django !!"
datePublished: Tue Mar 07 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clexvi6z30063mvnv081acifp
slug: decorators-in-django
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677327035102/9f59744f-e273-4542-9f82-323dcb447bc0.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1677327073716/eeb9a025-f75c-474e-997e-73082d2f7531.png
tags: django, decorators, wemakedevs, mayankaggarwal, mayank

---

Django decorators are a powerful tool for modifying the behavior of views, functions, and methods in your Django application. In this blog, we will discuss what decorators are, how to use them, and provide examples of some of the most commonly used decorators in Django.

### What are decorators?

Decorators are functions that modify the behavior of other functions. They are used to add functionality to a function or method without changing its code. Decorators are defined using the @ symbol followed by the name of the decorator function.

Here is an example of a decorator that adds a log message before and after a function is called:

```python
def log_decorator(func):
    def wrapper(*args, **kwargs):
        print('Before function call')
        result = func(*args, **kwargs)
        print('After function call')
        return result
    return wrapper

@log_decorator
def my_function():
    print('Function called')
```

When we call `my_function()`, the log\_decorator will be called first, and it will add the log messages before and after the function is called. This is a simple example of how decorators work.

### Using Decorators in Django

Django provides several built-in decorators that you can use to modify the behavior of your views, functions, and methods. Here are some of the most commonly used decorators in Django:

### @login\_required

The `@login_required` decorator is used to restrict access to a view to only logged-in users. If a user is not logged in, they will be redirected to the login page.

```python
from django.contrib.auth.decorators import login_required

@login_required
def my_view(request):
    # view code here
```

### @csrf\_exempt

The `@csrf_exempt` decorator is used to disable the CSRF protection on a view. CSRF protection is enabled by default in Django to prevent cross-site request forgery attacks. However, there may be cases where you want to disable CSRF protection, such as when building a public API.

```python
from django.views.decorators.csrf import csrf_exempt

@csrf_exempt
def my_view(request):
    # view code here
```

### @cache\_page

The `@cache_page` decorator is used to cache the output of a view for a specified amount of time. This can improve the performance of your application by reducing the number of requests that need to be processed.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 15)
def my_view(request):
    # view code here
```

### @require\_http\_methods

The `@require_http_methods` decorator is used to restrict the HTTP methods that a view can respond to. This can be useful for enforcing RESTful API design principles.

```python
from django.views.decorators.http import require_http_methods

@require_http_methods(['GET', 'POST'])
def my_view(request):
    # view code here
```

### @method\_decorator

The `@method_decorator` decorator is used to apply a function-level decorator to a class-based view. This is necessary because class-based views are not functions and do not support function-level decorators.

```python
from django.utils.decorators import method_decorator
from django.contrib.auth.decorators import login_required

class MyView(View):
    @method_decorator(login_required)
    def dispatch(self, request, *args, **kwargs):
        return super().dispatch(request, *args, **kwargs)
```

### Conclusion

Decorators are a powerful tool for modifying the behavior of views, functions, and methods in your Django application. Django provides several built-in decorators that you can use to modify the behavior of your views, functions, and methods. By using decorators, you can add functionality to your application without changing its code, making it easier to maintain