---
layout: post
title:      "Webtoon CLI Gem"
date:       2018-12-21 23:42:08 -0500
permalink:  webtoon_cli_gem
---

When I started this project, I was discouraged. I was overwhelmed by the instructions and felt they used a lot of terms I hadn't seen before. If you're just starting your project, do your best not to get overwhelmed. Just start with Avi's CLI walkthrough video.

Another snag I hit is that I received conflicting information as to if it was best to work on a local environment or use the IDE we use for all of the previous labs. I decided to set up a local environment, but I had no idea what I was doing. I ended up installing things incorrectly, and installing everything about three times. Once I did get everything set up, I had never used the bundle gem (name) to create a gem, and couldn't figure out why my classes and my methods weren't working. I didn't know there was a module. 

What I ended up doing was watching Avi's CLI walkthrough video (I hadn't watched any of the videos from previous lessons because I didn't find them helpful.) and creating my gem step by step that way. I would create methods that were essentially shells that output test strings, but related to how I wanted the methods to work, and over time I fleshed them out. 

The first project I worked on attempted to scrape the attractions off the Disney World website, but due to the high network security and use of JavaScript, I could not scrape the text from the website. That project had also been an attempt to create a CLI version of an app I want to make, and in all honesty, it was overcomplicated for the requirements of this project, and was a waste of time. For students starting the project, I know it's difficult, but just try to do the bare minimum. 

I brought a couple new ideas to my project lead, and we went through the new webpages that I was interested in scraping. Scraping was definitely the most difficult and time consuming part of this process for me. When I started my second project, I worked on the Scraper class first, and once I got that working, I moved on to the CLI class, and then the Comic class. 

The next difficulty I ran into was getting the scraped information into my Comic and CLI classes. I had a really difficult time conceptualizing how that information got where it needed to go. In one case, I decided to hard code URL's and come back and correct it if necessary. Because there were top ten lists for multiple selectors, each selector had it's own URL and that unique URL had to be scraped to retrieve the correct information. I relied heavily on how the Student Scraper lab worked, as well as the Best Restaurants CLI gem example.  

Because my project differs so much from these two labs when it comes to the multiple URL's, I believe there is likely a more efficient way to write the code I have written, but for now, the CLI gem works, and I am open to advice from others on how to improve it. There seems to be a bit of a delay when the gem scrapes, initializes, and adds details to the comics before printing them out, which is probably my biggest concern that I'm hoping to address.

For now I'm content, feeling accomplished, and looking forward to learning about SQL. 

-A
