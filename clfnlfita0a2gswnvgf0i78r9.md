---
title: "Create Your First Bot Now within 2 min!!"
datePublished: Sat Mar 25 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clfnlfita0a2gswnvgf0i78r9
slug: create-your-first-bot-now-within-2-min
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679671508049/1b456c83-7657-4603-be49-efea93e8b18d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1679671591097/b07a83fd-b067-4662-bb02-270bd02e9282.png
tags: bot, python3, wemakedevs, mayankaggarwal, mayank

---

Discord is a popular platform for gamers and online communities to communicate and collaborate. Discord bots are automated programs that can be added to a server to perform various tasks, such as moderating chats, playing music, and providing information. In this blog, we will discuss how to create a Discord bot using Python and the [discord.py](http://discord.py) library.

### **Step 1:**

Setting up a Discord Bot Account Before we can create a Discord bot, we need to create a Discord bot account. Follow these steps:

1. Go to the Discord Developer Portal ([**https://discord.com/developers/applications**](https://discord.com/developers/applications)).
    
2. Click on the "New Application" button and give your application a name.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679669821234/596477e9-0aaa-48de-93b4-c7af8b28529d.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679669862755/0ec3b78a-755b-49b7-87cd-d372d2b1d93f.png align="center")
    
3. Click on the "Bot" tab on the left-hand side and click the "Add Bot" button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679669924128/59ffe32f-dfa3-40c8-9d1b-d1da01922b82.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679669950350/dc2c84ff-40de-41d0-b42f-c41a25b2552d.png align="center")
    
4. Customize your bot's name and profile picture.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679669980390/17f51dae-bab3-4746-9ad3-7d70f0f28a02.png align="center")
    
5. Click the "Copy" button under "Token" to copy your bot's token.
    

### **Step 2:**

Setting up the Development Environment To develop our Discord bot, we will use Python and the [discord.py](http://discord.py) library. Follow these steps:

1. Download and install Python ([**https://www.python.org/downloads/**](https://www.python.org/downloads/)).
    
2. Create a new folder for your bot and navigate to it in your terminal.
    
3. Run the command "pip install [discord.py](http://discord.py)" to install the [discord.py](http://discord.py) library.
    
4. Either you can go to Microsoft Store and search for python and install it.
    

### **Step 3:**

Writing the Bot Code Now that we have set up our bot account and development environment, we can start writing the bot code. Here's a basic example that responds to messages containing the word "hello":

```plaintext
import discord

client = discord.Client()

@client.event
async def on_ready():
    print('Logged in as {0.user}'.format(client))

@client.event
async def on_message(message):
    if message.author == client.user:
        return

    if 'hello' in message.content.lower():
        await message.channel.send('Hello!')

client.run('your-bot-token-goes-here')
```

This code creates a new Discord client and defines two event functions: **on\_ready()** and **on\_message()**.

* The on\_ready() function prints a message to the console when the bot has successfully logged in.
    
* The on\_message() function checks if the message contains the word "hello" and responds with "Hello!" if it does.
    

### **Step 4:**

* Running the Bot To run the bot, save the code in a file named "[bot.py](http://bot.py)" .
    
* Run the command "python [bot.py](http://bot.py)" in your terminal. Make sure to replace "your-bot-token-goes-here" with your bot's token.
    

### **Step 5:**

Adding the Bot to a Discord Server To add the bot to a Discord server, follow these steps:

1. Go to the Discord Developer Portal ([**https://discord.com/developers/applications**](https://discord.com/developers/applications)).
    
2. Click on your bot's application.
    
3. Click on the "OAuth2" tab on the left-hand side.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679670107312/ba78074b-9f84-4645-aae9-33da1194e895.png align="center")
    
4. In Default Application Link select In-app-application.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679670189352/de0de144-f6d1-437f-ae69-293f69c2f37e.png align="center")
    
5. Select the "bot" scope and check the boxes for the permissions you want your bot to have.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679670224918/ea19475e-f5dc-4c26-abc0-7df8e3c47a1d.png align="center")
    
6. Make Sure to Save Changes.
    
7. Now Navigate to Url Generator and select bot in Scopes and Select all the same permissions as selected above.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679670344750/c1afbf93-b77d-407a-ba92-096162e29a6d.png align="center")
    
8. Copy the generated OAuth2 URL and paste it into your web browser.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679670410157/5b22e65e-55f4-4557-8dfb-9e7a9d7344a4.png align="center")
    
9. Select the server you want to add the bot to and click "Authorize."
    

Congratulations! You have successfully created a Discord bot in Python using the [discord.py](http://discord.py) library. From here, you can continue to add more features and functionality to your bot, such as playing music or moderating chats.

### **Summary**

This blog provides a comprehensive guide on how to create a Discord bot in Python using the [discord.py](http://discord.py) library. The blog starts with an introduction to Discord bots and their benefits, followed by a detailed explanation of the steps involved in creating a Discord bot. The steps include setting up a Discord bot account, installing Python and the [discord.py](http://discord.py) library, writing the bot code, running the bot, and adding the bot to a Discord server. The blog also provides sample code snippets and instructions on how to customize the bot's functionality. Overall, the blog serves as a helpful resource for anyone looking to create a Discord bot in Python.