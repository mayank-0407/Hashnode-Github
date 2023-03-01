# How to use DateTimeField in Django Models !!

Django's `DateTimeField` is a useful field that allows you to store and manipulate date and time data in your models. In this blog, we'll take a closer look at how to use `DateTimeField` in Django, with code examples and images to help illustrate the concepts.

### Step 1: Create a Django Model

To use `DateTimeField`, we first need to create a Django model that includes this field. Here's an example:

```python
from django.db import models

class Event(models.Model):
    name = models.CharField(max_length=255)
    start_time = models.DateTimeField()
    end_time = models.DateTimeField()
```

In this example, we've created a simple model called `Event` with a `name` field and two `DateTimeField` fields called `start_time` and `end_time`.

### Step 2: Migrate the Model

After creating the model, we need to create a database table to store the data. We do this by running migrations:

```python
python manage.py makemigrations
python manage.py migrate
```

This creates a new database table called `myapp_event`, with columns for the `id`, `name`, `start_time`, and `end_time` fields.

### Step 3: Use the DateTimeField in Views

We can now use the `DateTimeField` in our views to create new `Event` instances. Here's an example view that creates a new `Event`:

```python
from django.shortcuts import render
from myapp.models import Event
from django.utils import timezone

def create_event(request):
    if request.method == 'POST':
        name = request.POST.get('name')
        start_time = timezone.now()
        end_time = timezone.now()
        event = Event.objects.create(
            name=name,
            start_time=start_time,
            end_time=end_time
        )
        event.save()
        return redirect('/events/')
    else:
        return render(request, 'create_event.html')
```

In this view, we create a new `Event` instance with the `name`, `start_time`, and `end_time` fields. We use [`timezone.now`](http://timezone.now)`()` to set the `start_time` and `end_time` fields to the current date and time.

### Step 4: Display the DateTimeField in Templates

Finally, we can display the `DateTimeField` in our templates. Here's an example:

```xml
{% for event in events %}
  <h2>{{ event.name }}</h2>
  <p>Start Time: {{ event.start_time }}</p>
  <p>End Time: {{ event.end_time }}</p>
{% endfor %}
```

In this template, we use `{{ event.start_time }}` and `{{ event.end_time }}` to display the `start_time` and `end_time` fields for each `Event` instance.

### CONCLUSION

In conclusion, `DateTimeField` is a powerful field in Django that allows you to store and manipulate date and time data in your models. By following the steps outlined above, you can use `DateTimeField` in your Django project to create models that store date and time data, and display that data in your views and templates.