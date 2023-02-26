# Getting Mails from Your static webpage

---

<mark>Note: I m not Writing this technical blog to improve my CV or something. It is just i got to know about it 2-3 days ago and I tried it and I also liked it, so I thought to write a Blog on it.</mark>

Firstly, I would like to tell you that:

* I thought it is not possible to directly add a form to send emails to your email.
    

But, it is been said that google is your best friend so I found something.

## What is FromSpree?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674576829625/0407e3c7-8fae-4f82-ada8-dc21f3a9a005.png align="center")

* As is visible in the above Figure, it is a Free API that helps you to directly get your frontend webpage email.
    
* It can be used very easily and it is also safe. I also tried it on my Personal Website You can see it here! [https://mayankaggarwal.live](https://mayankaggarwal.live/)/
    
    ---
    

### Using FormSpree

* Firstly Create your Account in Formspree .[https://formspree.io/](https://formspree.io/)
    
* Now you will be able to see this + icon on the navbar.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674577487081/7f8457c6-6e39-4a3f-9f6f-76ae6ed9f634.png align="center")

* And Select New Form option.
    
* Give a suitable name for your form.
    
* Now You will be able to see a snippet like this:-
    

```xml
<!-- modify this form HTML and place wherever you want your form -->
<form
  action="https://formspree.io/f/mayznrwj"
  method="POST"
>
  <label>
    Your email:
    <input type="email" name="email">
  </label>
  <label>
    Your message:
    <textarea name="message"></textarea>
  </label>
  <!-- your other form fields go here -->
  <button type="submit">Send</button>
</form>
```

* Now create an HTML page and paste this snippet(make sure method of form is POST because POST is most safest).
    
* You r now good to go.
    
* Try it by Submitting the form and seeing your email you will be having a mail there.
    
    > So This was my thinking and method of use for Formspree. As a beginner, I shared my experience here.
    > 
    > You can check my website to get to know about me.
    > 
    > Link: [https://mayankaggarwal.live/](https://mayankaggarwal.live/)