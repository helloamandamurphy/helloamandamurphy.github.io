---
layout: post
title:      "PhotoLoco, JS + Rails API"
date:       2019-12-04 03:42:55 +0000
permalink:  photoloco_js_rails_api
---

## How hard could it be?
When it came to this project, I was feeling very optimistic and thought, “I’m a Rails pro now, this should be a cinch.” When I approached my Rails project, all of my problems were caused by being impatient and not wanting to watch through the walkthrough video. This time around I swore to code along with the entire walkthrough video series before going off on my own. While the walkthrough video for this project was very helpful, there were a lot of other aspects I had to figure out on my own, which made it more of a growing experience for me as a developer, and also made it feel much earned when I completed this phase of the project.

As I built my project, I documented the obstacles I encountered and how I resolved them, so that any other Flatiron School student might use it as a reference when they are running into issues with their own JavaScript / Rails API application. I also hope that it will give you a better picture of how my mind works when it comes to problem solving.

Starting off, I want to show you a bigger picture of where this fell in my coding journey. I completed my Rails project on July 17, completed the first half of my assessment on July 24, and completed the second half August 2. That’s a pretty big gap even for me. When I submitted my Rails project I took off a month, (outside of my assessment) because we were making the move from Colorado to Indiana. 

When we got back to Indiana, I started with the JavaScript section. I made it through the JavaScript section with pretty good time--JavaScript was the first language I had started with when I began experimenting with code--but I could write JS, but had a hard time seeing how everything fit together. Shortly after I finished the JavaScript module, Flatiron released V8 of their Web Development curriculum, and it was a major overhaul on the JS module. This meant that I had to complete an additional forty new lessons and labs, which pushed my project start date back about two weeks, but it provided a view of the big picture I didn’t have before. 

And then, it was finally time to start this project...four months after completing my Rails project.

That’s a long time to be away from Rails, and I found that most of my issues while working on this project, were on the back-end side of things.

## The Idea

So let’s get started:

Here’s the basic idea for my application: I’m trying to start my own photography side business, and one of the big parts of shooting photography (outside of a studio) is finding good locations for photos. I wanted to create a site where users could share photographable locations with other photographers. Locations are made by one user, but photos of the location can be uploaded by multiple users.

*  I’m not sure why, but I still have a hard time starting an application on my computer, and pushing that existing project to GitHub. (Go ahead, judge me, it’s just not something I do very often.) I found this page from GitHub helpful. https://help.github.com/en/github/importing-your-projects-to-github/adding-an-existing-project-to-github-using-the-command-line


* The second issue I ran into wasn’t code related--I wanted users to be able to save locations without addresses, but wasn’t sure if it was better to use longitude and latitude coordinates vs. plus codes vs. anything else. I couldn’t find any information that was conclusive, so I ran a poll on my Twitter. Longitude and Latitude won, so that’s what I went with to start out. (And if I find a better answer at a later date, I can change it.)


* The next thing I had to consider was how to save longitude and latitude into the database. I found this article very helpful: https://stackoverflow.com/questions/38469142/migration-with-a-decimal-number-with-2-trailing-digits
And I also thought this one was informative--it deals with how precise longitude and latitude is depending on how many decimal places are involved (you’ll have to scroll down a couple answers to find it.) https://stackoverflow.com/questions/159255/what-is-the-ideal-data-type-to-use-when-storing-latitude-longitude-in-a-mysql


* I am using PostgreSQL as a database for this project, so I also ran into this error when I tried to run `rails db:migrate`:
 ```
rails db:migrate
rails aborted!
ActiveRecord::NoDatabaseError: FATAL:  database "photoloco_development" does not exist
```
On my last project I had done a Google search and found a StackOverflow article that suggested running this command: `bundle exec rake db:create`, but you really just need to run `rails db:create` before running `rails db:migrate`.


* When I tried to open the Rails server for the first time, it said something was not defined in my LocationsController as it expected. It turned out that I had `API` capitalized in my LocationsController, and it should have been title cased `Api`.


* I also found out that I had messed up the project structure--this is kind of a funky project because it’s in between a Rails application (where you use the generated files for front-end and back-end), and a React / Rails application (where you typically have one directory for React, and one directory for Rails.) So you probably want something that looks like this:
	 javascript-project/
 		 backend/
   			 app/
   			 (...other rails files and folders)
 		 frontend/
    			index.html
    			style.css
   			 index.js
 		 README.md


* When I was working on the JS side of things, I kept getting this error: 
```
Uncaught (in promise) TypeError: Illegal constructor at locations.js:13 at Array.forEach (<anonymous>) at locations.js:13
```
It turns out that I had not loaded Location.js file into my index.html file. (Yikes.) 


* I really struggled trying to figure out ActiveRecord Associations between my models. I wanted users to be able to add many locations, and I wanted locations to have many photos, photos to belong to a location, and I wanted locations to have many tags and tags to have many locations (let’s say you want to find all locations tagged “waterfall”--the waterfall tag should pull up a list of locations.

I thought I had things figured out and was going to use `has_and_belongs_to_many` for the first time--until I Googled how to implement it and found the top article (written by a Flatiron grad) that was titled, “Why You Don’t Need has_and_belongs_to_many Relationships.” Shucks. (Only I’m sure I said much worse than shucks when I was trying to puzzle through these relationships.) https://flatironschool.com/blog/why-you-dont-need-has-and-belongs-to-many

So after staring at the screen and writing it out several ways in my notebook, I went to the Flatiron Slack channel, messaged a coach (or two) and also posted about my issue on Twitter. Avi ended up responding to my Tweet (bless him) and talked me through it. https://twitter.com/babiescatscode/status/1196460492056879104?s=20

We determined I needed a separate join table, connecting the Location table and the Tag table--the benefit being that if I wanted to add attributes to that relationship (beyond foreign keys) at a different time, I could.

Avi also referenced these two articles, so I’ve read and bookmarked them--check them out if you’re having a similar issue. https://guides.rubyonrails.org/association_basics.html#choosing-between-has-many-through-and-has-and-belongs-to-many
https://www.sitepoint.com/tagging-scratch-rails/


* One thing I finally put together while I was struggling through ActiveRecord Associations is that when you use `belongs_to` it can only belong to one instance of your model. (I really wish this relationship was called `belongs_to_a`) So for example: 
ModelA has_many :model_bs, but Model B belongs_to a :model_a. has_many :plural, belongs_to :one


* I was really struggling with the backend, even after I had figured out the ActiveRecord Associations, so I hopped in a Study Session with Howard--which I was really excited about, because I’ve heard so many positive things about him since I started, but he always seemed to be a lead in the module ahead of me. 

It turned out that I was missing a foreign key in my database--specifically in my Photos table. Something that Howard said that was really helpful was: If there is a belongs_to relationship, you need a foreign key in your table. If you think about it, the entry in your database should say: This is photo 123, it belongs to location 67. Makes sense, but I had not put that together before.


* At this point, I was a little overwhelmed. The walkthrough video I watched had one class with one attribute, and I was trying to make a similar application with four classes, each having one or more attributes. I would open my text editor and stare at my code for hours, experimenting, and I couldn’t seem to make any progress. I couldn’t get my seed data to save to my database, so I cut the Tag and LocationTag classes until I could get my Location and Photo classes to behave the way I wanted them to.

I have two thoughts on this: 1) I don’t think this would have been an issue if I hadn’t had a four month gap between my Rails project and my JavaScript / Rails project. 2) I think if I had worked solely on the back-end of things-- getting the database to work the way I wanted it to--first, before moving on to JavaScript, I wouldn’t have been stuck in this phase for so long.


* I came back the next day, and started reviewing nested attributes. This was a Rails topic that had gotten pretty rusty for me. This Flatiron lesson really helped.
https://learn.co/tracks/full-stack-web-development-v8/module-13-rails/section-7-associations-and-rails/basic-nested-forms

I also reworked my seed file, because it was unnecessarily complicated--I had stolen the original structure from a lab I had completed, and then implemented it on my last project (where my models had several more attributes.) I did have a little trouble figuring out how to set up a seed file with nested attributes, but I found this article on StackOverflow that helped.

https://stackoverflow.com/questions/37734016/how-add-nested-attributes-in-the-seeds-file-rails


* After I got my Location and Photo models working, I went back and started rewatching the entire walkthrough video, and I made notes in my code that explained what each function accomplished. I had some questions as to what `.json()` accomplishes*, and I really liked this explanation: 
https://developer.mozilla.org/en-US/docs/Web/API/Body/json


* On the JS side of things, my submit button was not saving the form inputs. I kept getting this error:
```
TypeError (no implicit conversion of Symbol into Integer):
app/controllers/api/v1/locations_controller.rb:13:in `create'
```

So I took a look at my create method in my LocationsController. I was running into an issue where I was getting my params back twice. I resolved that issue using pry, and tinkering with the console, but I’m still not exactly sure what was going on there.

I also forgot that in order to extract the nested attribute from the JSON, I needed to use bracket notation: `params[“location”][“photo”][“url]`--Okay, maybe I didn’t need to use it, but it did seem to be the only thing that worked at the time, and I don’t think I’ve used bracket notation since I worked on my Sinatra project...in April. 


* When I finally got my back-end to work the way I wanted it to, I realized I needed to add more HTML and CSS to my page. I think out of all of the languages and frameworks I’ve used, CSS is the most intimidating for me. There are just...so...many...options.

But I’m not one to roll over when I’m scared, so I decided to try CodePen for the first time. Yes, I said FOR THE FIRST TIME. And then I Googled for a tutorial video that walked me through styling, and I thought, “Huh, I didn’t think CSS had variables, but okay.” You can probably see where this is going. I copied and pasted my CSS in, and I learned very quickly that it was not a .css file, it was a .scss file. 

I had no idea what to do with a .scss file, so I started Googling, and I could not figure out what I was supposed to do with it. (If you’re having the same issue, please come find me on Twitter or Slack.) After a lot of frustration, and help from strangers on Twitter, (Thank you, lovely friends.) I figured out that this was a bit of a weird situation. 

If you build a normal Rails application, Sass is built in, and it’s just a matter of adding the styles to your views folder (does that sound right?) and running a line in your terminal to convert your .scss file to a second .css file. If you are using React, I think it works just the same way. But I was using Rails as an API, and vanilla JS, so I just needed to create a .scss file in my styles directory, download an Atom package (or a VSCode extension) and use it to compile the SCSS to CSS.

A couple of other notes: Don’t write in your CSS file, because it will get rid of your SCSS file. And don’t forget to update your stylesheet info in your HTML file...not that I have personal experience with either of those things.


* Getting down to the nitty, gritty, I also had to figure out how to generate links to Google Maps with user input coordinates--this StackOverflow post had my back:
https://stackoverflow.com/questions/30544268/create-google-maps-links-based-on-coordinates
`http://www.google.com/maps/place/lat,lng`

* Okay, so next on the agenda: adding a like button that would update a like count on a click. I added like as an attribute to my Location table, passed it through to my HTML/CSS/JS display. Then I tried to add a button I had found on CodePen. It was going pretty well, but I couldn’t figure out why my thumbs up icon was not there--it turns out it was a Font Awesome icon, so I had to make sure I had the correct line in my button HTML text, in this case `<i class="fas fa-thumbs-up">`, and then I also had to sign up for Font Awesome, and get this script tag to import their icons into my HTML page.   `<script src="https://kit.fontawesome.com/a8e960d804.js" crossorigin="anonymous"></script>`

* Trying to add an EventListener for a click, and kept getting this message: 
```
Uncaught TypeError: Cannot read property 'addEventListener' of null
at Locations.initBindingsAndEventListeners (locations.js:28)
at new Locations (locations.js:14)
at new App (app.js:4)
at index.js:2
``` in my console. 

This was because when I was trying to set my buttons attribute in initBindingsandEventListeners, I was attempting to set the button before any buttons existed (because none of my locations had loaded.) I was able to set `this.buttons` in my likeListener() function, which I called after my fetch request had been made in my `fetchAndLoadLocations` function. 

* When I came to incrementing my like count, I was testing it out with an alert, and was surprised to find that it was concatenating the numbers:
`${e.target.value + 1}` if 2 was the value of `e.target.value` my alert was returning 21 instead of 3.

I found this article on Stack Overflow suggesting adding a plus sign in front of a string to make it an integer. That’s pretty nifty. `${+e.target.value + 1}` You can also use parseInt() of course, which I think I ended up switching to. https://stackoverflow.com/questions/14496531/adding-two-numbers-concatenates-them-instead-of-calculating-the-sum


That’s a lot, I know--it’s been a real process.

Thanks for reading this far. I'm sure I'll add on more at a later time just to wrap things up, but that's it for now.

-A





