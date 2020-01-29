---
layout: post
title:      "Rails Project: Hidden Mickey Pin Binder"
date:       2019-07-17 01:53:50 -0400
permalink:  rails_project_hidden_mickey_pin_binder
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/NW_GtF5zo7A" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
[View Pin Binder on GitHub](https://github.com/helloamandamurphy/hiddenmickey)

# Summary
A digital pin binder for users to keep track of their Disney pin collection.

***

# Languages and Tools Used
Ruby, Ruby on Rails, Google Omniauth, Pry, Bcrypt

***

# Features
* Created a Model-Controller-View (MVC) Rails application with Create, Read, Update, and Delete (CRUD) functionality
* Integrated multiple models using Active Record relationships, scopes, and validations
* Utilized Google OAuth option for user sign-in
* Rendered error messages when form requirements were unmet

***

# Obstacles Encountered

1) The first issue I ran into was more of a design issue. 

There are a limited number of pin designs and collections, but there is no comprehensive list or site that displays all Hidden Mickey pins that exist. Some years there are four waves of pins released, some years none are released.

I did a little Googling and found there was a [Pin Trading Database](https://www.pintradingdb.com/). It exists, but there were a lot of problems I could identify.
* It included all pins. There are a set number of Hidden Mickey pins, but there are likely an unknowable number of official Disney pins (the kind that are sold in the Parks.)
* Users created their own pins. Meaning there are likely thousands of duplicate pins in the database. 
* Identification numbers were based on the database ID numbers, not an officially assigned number.
* The pin photographs were bad.
* The site looks bad.
* The site shows a list of all users by username. (That's not the worst as far as security issues are concerned, but it makes me cringe.)

I decided I wanted to create my site with the following in mind:
* I wanted to narrow the pins in my database down to just Hidden Mickey pins.
* I want to input all pin information into the database (in the future) and have users add those pins to their collection, rather than create a new pin every time.
* I wanted to find an easy way to identify each unique pin. 

I did a little more Googling and could not find a comprehensive list of the Hidden Mickey series or their information. I found a few years online from various sites and saved them for future use. 

And then I did something that was out of character for me: I reached out to a stranger on social media. I had been following a Disney cast member for a year on social media, and so I messaged the cast member and asked if there was any place I might be able to find information on all of the Hidden Mickey series. The person responded quickly and explained that Disney used to have a site for it, as well as Pin checklists, but had done away with both. The person said they might have to dig around, but he/she could potentially send me a copy of the lists they had. (Ya know, since it used to be public information.)

I was a little disappointed to find out my idea wasn't new--Disney had the same idea before me, and had determined it wasn't worth the work it took to support the website. (In the words of Mickey Mouse, "Awwww shucks!") But I went ahead and decided to proceed with the project anyway.

***

2) After talking to my project coach about what I had planned, he suggested using PostgreSQL so that I could share my Rails project on Heroku once it was complete. That sounded great to me, because it was someting I wanted to do with my Sinatra project as well.

So I'm typing and building things and creating migrations, but then the migrations...won't migrate.
I ran `rake db:migrate` and the terminal slings back: 

```
rake aborted!
PG::ConnectionBad: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```

Okay, say what now? I open up my PostgreSQL app, and initialize the server. It's still not working. So I keep Googling, and I find the instructions on the [Postgres.app site](https://postgresapp.com/) very helpful. But I was still having issues, and receiving this error: 
```
ActiveRecord::NoDatabaseError: FATAL: database “hiddenmickey_development” does not exist
```


So I threw that error into Google and found [this Stack Overflow page](https://stackoverflow.com/questions/25611004/rake-dbcreate-throws-database-does-not-exist-error-with-postgresql).

The Stack Overflow response suggested running this in the command line: `bundle exec rake db:create`. So I ran that, followed by `rake db:migrate` and voila! I had a database.

I later found that you can just run `db:create` and then `db:migrate` and it does the same thing.

***

3) I was hoping that database issue was the only bump in the road, but I was wrong. 

I too experienced the classic, "My instance isn't saving" issue.

I had a similar issue in my Sinatra project (I tried to name an instance "request" which is a reserved word we don't use when building the things.) so I was convinced it was due to naming my instance "pin." (My User model was working just fine.) I went through and changed everything named "pin." It was a total mess, and did not change anything. 

I threw up my hands and asked the Slack Gods (the more experienced Flatiron School students) for any advice. One of the students suggested I throw a pry in the create method and run `@pin.errors`. I don't know why I hadn't thought of that, but I had not. 

I realized my pin instance would not save because I was not assigning a User to @pin in my create method, and I also had neglected to add `user_id` as an attribute on my Pins table. (For anyone not tracking: when you use a belongs_to relationship in your Rails models, it requires that you assign what the instance belongs to in your create method and your table.)

***

4) Call me inexperienced, because this is embarrassing. Once I had resolved my create issue with my Pin instance, I realized I had another issue: all of the users I had created had vanished (or they weren't saving.) It took me a second to realize why. 

When I'm working on a project with no real data, I don't like to add a million migrations to alter a table. I have been running `rake db:drop`, making changes, and then running `rake db:migrate`--all this time, not realizing that when you drop the table...the information in your table goes bye bye.

To save myself time, I created seeds for the first time! That way, every time I dropped the table, I could repopulate the new table with the same information.
***

5) I struggled with several other issues, but after my instance wouldn't save in the create method, I started watching these walkthrough videos by Flatiron School Technical Coach, Jenn Hansen. I can't emphasize how helpful these videos were--if you're just starting your Rails project, definitely watch them. (It's a lot of information, but I watch them on 1.5x speed and still catch it all.)

[You can find her Rails Walkthrough playlist here.](https://www.youtube.com/playlist?list=PLI_-ZfHw8Y6VqNTRKNu8yswERHSqxzNC_)

***

![](https://i.imgur.com/oM1eiWq.jpg)
Part of our Pin Collection

# What's Next
I have a few other topics I learned while working on this project, that I'm hoping to write future (more technical) blog posts about including: Omniauth, using enums, and possible nested forms.

As far as my Rails application goes, I would like to:
* Implement Bootstrap or custom CSS styling
* Change the new pin form so that if you select one option (perhaps what series the pin belongs to) the form would update to reflect pin information from pins only in that series. Example: If you have a pin with Aurora on it, you could select Aurora as the pin's subject, and the series select list would reflect only series that contained Aurora in them, as well as a photo of the pin you were adding to confirm you were adding the correct pin.
* Add all existing pin and series information I have into the database
* Add a button at the bottom of a pin show page that you could click and it would instantly add that pin to your collection.
* Add trading and selling functionality.
* Use Devise for sign up and log in.

Thanks for reading.
-A

**Connect with Me**
[GitHub](https://github.com/helloamandamurphy)
[Intercoastals](https://theintercoastals.com/)
[Instagram](https://www.instagram.com/intercoastals/)
[LinkedIn](https://www.linkedin.com/in/helloamandamurphy)
[Twitter](https://twitter.com/babiescatscode)
