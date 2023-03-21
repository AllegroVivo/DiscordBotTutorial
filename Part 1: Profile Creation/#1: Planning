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

Here's how I've decided to organize the data:

+ Details
  - Character Name
  - Flavor URL
  - Accent Color
  - RP Jobs
  - Rates
+ At A Glance
  - Gender / Pronouns
  - Race / Clan
  - Orientation
  - Height
  - Age
  - Friend Code
+ Personality
  - Likes
  - Dislikes
  - Personality
  - About Me
+ Images
  - Thumbnail
  - Main Image
  - Additional

You'll notice that I've reordered things a bit - this order is going to be the most similar to the actual visual layout of the profile itself, so we're just using the structure here to help visualize the end result. You'll also notice that I have a group called `Personality` but I've also named a section "Personality" as well. Don't worry about this, the two won't get confused as we move forward, and that will become clear as we build the classes that will hold each group of data.

I'll refer back to this structure during the tutorial, so get familiar with it!
