---
layout: post
title:      "Building My First Web Application, "Trashare""
date:       2019-04-17 15:44:47 -0400
permalink:  building_my_first_web_application_trashare
---


<iframe width="560" height="315" src="https://www.youtube.com/embed/r0dmbmWLs6U" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[View Trashare on GitHub](https://github.com/helloamandamurphy/trashare)

# Summary
Trashare is a web application created to help members of the community exchange used items or trash for creative projects that use recycled materials to reuse waste.

***

# Languages and Tools Used
Ruby, Sinatra, SQLite3, Active Record, Pry, Shotgun, Bcrypt

***

# Features
* Built a Model-View-Controller application using multiple models with functionality to create, read, update, and delete (CRUD) entries
* Implemented Active Record for model relationships and validations
* Used bcrypt gem to securely save user passwords

***

# Obstacles Encountered

1) Seeing the big picture. 

When it came to learning Sinatra, I had a difficult time seeing the big picture of how everything fit together. I started a few lessons, but then switched to watching the walkthrough video of building a Sinatra application.

I didn't understand everything as I was watching, but I've always benefitted from hearing others talk about their code and following along with videos. I created my own skeleton repository as I watched the video, and when it was done, I went back and started on the lessons I skipped over. I was able to apply the smaller parts of the Sinatra module to the "big picture" of building a web application with Sinatra, and when it came to the project, I completed the basic requirements for the project in about eight hours.

***

2) Thinking of the project idea. 

Something I read in the Career Prep course was that it was important to show that your portfolio projects were creating a solution to an existing problem. While I agree that's important, as engineers, we aren't often the people creating the solutions--we're the people who bring those solutions into existence.

I read through the project requirements, looked at another student's project, and asked my husband for some design ideas. He's a masters' student at Indiana University's Human-Computer Interaction and Design program, and it just so happened that he had completed a group project where users posted items they were trying to discard so artists could use them for recycled art projects. The project was titled "Trashare," a combination of the words "trash" and "treasure."

[The screens for the project can be seen here.](https://projects.invisionapp.com/share/M4QSTUXY2HC#/screens)

***

3) Evaluating the design. 

Trashare seemed pretty straightforward: there were users, the users had many posts, and the posts belonged to the users.

But the more I looked at the screens, I realized there were multiple types of posts that all needed to have CRUD functionality: 
* Give (where users could post items they were trying donate to artists)
* Make (where artists could post what they had made and instructions on how to make crafts out of recycled items)
* Request (where artists would post a list of items they were looking for.) 

In addition to these three post types, the posts all included tags.

I decided for the sake of time and making progress in the course, that I would aim to meet the project requirements (creating only two models: Users and Donations), and if time permitted I could add more models either before submitting the project, or later down the road when I was assembling my portfolio.

***

4) Creating user validations.

The User and Donations models didn't take long to complete, but then I had to do a little research to validate the new user information to prevent multiple users creating accounts with the same email or username. That didn't take too long after [reading this article.](https://guides.rubyonrails.org/active_record_validations.html)

***

5) Creating the Request class.

When I went to add the Request model, it seemed like a pretty simple copy-and-paste, and change variable names kind of job. It was not. 

The code broke in the RequestController's post method for creating a new object. The error said it was coming from something in my rvm folder--so I thought that something in my local environment was messed up...and reinstalled the entire thing, which did not fix anything.

At this point, I was very proud of myself, because I stopped and asked for help. A couple days letter another student was able to help me identify the issue:

It turned out that I was trying to name a class with one of the [reserved words](http://reservedwords.herokuapp.com/words).

Sinatra has its own built in method and object named Request. By creating my own class and attempting to create a new object, I was overwriting the `Sinatra::Request`, which was critical to Sinatra working. After renaming my Request model, RequestController, and all the associated views and variables, the code worked flawlessly after a few tweaks.

***

# What's Next
In the future, I would like to:
* Create a tags class/functionality and add the ability to find all donations, requests, and crafts by tags
* Create a search capability where the user can enter a search term and posts are returned based on search term
* Add CSS styling

I would also like to revisit the design with the design team--something I noticed while working is that the original screens did not include links for basic functionality--there is a link to view all the crafts, but no link for the user to add their own craft; a link to donate material, but not to view all the donations; and the home page and the marketplace pages are very similar, but the home page doesn't have much functionality.

Being a developer and not a designer, when working with a design team or customer, I would prefer to touch back with them with proposed solutions and see if those solutions are approved, or if they have other ideas.

And as I'm revisiting this project months later, I would really like to give it another go as a more experienced developer. I could see myself:
* Rebuilding the back-end with Rails
* Rebuilding the front-end with React, or maybe Gatsby (something I want to learn next!)
* Adding seed data (I entered all of the data individually at the time, because I had no idea how to add a seed file.)
* Changing the database to PostgreSQL so I can host the project on Heroku or something similar
* Adding styling to match the original design--the front-end of this project is painful to look at!

***

Thanks for reading.
-A

**Connect with Me**
[GitHub](https://github.com/helloamandamurphy)
[Intercoastals](https://theintercoastals.com/)
[Instagram](https://www.instagram.com/intercoastals/)
[LinkedIn](https://www.linkedin.com/in/helloamandamurphy)
[Twitter](https://twitter.com/babiescatscode)

