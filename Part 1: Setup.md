# Part 1 - Setup & Preparation

## Introduction

During my time learning Python, I was primarily interested in Discord bots, however, I found that once I reached a certain point, all the tutorials out there were too basic or covered the same things as a multitude of other tutorials. I’ve felt like there’s a general lack of creativity for bot tutorials, so I hope to break that mold with this step-by-step guide. We’re going to make the most of the Discord platform and use it to create a desktop-style application!

***By the end of this tutorial, you should be able to:***

+ Set up and configure a new bot account with Discord.
+	Create slash commands to accomplish various functions for the user.
+	Understand the various Discord events and methods of handling those.
+	Use Discord UI elements to create an interface with the bot.
+	And lots more things I can’t even think of right now!

For the tutorial, I’ll be demonstrating a bot that I came up with during the pandemic, when I was immersed in the RP community of Final Fantasy XIV. I managed an in-game venue, more or less a digital version of a real business. And while I was there, I wrote this bot to perform various administrative functions for me – to keep me sane. Profile creation, raffle management, a time clock, and many more functions are waiting to be developed. The first feature we’ll look at is the ability to make customizable embedded profiles for users!

Do note, this tutorial is going to be written for an intermediate-level audience, but hopefully accessible to newer developers as well. We’re going to look at object-oriented programming practices, how to keep code concise and clean, module structure, and more. There may be some times when you need to take a break and look up another tutorial – written or video – that explains a concept I’m discussing in more detail. Hopefully that won’t be the case, as I’ll try to explain everything as simply and thoroughly as possible, so, let’s get started!

One final comment. You’ll notice I use frogs as a recurring theme throughout the tutorial. I find that giving a bot some personality and a theme not only makes the user feel more comfortable, but honestly, it makes the development process a lot more fun and individualistic. Feel free to use your favorite animal!

## Discord Bot Account Setup
#### Create New Application Instance
Before we jump into things, there are a handful of setup tasks that we should take a look at. None of them are too difficult or time consuming, but they’re necessary to get up and running. First, we’ll take a look at the [Discord Developer Portal](https://discordapp.com/developers/applications) and create ourselves a bot account. After arriving at that page, ensure you see the words “My Applications”, and click the `New Application` button in the top right.

![A screenshot of an empty My Applications page on the Discord Developer Portal](https://user-images.githubusercontent.com/79615185/226673099-c65c8794-5797-48a0-8df0-f8f7e9f0219b.png)

You’ll be prompted to enter the name of your application…

![A screenshot of the prompt box for creating a new application.](https://user-images.githubusercontent.com/79615185/226673530-0d7d089c-405d-4b9f-b70c-0ab2f45cb59f.png)

#### Add Bot Instance
And that’s it! You have a bot! Go ahead and give it a description on the “General Information” page and then, from the navigation pane on the left, select the `Bot` option. You’ll be presented with… a blank page? Don’t fear, we’ll populate that now. Click the Add Bot button at the top right.

![A screenshot indicating the position of the New Bot button.](https://user-images.githubusercontent.com/79615185/226673707-a09c48f2-c6ac-49f2-a83e-5e395827f445.png)

There’ll be a prompt asking if you’re sure. If you’re not sure, you might as well close this tutorial now! On the next page, make sure you grab the secret token as soon as you can. Paste it in Notepad and SAVE IT. You only get to see it once, and that once is now. (Ironically, I forgot to save my Token after writing this and had to reset it…)

![A sample new bot token.](https://user-images.githubusercontent.com/79615185/226674030-eaf410a8-57a0-4191-ac51-1718149051cf.png)

#### Gateway Intents
Next up, if we scroll down, there will be a section entitled `Privileged Gateway Intents`. 

![The Privileged Gateway Intents section of the Discord Developer Portal.](https://user-images.githubusercontent.com/79615185/226674380-ee3a5e92-e8e6-4d2c-affd-652d888a99c0.png)

If you want to learn a bit more about what these mean read on, I found it a bit hard to understand at first too, otherwise the short version is you don’t need any of these enabled for this project. 

To understand what these intents are, it’s important to understand that Discord has flagged certain pieces of user information as “sensitive” or “privileged”. Think of it like a set of medical records. Only certain individuals have access to certain sections – psychology for mental health, for instance – and to get that access, they need special permission. The same concept applied here. We don’t get, or even want, access to this info unless we need it, in fact, the Discord team personally reviews bots in over 100 servers. So let me go over all three groups of intents.

+ **Presence:** This setting allows the bot to have access to users’ Rich Presence. If you’ve ever looked at someone’s profile and see something like this, the section at the bottom is this user’s Rich Presence data. A bot would rarely need to see this information, and since it could potentially be used to creep on someone, it’s privileged.

![Sample user profile with Rich Presence active.](https://user-images.githubusercontent.com/79615185/226680516-f66286f9-d0a4-4cdc-ae32-51b1f61adeb7.png)

+ **Server Members:** This particular intent is an umbrella category that covers four different pieces of sensitive information. The Add, Remove, and Update event for members within a guild – pretty straightforward definition of these events - as well as the Thread Members Update event, which is only called when a text channel thread has users added to it.
+ **Message Content:** This is the “*big*” one, and the most recent addition to the privileged intents list. This covers the literal content of messages sent within Discord. So words, images, files, and other message elements sent by human users are forbidden for the bot to access unless it has this intent. This is why the migration from text-based bot commands to slash commands was such a big deal when they rolled it out early-2022. For the duration of this course, you won’t need to access message content as all our functions can be called with slash commands.

#### OAuth2 Settings
Now that we’re finished with the bot user setup, head to the `OAuth2` tab on the left and click on the `URL Generator` sub-option. You should be presented with a page that looks like the following image.

![A screenshot of the Discord Developer Portal OAuth2 settings.](https://user-images.githubusercontent.com/79615185/226678530-c5a45651-c43c-47e1-85a7-740b7ee3f295.png)

Ensure you’ve selected the two scopes shown in the image – `bot` and `applications.commands`. This is simply going to tell Discord that it's okay that we're a bot and that we can create commands. Do note, if you select any other of the available scopes, a new line entitled `Select Redirect URL` will appear. These are for advanced bots that use external systems or APIs, so we won't be needing anything besides the two we've already selected.

After you toggle the `bot` option, another window should appear lower down - the `Bot Permissions` window. As with any good tutorial, I'm going to caution you to be wary of granting too many permissions to a bot, particularly if it goes into production. I've outlined the permissions we'll need for this tutorial in the image below, but I also found that if I'm testing my bot on a private server, simply ticking the `Administrator` permission works just as well. It's up to your preference, just, again, be cautious!

![A screenshot of the bot permissions options that will be required for this project.](https://user-images.githubusercontent.com/79615185/226682922-5ea25eda-91c0-46b7-98ce-97d59ab8f49a.png)

And with that, you can paste the provided link into a browser and invite the bot to your test server. Hopefully you're familiar with the process of getting a bot into a server, because I'm not going to cover that here. The bot won't show as online quite yet, so don't fret. We just want to be sure it's in the server and able to post in the test channel(s) you have set up.

## IDE Choice

Something I want to touch on just briefly before wrapping up is choice of IDE, or Integrated Development Environment. You most likely already have one of these on your computer - I highly doubt you're coding with Notepad, after all - but I just want to clarify that throughout this course I'll be using [PyCharm by JetBrains](https://www.jetbrains.com/pycharm/). If you're unsure on what IDE you like most, or if you're in the market for trying out a variety of options, give PyCharm a go. It's got a variety of extremely helpful functions and the interface is easy to use and very user-friendly.

## Python Packages

I finally want to finish off by installing two of the Python packages we're going to use during the tutorial. In fact, we're going to use these two libraries right off the bat! Run the following two commands separately in a command prompt/PowerShell window, or within your IDE's terminal. (You can also use the package installer that comes bundled with most IDEs as well. We'll be using the following two packages:
+ **Pycord** -- `pip install py-cord` -- A modern, easy-to-use, deature-rich, and async ready fork of the `discord.py` framework.
+ **Dotenv** -- `pip install python-dotenv` -- A library providing support for using `.env`, or environment, files.


That concludes the setup portion of this tutorial, so I'll end this section here. See you in the next guide!
