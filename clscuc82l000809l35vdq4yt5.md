---
title: "What are docker file and docker compose file?"
datePublished: Thu Feb 08 2024 06:31:44 GMT+0000 (Coordinated Universal Time)
cuid: clscuc82l000809l35vdq4yt5
slug: what-are-docker-file-and-docker-compose-file
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707326663769/052c0d05-d5de-4b91-976d-4cf293ae7b0c.avif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707326700023/699cb1cb-a8db-49b5-bacc-67eb3a45808a.avif
tags: docker, docker-compose, wemakedevs, mayankaggarwal, mayank

---

Docker has become an extremely popular tool for developing, packaging, and deploying applications using containers. When working with Docker, two key configuration files enable you to define and run your containers - the Dockerfile and docker-compose.yml. Dockerfile and docker-compose.yml are the two most important configuration files which are used in Docker for defining and running images/containers:

* **Dockerfile:** This text file contains a set of instructions that tells Docker how to build a Docker image. This text file has no extension we simply name it a Dockerfile. Some common instructions in a Dockerfile include specifying a base image to build on, copying files into the image, installing dependencies, defining environment variables, exposing ports, and defining the command to run when a container is launched from the image. Dockerfiles automate the image-building process.
    
* **docker-compose.yml:** This YAML formatted file defines services, which are containers that run from Docker images. The docker-compose file allows you to define things like what Docker images to use for the services, ports to expose, volumes to mount, environment variables to pass, dependencies between services, and more. The docker-compose file allows you to define and configure all the services of your application in one place and then spin everything up with one docker-compose command.
    

## **How To Create A Dockerfile**

Dockerfiles are text files that contain instructions for building Docker images automatically. Defining your containers with Dockerfiles improves consistency, makes recreating containers easier, and allows them to be easily shared with others. In this blog post, we'll walk through writing a Dockerfile step-by-step.

### Step 1: Setting Up Your Project

* Create a new directory for your project and navigate into it:
    

```plaintext
mkdir my-docker-project
cd my-docker-project
```

![Creating Folder for Dockerfile](https://privatemedia.geeksforgeeks.org/wp-content/uploads/20240205221326/img1.png align="left")

### Step 2: Creating A Basic Application

* For demonstration purposes, let's create a simple Python application. Create a file named app.py with the following content:
    

```plaintext
# app.py
a=2
b=100
print(max(a,b))
```

**Output**

```plaintext
100
```

### **Step 3: Writing The Dockerfile**

* Create a file named **Dockerfile** (without any file extension) in your project directory. This file will contain instructions for building your Docker image.
    
* Open the Dockerfile using a text editor and add the following instructions:
    

```plaintext
# Dockerfile
# Use an official Python runtime as a base image
FROM python:3.11.4

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Run the application
CMD ["python", "app.py"]
```

Let's break down these instructions and know them indetailing

**FROM**: Specifies the base image for your application. In this case, we're using the official Python 3.11.4 image.

**WORKDIR**: Sets the working directory inside the container.

**COPY**: Copies the contents of the current directory into the container's working directory.

**CMD**: Specifies the command to run when the container starts.

![Dockerfile](https://privatemedia.geeksforgeeks.org/wp-content/uploads/20240205221838/img22.png align="left")

Fig 1.2 How your file directory will look like

### Step 4: Building The Docker Image

* Open a terminal in your project directory and run the following command to build your Docker image:
    
* This command tells Docker to build an image with the tag **my-docker-image** using the current directory **(.)** as the build context.
    

```
 docker build -t my-docker-image .
 docker images
```

![Building The App's Image](https://privatemedia.geeksforgeeks.org/wp-content/uploads/20240205223130/image.jpg align="left")

Fig 1.3 Building the app's image

### Step 5: Running the Docker Container

Once the image is built, you can run a container based on that image:

```
 docker run my-docker-image
```

![Running the docker image](https://privatemedia.geeksforgeeks.org/wp-content/uploads/20240205223407/img4.png align="left")

Congratulations! You've successfully created a Dockerfile and containerized your application.

## How To Create A Docker Compose Yaml File

Docker Compose is a powerful tool that allows developers to define and manage multi-container Docker applications. In this tutorial, we'll guide you through the process of creating a **docker-compose.yml** file step by step. By the end, you'll have a grasp of how to orchestrate your containers effortlessly.

To Know about the Installation of Docker, refer this - [Article](https://www.geeksforgeeks.org/docker-installation-on-windows/)

### Step 1: Project Setup

* If you haven't already, create a new directory for your project and navigate into it:
    

```
mkdir my-docker-compose-project
cd my-docker-compose-project


```

```plaintext
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Docker Compose File</title>
</head>
<body>
    <h1>Hello, This is Docker Compose Demo!</h1>
</body>
</html>

```

### Step 2: Define Your Services

* Create a simple web application by adding a **Dockerfile** and a basic HTML file.
    
* In your project directory, create the following files html/index.html and Dockerfile
    
* Save the following HTML code as html/index.html.Save the following dockerfile code with name "Dockerfile"
    

HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Docker Compose File</title>
</head>
<body>
    <h1>Hello, This is Docker Compose Demo!</h1>
</body>
</html>
```

* Save the following dockerfile code with name "Dockerfile"
    

```
# Use an official Nginx image as a base
FROM nginx:latest

# Copy the content of the "html" directory into the container
COPY html /usr/share/nginx/html
```

### Step 3: Create A Docker Compose File

* Now, create a file named **docker-compose.yml** in your project directory. This file will define your services, networks, and volumes.
    
* Open the **docker-compose.yml** file using a text editor and add the following content.
    
* This **docker-compose.yml** file specifies a service named "web" that builds from the current directory and maps port 8000 on the host to port 80 on the container.
    

```
# this is yaml file
version: '3'
services:
  web:
    build: .
    ports:
      - "8000:80"
```

![Docker compose file](https://privatemedia.geeksforgeeks.org/wp-content/uploads/20240205224129/img21.png align="left")

### Step 4: Build And Run With Docker Compose

* Open a terminal in your project directory and run the following command to build and run your services defined in the **docker-compose.yml** file:
    

```
# write this command in cmd
docker compose up
```

![Building Images through docker compose](https://privatemedia.geeksforgeeks.org/wp-content/uploads/20240205224712/image-(1).jpg align="left")

* Docker Compose will pull the necessary images, build your services, and start the containers. Visit [http://localhost:8000](http://localhost:8000) in your browser to see your web application.
    

![Demo Of Docker Compose](https://privatemedia.geeksforgeeks.org/wp-content/uploads/20240205224926/imgg_final.png align="left")

### Step 5: Cleaning Up

* When you're done, you need to stop the running containers and for that open new cmd and type:
    

```
 # write this command in cmd
docker-compose down
```

Congratulations! You've successfully created a Docker Compose file and orchestrated your multi-container application.

## **Conclusion**

In summary, Dockerfile defines what goes INTO a Docker image, while docker-compose.yml defines what containers to RUN from Docker images and how they work together to form an application. Dockerfile is more focused on the image building phase, while docker-compose is focused on running containers in production. They are often used together to dockerize full applications.

## Dockerfile And Docker Compose File - FAQs

### **Why We Use Docker Compose When We Have Dockerfile?**

> Docker Compose and Dockerfile serve different purposes in the containerization process, and they are often used together to streamline the development, deployment, and management of multi-container applications.

### **What Is The Difference Between Dockerfile And Docker-Compose?**

> Dockerfile is used to build a single container image, while Docker Compose is used to orchestrate multiple containers that work together as part of a larger application.

### **Why There Is No Extension Of Dockerfile?**

> The absence of a file extension for Dockerfile is by design. Docker looks for a file named Dockerfile in the build context directory by default. When you run the docker build command, Docker automatically searches for a file named Dockerfile in the build context and uses it for building the image.

### **Can We Containerize Machine Learning model?**

> Yes, containerizing machine learning models is a common and effective practice in the field of data science and machine learning. Containerization provides a way to package your machine learning model along with its dependencies, making it portable, reproducible, and easily deployable across different environments.