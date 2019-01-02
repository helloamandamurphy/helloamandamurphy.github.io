---
layout: post
title:      "Tic Tac Toe PTSD and Endless Loops"
date:       2019-01-02 17:31:53 +0000
permalink:  tic_tac_toe_ptsd_and_endless_loops
---


I don't think I'll ever play Tic Tac Toe again.

I've come to learn that when my code is broken, it is almost always broken in the smallest, most difficult to identify way.

So difficult, in fact, that when I was trying to complete my Tic Tac Toe CLI lab, (the pre-OO version), I had three technical coaches look at my code and go through it method by method before we could get the code to work--all three said, "It looks right." And yet, everytime I ran learn, a loop would hit so hard that it would crash my IDE. 

I would pore over my code for hours, looking for whatever it was that was causing a infinite loop--I thought I understood Ruby...maybe I thought I understood it but didn't. Maybe this programming thing wasn't going to work out. Maybe my mind just wasn't made for it. Maybe this course would be just another thing to add to the list of projects I had started and not finished.

But I could see my peers' code and mine looked very similar--it wasn't like they were writing in French, and I was over here writing gibberish. Maybe I was on the right track.

When I got to a point where I was out of ideas, I reached out to a technical coach, usually on the edge of tears. I had no idea how to use this magical tool "pry" that everyone was talking about. This lab really changed that, and if you can get a good technical coach to teach you how pry works, life will be much easier. (I have also seen Study Groups that cover this material.)

Eventually after a couple weeks of being stuck on this lab, we narrowed it down to my play method. While it looked correct, the final coach taught me a trick: Comment out every line in the method, and add each line back one at a time (typing the line as a new line, and deleting the old, commented out version.) If the code does break, you know which line is the problem. If the code doesn't break again and it magically works this time, hey, you have working code.

I still have no idea what was wrong with my play method. When I added each line in, line by line, re-typing my code in, the loop was magically gone.

I hope that trick can help others. It's still something I try. Other lessons learned: 

1) Reach out to a coach before you get to the point that you want to give up. Yes, I understand part of coding is figuring things out for yourself, but if you wanted to teach yourself code, there are a lot of free resources out there to do so. Part of what you're paying for is the assistance of the technical coaches.

2) The sooner you learn to use pry, the better. I think it would be helpful if it was in the curriculum much earlier than it is, especially since most of the coaches I worked with would tell me to use pry before I even knew what it was or how to use it. It's a very useful tool to debugging your code, but you have to know how to use it. 
