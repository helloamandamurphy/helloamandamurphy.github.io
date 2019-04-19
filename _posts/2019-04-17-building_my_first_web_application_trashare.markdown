---
layout: post
title:      "Building my first web application, Trashare"
date:       2019-04-17 15:44:47 -0400
permalink:  building_my_first_web_application_trashare
---


I'm a big picture kind of gal. Sometimes it's helpful, and sometimes it's a hindrance. I often underestimate how long it realistically takes to accomplish a task, because I'm more concerned about what I'm going to do once it's done. If my educational coach is reading this, she's likely nodding her head.

When it came to this Sinatra project, I tried to work with my big-picture orientation in mind. I completed some of the Sinatra lessons, but I started feeling a little anxious, not quite understanding how so many different components fit together. So I jumped ahead and watched a Study Group video of Avi building out a skeleton repository. 

I didn't understand everything as I was watching, but I've always benefitted from hearing others talk about their code and following along with videos. I created my own skeleton repository as I watched the video, and when it was done, I went back and started on the lessons I skipped over. I was able to apply the smaller parts of the Sinatra module to the "big picture" of building a web application with Sinatra, and when it came to the project, I completed the basic requirements for the project in about eight hours.

Something I read in the Career Prep course was that it was important to show that your portfolio projects were creating a solution to an existing project. While I agree that's likely important, as engineers, we aren't often the people creating the solutions-- we're the people who bring those solutions into existence. One of the blog posts I'd read about the Sinatra project is that a student said he had the hardest time thinking of what to do for his project.

I read through the project requirements, looked at another student's project (he'd hosted it on Heroku) and approached my husband, who is a masters student at Indiana University's HCI/d program, and asked him for some design ideas. It just so happened that he had completed a group project where users posted items they were trying to discard so artists could use them for recycled art projects. The project was titled "Trashare," a combination of the words "trash" and "treasure."

[The screens for the project can be seen here.](https://projects.invisionapp.com/share/M4QSTUXY2HC#/screens)


## Working on Trashare
I liked the idea of making one of his designs because then I could show prospective employers that I had made a product based on a customer design.

Trashare seemed pretty straightforward: there were users, the users had many posts, and the posts belonged to the users.

But the more I looked at the screens, I realized there were multiple types of posts that all needed to have CRUD functionality: Give (where users could post items they were trying donate to artists), Make (where artists could post what they had made and instructions on how to make crafts out of recycled items), and Request (where artists would post a list of items they were looking for.) In addition to these three post types, the posts all included tags.

I decided for the sake of time and making progress in the course, that I would aim to meet the project requirements (creating only two models: Users and Donations), and if time permitted I could add more models either before submitting the project, or later down the road when I was putting together my portfolio.

The User and Donations models didn't take long to complete, but then I had to do a little research to validate the new user information to prevent multiple users creating accounts with the same email or username. That didn't take too long after [reading this article.](https://guides.rubyonrails.org/active_record_validations.html) 

When I went to add the Request model, it seemed like a pretty simple copy-and-paste, and change variable names kind of job. It was not. The code broke in the RequestController's post method for creating a new object. After a couple days of attempting to debug it, reinstalling my entire local environment--the error eventually said it was coming from something inside my rvm folder--and having a technical coach take a look at the code, I still have not been able to make it work. If you're reading this and want to take a look at it, [the GitHub repo is here.](https://github.com/helloamandamurphy/trashare) 

Oddly, the Creation model works just fine, despite being made the exact same way.

At this point, I commented out the HTML view pages associated with the Request model and will return to it later down the road. I know very little about Rails, but I'm thinking I can rebuild the backend of this project using Rails, and add the CSS styling once I complete the Rails module. 

I tend to fixate on problems, but something I learned from my days as a PR writer is that you have to learn when to let a piece go. I exceeded my goal and hit a  roadblock trying to do extra. While I think it's important to learn why this isn't working, I want to continue moving forward until I can get another set of eyes on it. 

## An Update
#### (Two Days Later)
Once I submitted my project I shot up one more flare and asked the Sinatra Slack chat if anyone could figure out why my Request MVC was not working. I didn't expect anyone to look at it, because generally speaking, we're busy humans and it's difficult enough to take care of ourselves, let alone attempt to help others.

A couple hours later I checked the Slack, and I had two people respond to my cry for help. The information was helpful and understandable (sometimes when I'm trying to read StackOverflow responses I feel like I'm trying to read Egyptian hieroglyphs.)

Sinatra has it's own built in method and object named Request. By creating my own class and attempting to create a new object, I was overwriting the Sinatra::Request, which was critical to Sinatra working. After renaming my Request model, RequestController, and all the associated views and variables, the code worked flawlessly after a few tweaks.

This is pretty typical of me to find the solution after I step away from the project, so if you're a fellow programmer and you're stuck, take a step back, ask for help, and the solution might come to you.

## Future Work
I successfully created a User class and a Donation CRUD using Ruby and the Sinatra framework, and write the associated HTML pages populated with ERB text. Additionally, I was able to create two other CRUDs and their associated HTML pages. So what's left? 

* Create a tags class and add the ability to find all donations, requests, and crafts by tags.
* Create a search capability where the user can enter a search term and posts are returned based on search term.
* Add CSS styling

Another thing that would be beneficial is to meet with the design team again to discuss the site layout. Something I noticed while working is that the original screens did not include links for basic functionality--there is a link to view all the crafts, but no link for the user to add their own craft; a link to donate material, but not to view all the donations; and the home page and the marketplace pages are very similar, but the home page doesn't have much functionality. Being a developer and not a designer, when working with a design team or customer, I would prefer to touch back with them with proposed solutions and see if those solutions are approved, or if they have other ideas.

Thanks for reading!

-A
