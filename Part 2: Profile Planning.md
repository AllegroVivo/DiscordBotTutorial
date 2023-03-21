# Embedded Profile Creation
## Part 1: Planning

### Sections

So let's take a look at what information we want to store in our profile. To make this process a bit easier, I've scoured a number of RP-based discords and put together a list of things included in most, if not all, character profiles I came across. This is by no means a comprehensive list of items, and if you think of different or additional things to add in one section or another as we go, I encourage you to do that, just don't let it confuse you while following the tutorial. Here's the character data we'll be working with:

+ Name
+ Friend ID
+ Gender
+ Race
+ Height
+ Age
+ Likes/Dislikes
+ Orientation
+ Rates (for characters that perform a contractable job)
+ Personality
+ Images
+ About Me / Biography
+ RP Job(s)
+ URL/Website

I want to add an additional item to this list, and I only mention this because if I didn't, you might see `Accent Color` in the list and wonder how somthing like a color is displayed in Discord, which doesn't have text color options. Well, what I'm actually referring to is the accent color attribute of a Discord embedded message. This is going to give the user further customization options, so we definitely want to give them a chance to set it to their favorite color. So we'll add that to the list too.
+ Accent Color

### Organization

Having all our data points is well and good, but the question remains as to how we'll organize these. We could easily make a single class simply called `Profile` that has an attribute for each of these pieces of data, but that would get *incredibly* bulky, unruly, and generally hard to manage. So, while we might have a class called `Profile` that contains all this data, I believe splitting it into groups of similar data items is going to give us the easiest way to manage **and** present the data to the end-user.
