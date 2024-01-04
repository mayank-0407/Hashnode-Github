---
title: "Mastering Node.js Templating with EJS: A Comprehensive Guide to Dynamic Web Development || Lesson - 3"
datePublished: Thu Jan 04 2024 06:31:12 GMT+0000 (Coordinated Universal Time)
cuid: clqytwqav000o08jl4ixu64a1
slug: mastering-nodejs-templating-with-ejs-a-comprehensive-guide-to-dynamic-web-development-lesson-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704120413850/420f71b5-ba12-41d2-a52e-7cab70f8bd20.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1704120454700/f74caaba-68f4-48fb-bb56-8ba989c55743.gif
tags: javascript, nodejs, wemakedevs, mayankaggarwal, mayank

---

Welcome to "Mastering Node.js Templating with EJS: A Comprehensive Guide to Dynamic Web Development." In the ever-evolving landscape of web development, the ability to craft dynamic and engaging user interfaces is paramount. Node.js, with its robust server-side capabilities, paired with the simplicity of EJS (Embedded JavaScript) templating, offers a powerful solution for developers seeking an efficient and flexible way to generate dynamic HTML content.

## Chapter 1: What is Templating?

In the realm of web development, templating is a technique that facilitates the dynamic generation of HTML content by embedding variables and logic into static HTML markup. This enables developers to create reusable templates for rendering content on the server side, providing a way to inject dynamic data seamlessly.

## Understanding Templating in Node.js

Node.js, a server-side JavaScript runtime, supports various templating engines, and one of the popular choices is EJS (Embedded JavaScript). EJS allows developers to embed JavaScript code directly into their HTML templates, making it easier to inject dynamic content.

### Setting Up EJS in a Node.js Project

To get started with EJS, you first need to install it as a dependency in your Node.js project. Use the following command to install EJS:

```bash
npm install ejs
```

Once installed, you can configure your Node.js application to use EJS as the templating engine. Create a simple Node.js server file (e.g., `app.js`) and set up EJS as follows:

```javascript
// Importing required modules
const express = require('express');
const ejs = require('ejs');

// Creating an Express application
const app = express();

// Setting EJS as the view engine
app.set('view engine', 'ejs');

// Define a route to render an EJS template
app.get('/', (req, res) => {
    // Rendering the 'index.ejs' template
    res.render('index', { title: 'Node.js Templating with EJS' });
});

// Start the server on port 3000
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
```

In this example:

* We use the Express framework to create a simple server.
    
* EJS is set as the view engine using `app.set('view engine', 'ejs')`.
    
* A route is defined to render an EJS template named `index.ejs`.
    
* The `res.render` method is used to render the EJS template and pass data (in this case, a title) to it.
    

## Creating a Simple EJS Template

Now, let's create a basic EJS template (`views/index.ejs`) to understand how templating works:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><%= title %></title>
</head>
<body>
    <h1>Welcome to <%= title %></h1>
    <p>This is a simple EJS template.</p>
</body>
</html>
```

In this template:

* `<%= title %>` is the EJS syntax for embedding the `title` variable passed from the server.
    
* The resulting HTML will dynamically display the provided title, showcasing the power of EJS templating.
    

By running your Node.js application and navigating to [`http://localhost:3000`](http://localhost:3000), you should see the rendered HTML with the dynamic content from the EJS template.

This sets the foundation for understanding templating in Node.js using EJS. In the upcoming chapters, we'll delve deeper into EJS features, such as interpolation, conditional statements, and loops, to build more dynamic and feature-rich web applications.

## Chapter 2: Using EJS

Now that we have EJS set up in our Node.js project, let's explore how to use it to create dynamic HTML content. In this chapter, we'll cover the basics of embedding JavaScript code within EJS templates and showcase how to use EJS to generate dynamic content.

## Embedding JavaScript in EJS

EJS allows developers to embed JavaScript code directly into HTML templates. This enables the execution of server-side logic to generate dynamic content. Let's modify our previous example to include dynamic data in the EJS template.

### Updated Route in `app.js`

```javascript
// ...

app.get('/', (req, res) => {
    const user = { username: 'john_doe', age: 25 };

    // Rendering the 'user.ejs' template and passing user data
    res.render('user', { user });
});

// ...
```

### Creating an EJS Template (`views/user.ejs`)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p>Username: <%= user.username %></p>
    <p>Age: <%= user.age %></p>
</body>
</html>
```

In this example:

* We've created a new route that renders the `user.ejs` template.
    
* The `user` object is passed to the template, providing dynamic data.
    
* The EJS template uses `<%= user.username %>` and `<%= user.age %>` to display the username and age dynamically.
    

## EJS Delimiters

EJS uses delimiters to differentiate between static HTML and embedded JavaScript code. The default delimiters are `<% %>` for scriptlet tags and `<%= %>` for output tags. However, you can customize these delimiters if needed.

### Custom Delimiters in `app.js`

```javascript
// ...

// Setting custom delimiters for EJS
app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));
app.locals.delimiters = '<% %>';

// ...
```

Now, you can use `<% %>` for scriptlet tags and `<%= %>` for output tags.

### Updated EJS Template (`views/user.ejs`)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p>Username: <% user.username %></p>
    <p>Age: <% user.age %></p>
</body>
</html>
```

## Conclusion

In this chapter, we've explored the basics of using EJS to create dynamic HTML content in Node.js. By embedding JavaScript code within EJS templates, we can generate dynamic data and render it on the server side. Understanding the use of delimiters is crucial for distinguishing between static HTML and dynamic content.

In the upcoming chapters, we'll dive deeper into advanced EJS features such as the views directory, interpolation syntax, and passing data to EJS templates, allowing you to build more sophisticated and dynamic web applications.

## Chapter 3: Views Directory

Organizing your project's structure is essential for maintainability and scalability. In this chapter, we'll delve into the importance of the "views" directory when working with EJS in a Node.js project. The "views" directory serves as a container for all your EJS templates, providing a clean and structured way to manage your views.

## Setting Up the Views Directory

By default, Express (the web application framework for Node.js) looks for views in a "views" directory. Let's create a simple "views" directory to house our EJS templates.

### Project Structure:

```plaintext
- /your-project
  - /views
    - user.ejs
  - app.js
  - package.json
```

### Updated `app.js` to Specify Views Directory:

```javascript
const express = require('express');
const path = require('path');

const app = express();

// Setting EJS as the view engine and specifying the views directory
app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

// ...

app.get('/', (req, res) => {
    const user = { username: 'john_doe', age: 25 };
    res.render('user', { user });
});

// ...
```

In this example:

* We use `app.set('views', path.join(__dirname, 'views'))` to specify that our "views" directory is located in the same directory as our `app.js` file.
    
* The `res.render('user', { user })` method is now looking for the 'user.ejs' template inside the "views" directory.
    

## Benefits of a Views Directory

1. **Organization:** Placing all your EJS templates in a dedicated "views" directory keeps your project structure neat and organized.
    
2. **Scalability:** As your project grows, having a central location for views makes it easier to manage and locate specific templates.
    
3. **Readability:** Team members, including yourself, can quickly understand where to find and update templates.
    

## Conclusion

Effectively structuring your project is a fundamental aspect of web development. In this chapter, we emphasized the significance of the "views" directory when working with EJS in a Node.js project. By organizing your templates in a dedicated folder, you enhance project maintainability and streamline development workflows.

As we progress through the guide, this organizational practice will prove valuable as we build more complex web applications using EJS. In the next chapters, we'll dive into the specifics of EJS syntax, data interpolation, and advanced features that will further enhance your templating capabilities.

## Chapter 4: Interpolation Syntax

Now that we've established the basics of EJS and organized our project structure with the "views" directory, let's delve into one of the core features of EJS—interpolation. Interpolation is the process of embedding dynamic values or expressions within your HTML templates.

## Understanding EJS Interpolation

EJS uses the `<%= %>` syntax for interpolation. Any valid JavaScript code placed between these delimiters will be evaluated, and the result will be inserted into the HTML output. This makes it easy to display dynamic content generated on the server side.

## Basic Interpolation Example

Let's modify our 'user.ejs' template to include dynamic data using EJS interpolation.

### Updated 'views/user.ejs':

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p>Username: <%= user.username %></p>
    <p>Age: <%= user.age %></p>
</body>
</html>
```

In this example:

* `<%= user.username %>` and `<%= user.age %>` are EJS interpolation tags.
    
* These tags will be replaced with the corresponding values from the 'user' object when the template is rendered.
    

## Using JavaScript Expressions

EJS interpolation supports any valid JavaScript expression. Let's enhance our example by including a more complex expression within the template.

### Updated 'views/user.ejs':

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p>Username: <%= user.username %></p>
    <p>Age: <%= user.age %></p>
    <p>Year of Birth: <%= new Date().getFullYear() - user.age %></p>
</body>
</html>
```

Here, we use `new Date().getFullYear() - user.age` as part of the interpolation. This expression calculates the user's year of birth based on their age.

## Conclusion

In this chapter, we've explored the power of EJS interpolation, which allows us to embed dynamic data and expressions seamlessly into our HTML templates. As you continue to work with EJS, mastering the interpolation syntax will be crucial for creating dynamic and personalized web pages.

In the upcoming chapters, we'll expand on this knowledge by covering more advanced features of EJS, such as passing data to templates and incorporating conditional statements and loops. Stay tuned as we continue our journey to mastering Node.js templating with EJS!

## Chapter 5: Passing Data to EJS

In the previous chapters, we explored the basics of EJS and learned about the interpolation syntax. Now, let's take a deeper dive into how to pass data from your Node.js application to your EJS templates. This is a crucial step in creating dynamic and customizable views.

## Passing Data to EJS Templates

When rendering an EJS template using `res.render()`, you can pass an object containing data as the second parameter. This data object can then be accessed within the EJS template.

### Updated 'app.js':

```javascript
const express = require('express');
const path = require('path');

const app = express();

app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

app.get('/', (req, res) => {
    const user = { username: 'john_doe', age: 25 };

    // Passing the 'user' object to the 'user.ejs' template
    res.render('user', { user });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
```

### Updated 'views/user.ejs':

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p>Username: <%= user.username %></p>
    <p>Age: <%= user.age %></p>
</body>
</html>
```

In this example:

* The `res.render('user', { user })` line passes the `user` object to the 'user.ejs' template.
    
* Inside the 'user.ejs' template, we use `<%= user.username %>` and `<%= user.age %>` to access and display the data.
    

## Dynamic Data Rendering

Passing data allows you to dynamically render content based on the server-side logic. You can use this approach to display user profiles, product details, or any other dynamic content that varies based on the data you provide.

### Enhanced 'views/user.ejs':

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p>Username: <%= user.username %></p>
    <p>Age: <%= user.age %></p>

    <!-- Display a personalized message based on age -->
    <% if (user.age >= 18) { %>
        <p>Welcome, <%= user.username %>! You are an adult.</p>
    <% } else { %>
        <p>Hello, <%= user.username %>! You are a minor.</p>
    <% } %>
</body>
</html>
```

In this enhanced example, we've added a conditional statement using EJS tags (`<% %>`). This allows us to display a personalized message based on the user's age.

## Conclusion

Passing data from your Node.js application to EJS templates opens up endless possibilities for dynamic content generation. As we continue our journey through this guide, we'll explore more advanced features of EJS, including conditional statements, loops, and building complete web pages with dynamic content. Stay tuned for the upcoming chapters!

## Chapter 6: Instagram EJS

In this chapter, we'll take a practical approach to further understand EJS by creating a simplified Instagram-like page. This example will involve rendering a list of posts with user-generated content.

## Setting Up the Project

Before we begin, ensure you have the necessary packages installed. If not, run the following command:

```bash
npm install express ejs
```

Now, let's create the project structure:

```plaintext
- /instagram-ejs
  - /views
    - home.ejs
  - app.js
  - package.json
```

### 'app.js'

```javascript
const express = require('express');
const path = require('path');

const app = express();

app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

app.get('/', (req, res) => {
    const posts = [
        { username: 'john_doe', caption: 'Enjoying a sunny day!', image: 'sunny.jpg' },
        { username: 'jane_smith', caption: 'Exploring new places.', image: 'explore.jpg' },
        { username: 'sam_jones', caption: 'Coding all day!', image: 'code.jpg' },
    ];

    res.render('home', { posts });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
```

### 'views/home.ejs'

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram-like Page</title>
</head>
<body>
    <h1>Instagram-like Page</h1>

    <% for (const post of posts) { %>
        <div style="border: 1px solid #ddd; padding: 10px; margin-bottom: 10px;">
            <p><strong><%= post.username %></strong></p>
            <p><%= post.caption %></p>
            <img src="<%= post.image %>" alt="<%= post.caption %>" style="max-width: 100%;">
        </div>
    <% } %>
</body>
</html>
```

In this example:

* We have a simple 'app.js' file that sets up an Express server and renders the 'home.ejs' template.
    
* The 'home.ejs' template receives an array of posts, and a loop (`<% for (const post of posts) { %>`) is used to iterate through the posts and display them on the page.
    

## Running the Project

Navigate to the project directory in the terminal and run:

```bash
node app.js
```

Visit [http://localhost:3000](http://localhost:3000) in your browser, and you should see the Instagram-like page with posts displayed.

## Conclusion

By creating an Instagram-like page, we've gained practical experience in using EJS to dynamically render content. The ability to loop through an array of data and display it on the page is a powerful feature of EJS. In the next chapters, we'll explore more advanced EJS concepts, including conditional statements, loops, and the creation of a more complex Instagram page with additional features. Stay tuned!

## Chapter 7: Conditional Statements in EJS

Conditional statements are a crucial part of any templating language, enabling dynamic content based on certain conditions. In this chapter, we'll explore how to use conditional statements in EJS templates.

## Basic Conditional Statements

Let's enhance our Instagram-like page example by adding a like button to each post. We'll use a conditional statement to display different messages based on whether the user has liked the post or not.

### Updated 'views/home.ejs'

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram-like Page</title>
</head>
<body>
    <h1>Instagram-like Page</h1>

    <% for (const post of posts) { %>
        <div style="border: 1px solid #ddd; padding: 10px; margin-bottom: 10px;">
            <p><strong><%= post.username %></strong></p>
            <p><%= post.caption %></p>
            <img src="<%= post.image %>" alt="<%= post.caption %>" style="max-width: 100%;">

            <!-- Conditional statement for the like button -->
            <% if (post.liked) { %>
                <p>You liked this post!</p>
            <% } else { %>
                <button onclick="likePost('<%= post.username %>', '<%= post.caption %>')">Like</button>
            <% } %>
        </div>
    <% } %>

    <script>
        // Dummy function for liking a post
        function likePost(username, caption) {
            console.log(`Liked post by ${username}: ${caption}`);
        }
    </script>
</body>
</html>
```

In this example:

* We've added a `liked` property to each post in the 'app.js' file to simulate whether the user has liked the post.
    
* Inside the 'home.ejs' template, we use a conditional statement (`<% if (post.liked) { %>`) to display different content based on whether the post is liked or not.
    

## Advanced Conditional Statements

EJS allows you to use various logical operators and comparison expressions in conditional statements. Let's add a feature to display a special message for posts with captions longer than a certain length.

### Updated 'views/home.ejs'

```html
<!-- ... (previous code) ... -->

<% for (const post of posts) { %>
    <div style="border: 1px solid #ddd; padding: 10px; margin-bottom: 10px;">
        <p><strong><%= post.username %></strong></p>
        <p><%= post.caption %></p>
        <img src="<%= post.image %>" alt="<%= post.caption %>" style="max-width: 100%;">

        <!-- Conditional statement for the like button -->
        <% if (post.liked) { %>
            <p>You liked this post!</p>
        <% } else { %>
            <button onclick="likePost('<%= post.username %>', '<%= post.caption %>')">Like</button>
        <% } %>

        <!-- Advanced conditional statement for special message -->
        <% if (post.caption.length > 50 && post.caption.length <= 100) { %>
            <p style="color: orange;">This caption is quite lengthy!</p>
        <% } else if (post.caption.length > 100) { %>
            <p style="color: red;">Wow, that's a really long caption!</p>
        <% } %>
    </div>
<% } %>

<!-- ... (remaining code) ... -->
```

In this addition:

* We use the `if-else if` structure to check the length of the post caption and display different messages accordingly.
    
* The color of the messages is also styled based on the length of the caption.
    

## Conclusion

Conditional statements in EJS provide a powerful mechanism for incorporating logic into your templates. By using these statements, you can dynamically adapt your content based on specific conditions, resulting in more personalized and engaging web pages.

In the next chapters, we'll explore the concept of loops in EJS, allowing us to efficiently handle arrays and iterate over dynamic data. Stay tuned for more insights into mastering Node.js templating with EJS!

## Chapter 8: Loops in EJS

Loops are essential for handling arrays and iterating over dynamic data in EJS templates. In this chapter, we'll explore how to use loops to enhance our Instagram-like page example.

## Basic Looping

Let's modify our 'home.ejs' template to include a list of comments for each post using a loop.

### Updated 'views/home.ejs'

```html
<!-- ... (previous code) ... -->

<% for (const post of posts) { %>
    <div style="border: 1px solid #ddd; padding: 10px; margin-bottom: 10px;">
        <p><strong><%= post.username %></strong></p>
        <p><%= post.caption %></p>
        <img src="<%= post.image %>" alt="<%= post.caption %>" style="max-width: 100%;">

        <!-- Conditional statement for the like button -->
        <% if (post.liked) { %>
            <p>You liked this post!</p>
        <% } else { %>
            <button onclick="likePost('<%= post.username %>', '<%= post.caption %>')">Like</button>
        <% } %>

        <!-- Advanced conditional statement for special message -->
        <% if (post.caption.length > 50 && post.caption.length <= 100) { %>
            <p style="color: orange;">This caption is quite lengthy!</p>
        <% } else if (post.caption.length > 100) { %>
            <p style="color: red;">Wow, that's a really long caption!</p>
        <% } %>

        <!-- Loop for comments -->
        <ul>
            <% for (const comment of post.comments) { %>
                <li><strong><%= comment.username %>:</strong> <%= comment.text %></li>
            <% } %>
        </ul>
    </div>
<% } %>

<!-- ... (remaining code) ... -->
```

In this example:

* We've added a `comments` property to each post in the 'app.js' file to simulate an array of comments for each post.
    
* Inside the 'home.ejs' template, we use a loop (`<% for (const comment of post.comments) { %>`) to iterate through the comments and display them as an unordered list.
    

## Looping with Index

EJS provides a way to access the index of the current iteration in a loop. Let's enhance our example by displaying the index of each comment.

### Updated 'views/home.ejs'

```html
<!-- ... (previous code) ... -->

<% for (const post of posts) { %>
    <div style="border: 1px solid #ddd; padding: 10px; margin-bottom: 10px;">
        <!-- ... (previous code) ... -->

        <!-- Loop for comments with index -->
        <ul>
            <% for (let i = 0; i < post.comments.length; i++) { %>
                <li><strong><%= post.comments[i].username %>:</strong> <%= post.comments[i].text %> (Index: <%= i %>)</li>
            <% } %>
        </ul>
    </div>
<% } %>

<!-- ... (remaining code) ... -->
```

In this addition:

* We use a standard `for` loop to iterate through the comments array.
    
* The index of each comment is displayed using `<%= i %>`.
    

## Conclusion

Loops are powerful tools for handling dynamic data, such as arrays of comments in our Instagram-like page example. EJS provides a clean and straightforward syntax for incorporating loops into your templates, making it easy to iterate over arrays and display content dynamically.

In the upcoming chapters, we'll explore more advanced features of EJS, including creating a complete Instagram-like page with user input, serving static files, and using includes for modular template structures. Stay tuned for a comprehensive understanding of Node.js templating with EJS!

## Chapter 9: Creating an Instagram Page with EJS

In this chapter, we'll take our Instagram-like page example to the next level by incorporating user input for posting comments and displaying a complete Instagram-like page.

## Adding User Input

Let's modify our 'home.ejs' template to include a form for users to add comments to each post.

### Updated 'views/home.ejs'

```html
<!-- ... (previous code) ... -->

<% for (const post of posts) { %>
    <div style="border: 1px solid #ddd; padding: 10px; margin-bottom: 10px;">
        <!-- ... (previous code) ... -->

        <!-- Loop for comments with index -->
        <ul>
            <% for (let i = 0; i < post.comments.length; i++) { %>
                <li><strong><%= post.comments[i].username %>:</strong> <%= post.comments[i].text %> (Index: <%= i %>)</li>
            <% } %>
        </ul>

        <!-- Form for adding comments -->
        <form action="/add-comment" method="post">
            <input type="hidden" name="postId" value="<%= post.id %>">
            <input type="text" name="username" placeholder="Your username" required>
            <input type="text" name="comment" placeholder="Add a comment..." required>
            <button type="submit">Post Comment</button>
        </form>
    </div>
<% } %>

<!-- ... (remaining code) ... -->
```

In this example:

* We've added a form to each post with input fields for the user's username and comment.
    
* The form includes a hidden input field (`<input type="hidden" name="postId" value="<%=` [`post.id`](http://post.id) `%>">`) to identify the post to which the comment will be added.
    
* The form has an action attribute set to "/add-comment" and a method attribute set to "post" to handle the form submission.
    

## Handling Form Submission

Now, let's modify our 'app.js' file to handle the form submission and update the server accordingly.

### Updated 'app.js'

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const path = require('path');

const app = express();

app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));
app.use(bodyParser.urlencoded({ extended: true })); // Parse form data

// Sample posts with comments
const posts = [
    { id: 1, username: 'john_doe', caption: 'Enjoying a sunny day!', image: 'sunny.jpg', liked: false, comments: [] },
    { id: 2, username: 'jane_smith', caption: 'Exploring new places.', image: 'explore.jpg', liked: false, comments: [] },
    { id: 3, username: 'sam_jones', caption: 'Coding all day!', image: 'code.jpg', liked: false, comments: [] },
];

app.get('/', (req, res) => {
    res.render('home', { posts });
});

// Handle form submission to add a comment
app.post('/add-comment', (req, res) => {
    const { postId, username, comment } = req.body;

    // Find the post by postId and add the comment
    const post = posts.find(p => p.id === parseInt(postId, 10));
    if (post) {
        post.comments.push({ username, text: comment });
    }

    res.redirect('/');
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
```

In this example:

* We've added the 'body-parser' middleware to parse form data sent in the POST request.
    
* The server now listens for POST requests to '/add-comment' and handles the form submission by adding the comment to the corresponding post.
    

## Conclusion

By incorporating user input and handling form submissions, we've transformed our Instagram-like page into a more interactive and dynamic web application. Users can now add comments to each post, providing a more engaging experience.

In the upcoming chapters, we'll explore serving static files, incorporating reusable templates with includes, and further enhancing our Instagram-like page. Stay tuned for more insights into mastering Node.js templating with EJS!

## Chapter 10: Serving Static Files

In web development, static files such as stylesheets, images, and client-side JavaScript play a crucial role in enhancing the user interface and overall user experience. In this chapter, we'll explore how to serve static files using Express in conjunction with EJS.

## Structuring the Project for Static Files

Let's enhance our Instagram-like page by adding a stylesheet for better styling. Create a new folder named `public` in your project directory. Inside this folder, create a file named `styles.css` with the following content:

### 'public/styles.css'

```css
body {
    font-family: 'Arial', sans-serif;
}

.container {
    max-width: 800px;
    margin: 0 auto;
}

.post {
    border: 1px solid #ddd;
    padding: 10px;
    margin-bottom: 20px;
}

.post img {
    max-width: 100%;
}

.comment-list {
    list-style-type: none;
    padding: 0;
}

.comment {
    margin-top: 10px;
}

.form-container {
    margin-top: 20px;
}
```

This stylesheet will be applied to our Instagram-like page to improve its visual appearance.

## Updating the 'home.ejs' Template

Let's update our 'home.ejs' template to include the stylesheet.

### Updated 'views/home.ejs'

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram-like Page</title>
    <link rel="stylesheet" href="/styles.css">
</head>
<body>
    <div class="container">
        <h1>Instagram-like Page</h1>

        <% for (const post of posts) { %>
            <div class="post">
                <p><strong><%= post.username %></strong></p>
                <p><%= post.caption %></p>
                <img src="<%= post.image %>" alt="<%= post.caption %>">

                <!-- Loop for comments with index -->
                <ul class="comment-list">
                    <% for (let i = 0; i < post.comments.length; i++) { %>
                        <li class="comment"><strong><%= post.comments[i].username %>:</strong> <%= post.comments[i].text %> (Index: <%= i %>)</li>
                    <% } %>
                </ul>

                <!-- Form for adding comments -->
                <form action="/add-comment" method="post" class="form-container">
                    <input type="hidden" name="postId" value="<%= post.id %>">
                    <input type="text" name="username" placeholder="Your username" required>
                    <input type="text" name="comment" placeholder="Add a comment..." required>
                    <button type="submit">Post Comment</button>
                </form>
            </div>
        <% } %>
    </div>
</body>
</html>
```

In this update:

* We added a `<link>` tag in the `<head>` section to include the 'styles.css' stylesheet.
    
* We applied CSS classes to various HTML elements for better styling.
    

## Serving Static Files with Express

Now, let's configure Express to serve static files from the 'public' folder. Update your 'app.js' file as follows:

### Updated 'app.js'

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const path = require('path');

const app = express();

app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));
app.use(bodyParser.urlencoded({ extended: true }));

// Serve static files from the 'public' folder
app.use(express.static(path.join(__dirname, 'public')));

// Sample posts with comments
const posts = [
    // ... (previous code) ...
];

app.get('/', (req, res) => {
    res.render('home', { posts });
});

app.post('/add-comment', (req, res) => {
    // ... (previous code) ...
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
```

In this update:

* We use `express.static` middleware to serve static files from the 'public' folder.
    
* The `express.static` middleware is added before our route handlers to ensure that static files are served before processing other routes.
    

## Running the Project

Ensure your server is running, and then open [http://localhost:3000](http://localhost:3000) in your browser. You should see the improved Instagram-like page with the applied styles from the 'styles.css' stylesheet.

## Conclusion

Serving static files is a crucial aspect of web development, enabling the inclusion of stylesheets, images, and client-side scripts in your web applications. By incorporating the `express.static` middleware, we can easily serve static files with Express, enhancing the visual presentation and overall user experience of our Instagram-like page.

In the next chapters, we'll explore more advanced EJS features, including template includes for modular structures. Stay tuned for further insights into mastering Node.js templating with EJS!

## Chapter 11: Includes in EJS

In web development, modularization is a key principle for maintaining clean and organized code. EJS provides a feature called includes, allowing you to modularize your templates by separating them into reusable components. In this chapter, we'll explore how to use includes in EJS to enhance the structure and maintainability of our Instagram-like page.

## Creating a Header Include

Let's start by creating a header include that will be shared across multiple pages. In your 'views' folder, create a new file named 'header.ejs' with the following content:

### 'views/header.ejs'

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><%= pageTitle %></title>
    <link rel="stylesheet" href="/styles.css">
</head>
<body>
    <div class="container">
        <h1><%= pageTitle %></h1>
    </div>
```

In this include:

* We've created a simple header with a dynamic `<title>` and a link to the 'styles.css' stylesheet.
    
* The `<h1>` tag displays the dynamic `pageTitle` variable.
    

## Using the Header Include in 'home.ejs'

Now, let's use the header include in our 'home.ejs' template:

### Updated 'views/home.ejs'

```html
<%- include('header', { pageTitle: 'Instagram-like Page' }) %>

<% for (const post of posts) { %>
    <div class="post">
        <p><strong><%= post.username %></strong></p>
        <p><%= post.caption %></p>
        <img src="<%= post.image %>" alt="<%= post.caption %>">

        <!-- Loop for comments with index -->
        <ul class="comment-list">
            <% for (let i = 0; i < post.comments.length; i++) { %>
                <li class="comment"><strong><%= post.comments[i].username %>:</strong> <%= post.comments[i].text %> (Index: <%= i %>)</li>
            <% } %>
        </ul>

        <!-- Form for adding comments -->
        <form action="/add-comment" method="post" class="form-container">
            <input type="hidden" name="postId" value="<%= post.id %>">
            <input type="text" name="username" placeholder="Your username" required>
            <input type="text" name="comment" placeholder="Add a comment..." required>
            <button type="submit">Post Comment</button>
        </form>
    </div>
<% } %>
```

In this update:

* We use `<%- include('header', { pageTitle: 'Instagram-like Page' }) %>` to include the 'header.ejs' file, passing a dynamic `pageTitle` variable.
    
* The header include provides consistent styling and structure across different pages.
    

## Conclusion

Includes in EJS allow you to break down your templates into smaller, reusable components, promoting a modular and maintainable code structure. In this chapter, we created a header include and incorporated it into our 'home.ejs' template, demonstrating how includes can enhance code organization and consistency.

Congratulations on embarking on your journey to master Node.js templating with EJS. Each chapter brings you closer to harnessing the full potential of EJS, empowering you to create dynamic and engaging web applications. Happy coding!

> Make Sure to Follow me to stay tunned for next lesson.