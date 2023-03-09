---
title: "Send an Email through Django Views!!"
datePublished: Thu Mar 09 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clf0qdw7200u4j9nvdbjx2wnj
slug: send-an-email-through-django-views
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677329352713/02b93cda-0662-42cb-882b-c8fa7120b2c1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1677329392758/ca864dd0-2314-43a1-b53c-5ee57b7c8f73.png
tags: django, wemakedevs, email-sender, mayankaggarwal, mayank

---

Sending emails is a common feature in web applications, and Django provides a built-in module for sending emails. In this blog, we will learn what sending mail is and how to send verification mails through Django.

What is Sending Mail? Sending mail is the process of sending an email message from one computer or device to another computer or device via the internet. The email message can contain text, images, and other attachments. Sending email is a core feature of many web applications, including registration, password reset, and account verification.

### Sending Verification Mails through Django:

Sending verification mails is a common feature in web applications. In Django, we can use the built-in EmailMessage class to send email messages. To send verification mails through Django, we need to follow the below steps:

### Configure Email Settings:

First, we need to configure the email settings in the [settings.py](http://settings.py) file. We can use the SMTP server to send emails. Here's an example configuration:

```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = 'your_email@gmail.com'
EMAIL_HOST_PASSWORD = 'your_password'
```

### Create EmailMessage:

Next, we need to create an EmailMessage object that contains the email content. Here's an example:

```python
from django.core.mail import EmailMessage

email = EmailMessage(
    'Subject',
    'Body',
    'from@example.com',
    ['to@example.com'],
    reply_to=['another@example.com'],
    headers={'Message-ID': 'foo'},
)
```

In the example above, we have set the subject, body, from email address, to email address, reply-to email address, and email headers.

### Send Email:

Finally, we can use the send() method to send the email. Here's an example:

```python
email.send()
```

### Sending Verification Mails with Django's built-in Auth System:

Django's built-in auth system provides an easy way to send verification emails to new users. The auth system creates a User object with the username, email, and password fields. To send a verification email, we need to follow the below steps:

1. ### Create User:
    
    First, we need to create a User object. Here's an example:
    

```python
from django.contrib.auth.models import User

user = User.objects.create_user(
    username='john',
    email='john@example.com',
    password='password'
)
```

In the example above, we have created a User object with the username, email, and password fields.

1. ### Generate Verification Token:
    
    Next, we need to generate a verification token. We can use the Django's built-in token generator to generate the token. Here's an example:
    

```python
from django.contrib.auth.tokens import default_token_generator

token = default_token_generator.make_token(user)
```

In the example above, we have generated a verification token using the default\_token\_generator.

1. ### Create and Send Verification Email:
    
    Finally, we can create and send the verification email. Here's an example:
    

```python
from django.core.mail import send_mail
from django.template.loader import render_to_string
from django.utils.html import strip_tags

subject = 'Verify your email'
html_message = render_to_string('email_verification.html', {'token': token})
plain_message = strip_tags(html_message)
from_email = 'from@example.com'
to_email = user.email
send_mail(subject, plain_message, from_email, [to_email], html_message=html_message)
```

In the example above, we have created a verification email template 'email\_verification.html' and passed the token to the template. We have used the send\_mail() function to send the email.

### Conclusion

Sending verification emails is a common feature in web applications, and Django makes it easy to send emails using its built-in email-sending framework. In this blog post, we discussed what is sending mail and how to send verification emails to the user, which helps in Securing the website.