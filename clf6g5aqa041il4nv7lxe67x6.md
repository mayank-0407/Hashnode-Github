---
title: "Create Account from Excel File !!"
datePublished: Mon Mar 13 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clf6g5aqa041il4nv7lxe67x6
slug: create-account-from-excel-file
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677334663547/655053b5-4020-434d-aeed-c0b3e6c26d24.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1677334719562/5a543d1f-7ede-48d1-a00c-8cd0ab477285.png
tags: python3, pandas, wemakedevs, mayankaggarwal, mayank

---

Pandas is a popular Python library used for data analysis and manipulation. It provides data structures and functions for handling structured data, such as CSV, Excel, SQL databases, and more. In this blog post, we will discuss what Pandas is and how to create user accounts from an uploaded Excel file using Pandas in a Django view with code.

### Step 1: Install Pandas Library

To use Pandas with Django, you need to install the Pandas library. You can install it using pip:

```python
pip install pandas
```

### Step 2: Create a Django View

Next, you need to create a Django view that creates user accounts from an uploaded Excel file using Pandas. Here is an example:

```python
# views.py

import pandas as pd
from django.contrib.auth.models import User

def create_accounts_from_excel(request):
    if request.method == 'POST' and request.FILES['excel_file']:
        excel_file = request.FILES['excel_file']
        df = pd.read_excel(excel_file)
        for index, row in df.iterrows():
            username = row['username']
            email = row['email']
            password = row['password']
            user = User.objects.create_user(username=username, email=email, password=password)
            user.save()
        return HttpResponse("Accounts created successfully")
    else:
        return render(request, 'upload_excel.html')
```

In this example, we are defining a view `create_accounts_from_excel` that reads data from an uploaded Excel file and creates user accounts in Django. We are using Pandas to read the Excel file and convert it to a DataFrame. We are then iterating over the rows of the DataFrame using the `iterrows` method, and creating a user account for each row using the `User.objects.create_user` method. We are also saving the user account using the `save` method. If the accounts are created successfully, we return an HTTP response with a success message. We are also checking if the request method is POST and if the `excel_file` parameter is present in the `request.FILES` dictionary. If these conditions are met, we read the uploaded Excel file, else we render the template to upload a file.

### Step 3: Create an HTML Template for File Upload

Next, you need to create an HTML template that allows the user to upload an Excel file. Here is an example:

```python
<!-- upload_excel.html -->

<!DOCTYPE html>
<html>
<head>
    <title>Upload Excel File</title>
</head>
<body>
    <form method="post" enctype="multipart/form-data">
        {% csrf_token %}
        <input type="file" name="excel_file">
        <button type="submit">Upload</button>
    </form>
</body>
</html>
```

In this example, we are creating a form that allows the user to upload an Excel file. We are using the `enctype="multipart/form-data"` attribute to allow file uploads, and the `{% csrf_token %}` template tag to add a CSRF token to the form. When the user clicks the "Upload" button, the form data is submitted as a POST request to the `create_accounts_from_excel` view.

### Step 4: Create a URL Pattern

Finally, you need to create a URL pattern that maps to the `create_accounts_from_excel` view. Here is an example:

```python
# urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('create-accounts-from-excel/', views.create_accounts_from_excel, name='create_accounts_from_excel'),
]
```

In this example, we are defining a URL pattern `/create-accounts-from-excel/` that maps to the `create_accounts_from_excel` view.

That's it!

> ***Make Sure to Like and Follow my Bog.***
> 
> ***Get to Know me better*** [***here***](https://mayankaggarwal.live/)***.***