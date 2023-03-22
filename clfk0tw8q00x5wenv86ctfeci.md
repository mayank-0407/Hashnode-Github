---
title: "What is Chatterbot? How to use it!!"
datePublished: Wed Mar 22 2023 18:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clfk0tw8q00x5wenv86ctfeci
slug: what-is-chatterbot-how-to-use-it
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679423005133/507343fd-19e6-43b5-9233-4b9d155d0506.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1679423034886/b7642984-ecbb-44dc-aefa-774ca31db4ef.png
tags: bot, chatterbot, wemakedevs, mayankaggarwal, mayank

---

### Introduction:

Chatbots have become an essential part of modern businesses, especially in the customer service sector. They allow businesses to provide quick and efficient support to their customers without the need for human intervention. Python, being one of the most popular programming languages, has several libraries that allow developers to create chatbots easily. One such library is ChatterBot, an open-source Python library that allows developers to create chatbots quickly and easily. In this blog post, we will explore how to use ChatterBot to build a chatbot.

### What is ChatterBot?

ChatterBot is a Python library that allows developers to create chatbots using machine learning algorithms. It uses a conversational dialog system that allows the chatbot to learn from the conversation and generate appropriate responses to the user's input. ChatterBot provides several built-in storage adapters, logic adapters, and training corpora that make it easy to create a chatbot with minimal effort.

### Installing ChatterBot:

To install ChatterBot, open the command prompt or terminal and type the following command:

```plaintext
pip install chatterbot
```

This will install the latest version of ChatterBot on your system.

### Creating a Chatbot:

The first step in creating a chatbot is to create an instance of the ChatBot class. We can do this as follows:

```plaintext
from chatterbot import ChatBot

bot = ChatBot('MyBot')
```

In the above code, we have created an instance of the ChatBot class with the name "MyBot". We can customize the chatbot by passing several parameters to the constructor, such as storage\_adapter, logic\_adapters, and preprocessors.

### Training the Chatbot:

The next step is to train the chatbot using a corpus of data. A corpus is a collection of conversational data that the chatbot can use to learn from. ChatterBot provides several built-in corpora that we can use to train our chatbot. We can also create our own custom corpus of data. To train the chatbot, we can use the ChatterBotCorpusTrainer class, as follows:

```plaintext
from chatterbot.trainers import ChatterBotCorpusTrainer

trainer = ChatterBotCorpusTrainer(bot)

# Training the chatbot on the English corpus
trainer.train("chatterbot.corpus.english")
```

In the above code, we have created an instance of the ChatterBotCorpusTrainer class and passed our chatbot instance to it. We have then trained the chatbot on the English corpus by calling the train() method and passing the name of the corpus as an argument.

### Customizing the Chatbot:

ChatterBot provides several parameters that we can use to customize our chatbot. Some of the most commonly used parameters are:

* **storage\_adapter:** The storage adapter is responsible for storing the conversation data. ChatterBot comes with several built-in storage adapters such as SQLStorageAdapter, MongoDBAdapter, and RedisAdapter. We can choose the storage adapter that best suits our needs. For example, if we want to store conversation data in a MySQL database, we can use the SQLStorageAdapter as follows:
    

```plaintext
from chatterbot.storage import SQLStorageAdapter
from chatterbot import ChatBot

bot = ChatBot(
    'MyBot',
    storage_adapter=SQLStorageAdapter(
        database_uri='mysql://user:password@localhost/database_name'
    )
)
```

**logic\_adapters:** The logic adapter is responsible for selecting the best response for a given input. ChatterBot comes with several built-in logic adapters such as BestMatch, TimeLogicAdapter, and MathematicalEvaluation. We can choose the logic adapter that best suits our needs. For example, if we want to use the BestMatch adapter, which selects the responsewith the highest confidence value, we can add it to our chatbot instance as follows:

```plaintext
from chatterbot import ChatBot
from chatterbot.trainers import ChatterBotCorpusTrainer
from chatterbot.logic import BestMatch

bot = ChatBot(
    'MyBot',
    logic_adapters=[
        {
            'import_path': 'chatterbot.logic.BestMatch',
            'default_response': 'I am sorry, but I do not understand.',
            'maximum_similarity_threshold': 0.90
        }
    ]
)

# Training the chatbot on the English corpus
trainer = ChatterBotCorpusTrainer(bot)
trainer.train("chatterbot.corpus.english")
```

In the above code, we have added the BestMatch logic adapter to our chatbot instance. We have set the default response to "I am sorry, but I do not understand." and the maximum similarity threshold to 0.90. This means that the adapter will select the response with a confidence value of 0.90 or higher.

We can also create our own custom logic adapter by extending the LogicAdapter class and implementing the process() method. For example, if we want to create a logic adapter that selects the response based on the user's mood, we can create a class as follows:

```plaintext
from chatterbot.logic import LogicAdapter

class MoodAdapter(LogicAdapter):

    def __init__(self, **kwargs):
        super().__init__(**kwargs)

    def can_process(self, statement):
        return True

    def process(self, input_statement, additional_response_selection_parameters):
        if 'happy' in input_statement.text.lower():
            response = 'I am glad to hear that you are happy.'
        else:
            response = 'I am sorry to hear that you are not feeling well.'
        return response, None
```

In the above code, we have created a custom logic adapter that selects the response based on the user's mood. If the user mentions the word "happy", the chatbot will respond with "I am glad to hear that you are happy." Otherwise, the chatbot will respond with "I am sorry to hear that you are not feeling well."

### Using the Chatbot:

Once we have created and trained our chatbot, we can use it to generate responses to user inputs. We can do this as follows:

```plaintext
while True:
    try:
        user_input = input("You: ")
        bot_response = bot.get_response(user_input)
        print("Bot: ", bot_response)

    except (KeyboardInterrupt, EOFError, SystemExit):
        break
```

In the above code, we have created a loop that waits for user input and generates a response using the chatbot's get\_response() method. We have also handled several exceptions such as KeyboardInterrupt, EOFError, and SystemExit to gracefully exit the loop.

### Conclusion:

In this blog post, we have explored how to use the ChatterBot library to create a chatbot in Python. We have learned how to create a chatbot instance, train it using a corpus of data, customize it using storage and logic adapters, and use it to generate responses to user inputs. ChatterBot provides a simple and easy-to-use API that allows developers to create chatbots quickly and easily. With ChatterBot, anyone can create a chatbot that can learn and evolve with the user's input.

> You can visit pypi.org for more info. [clickhere](https://pypi.org/project/ChatterBot/)
> 
> Make Sure to Follow me on Hashnode.
> 
> Get to know more about me [here](https://mayankaggarwal.live/).