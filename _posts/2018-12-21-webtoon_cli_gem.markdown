---
layout: post
title:      "Webtoon CLI Gem"
date:       2018-12-21 23:42:08 -0500
permalink:  webtoon_cli_gem
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/QaFhOpyFx_Y" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[View Webtoon on GitHub](https://github.com/helloamandamurphy/webtoon)
# Summary
A CLI gem that scrapes webtoon.com and returns top ten comics for various genres and age/gender categories.

***

# Languages and Tools Used
Object-Oriented Ruby, Ruby Gem, Nokogiri, Pry

***

# Features
* Scraped multiple URLs with Nokogiri for data
* Used Ruby class and instance methods to process scraped data
* Implemented logic and conditionals to accommodate user input

***

# Obstacles Encountered
1) I was really overwhelmed by the prospect of making my own CLI gem, but I started watching Avi's walkthrough video, and it really helped.

***

2) Another snag I hit was setting up my local environment. 

Up until this point, I had been using the Learn IDE. I heard from a couple Flatiron School coaches that it would be helpful to set up a local environment prior to starting this project. I wanted to give it a try. 

[This is a link to setting up your local environment on a Mac if you're a Flatiron Student.](https://help.learn.co/en/articles/900121-mac-osx-manual-environment-set-up)

I had no idea what I was doing, installed things incorrectly, and had to install it about three times. But eventually with the help of a Flatiron coach, I got it set up correctly. (And finally felt like a "real developer.")

***

3) Once I got that set up, I started with creating my gem. I couldn't get my classes or methods to work. It turns out this was because I was new to using `bundle gem gemname` and didn't realize there was a module that I needed to account for.
***

4) I started by building my CLI file first--I would create methods that were essentially shells that output test strings, but related to how I wanted the methods to work, and over time I fleshed them out. 

When it came time to scrape a site, the first site I wanted to use didn't work. I attempted to scrape the attractions off the Disney World website, but due to the high network security and use of JavaScript, I could not scrape the text. 

That project had also been an attempt to create a CLI version of an app I want to make, and in all honesty, it was overcomplicated for the requirements of this project, and was a waste of time. For students starting the project, I know it's difficult, but just try to do the bare minimum. (It's called minimum viable product, or MVP.) If you have time you can add to the project after you have your first draft complete.

***

5) I brought a couple new ideas to my project lead, and we went through the new webpages that I was interested in scraping. Scraping was definitely the most difficult and time consuming part of this process for me. When I started my second project, I worked on the Scraper class first, and once I got that working, I moved on to the CLI class, and then the Comic class.

***

6) The next difficulty I ran into was getting the scraped information into my Comic and CLI classes. I had a really difficult time conceptualizing how that information got where it needed to go.

In one case, I decided to hard code URL's and come back and correct it if necessary. Because there were top ten lists for multiple selectors, each selector had its own URL and that unique URL had to be scraped to retrieve the correct information.

I relied heavily on how the Student Scraper lab worked, as well as the [Best Restaurants CLI gem](https://github.com/dannyd4315/worlds-best-restaurants-cli-gem) example.

Because my project differs so much from these two labs when it comes to the multiple URL's, I believe there is likely a more efficient way to write the code I have written, but for now, the CLI gem works, and I am open to advice from others on how to improve it.

***

7) In my assessment we addressed an issue I noticed before the assessment: There was a bit of a delay when the gem scraped, initialized, and added details to the comics before printing them out. It turned out I was scraping the top ten page, but also each comic's individual page every time the user requested a top ten list.

***

# What's Next
One of the things my coach pointed out during our assessment was that I was not storing the scraped information in a database or store for later use. Because the top ten comics change frequently, I think that's okay, but it's something to consider if I build a similar gem in the future.

For now I'm content, feeling accomplished, and looking forward to learning about SQL.

Thanks for reading.
-A

**Connect with Me**
[GitHub](https://github.com/helloamandamurphy)
[Intercoastals](https://theintercoastals.com/)
[Instagram](https://www.instagram.com/intercoastals/)
[LinkedIn](https://www.linkedin.com/in/helloamandamurphy)
[Twitter](https://twitter.com/babiescatscode)
