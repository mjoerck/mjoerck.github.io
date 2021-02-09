---
layout: post
title: Creating a simple Discord bot
subtitle: Code included!
tags: [coding, DIY, online]
---

Hello! Welcome to this short post about how I created a Discord bot for a community server (which I moderate). The bot in question has only got one purpose. It must not let anyone send messages in a specific Discord sever channel. The channel is reserved for commands starting with '!'. In other words the bot's job is to delete all messages that do not start with an exclamation mark. Please note that this is not a tutorial, it is meant more like a coding review.

### What language to write the bot in?

I originally contemplated writing the bot with node.js; however, I feel like Python is much faster to setup and to run on my server of choice - I do not want to spoil what I have chosen for hosting yet, perhaps you can guess it already?. I also feel much more at home with Python, thus it is my obvious language of choice.
Additionally, the Python Discord framework has got wonderful documentation, you can find it [here](https://Discordpy.readthedocs.io/en/latest/api.html) if you are interested in learning more.

After having chosen the programming language I proceed to code the bot. The mentioned requirements are very easy to implement. The code just needed a few lines to function:

```python
import Discord
import os

client = Discord.Client()

@client.event
async def on_ready():
    print('Logged in as {0.user}'.format(client))

@client.event
async def on_message(message):
    if message.author == client.user or message.author.bot:
        return
    if message.content.startswith('$hello'):
        await message.channel.send('Hello!')
    if str(message.channel) == "<CHANNEL-NAME>" and message.content.startswith('!') != True:
        await message.channel.purge(limit=1)

client.run('<TOKEN>')
```

The only non-standard library used is the Discord.py library - which can be installed normally by using pip. Feel free to borrow the code.

### Hosting the bot
With the bot working perfectly fine, the next step is hosting. Because I do not want to leave my PC on all the time I need some kind of hosting service or server. Since I have an abundance of Raspberry Pis laying around I will be utilising a Raspberry Pi Zero W for this project. The Zero W supports WIFI connectivity which is nice, besides this the Zero W has got 512 MB of ram and an ARM11 1 GHz processer which is more than adequate for this project.

I do not want to mess about making the bot start automatically on start-up, so I just start the Python script manually by using ```screen```, this also allows me to use the Zero W without running the bot if necessary.

#### ~MJOERCK
