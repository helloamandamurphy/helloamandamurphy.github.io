---
layout: post
title:      "Tic Tac Toe PTSD and Endless Loops"
date:       2019-01-02 17:31:53 +0000
permalink:  tic_tac_toe_ptsd_and_endless_loops
---


I don't think I'll ever play Tic Tac Toe again.

If you're a Flatiron School student, you know a big part of the first module is building a CLI Tic Tac Toe game, piece by piece.

It is from these labs that I have come to learn that when my code is broken, it is almost always broken in the smallest, most difficult to identify way.

Another thing I've come to realize is that I wait too long before asking for help. Flatiron School has a great team of technical coaches who are waiting in the wings most hours of the day to help you out when you get stuck. Learning to code has really taught me to stop being so stubborn and prideful and to ask for help when I need it.

While I was working on this lab, every time I ran the tests or tried to run my code, I would hit an infinite loop so hard it crashed my IDE.

I spent hours poring over my code, doubting myself, thinking that maybe I didn't understand code at all. But then I looked at the code my peers had written and my code didn't look too different. 

Eventually, when I reached out to the technical coach team, we went through my code, method by method, trying to find the issue. All three I worked with said, "It looks right." That was a confidence booster, but when we ran the tests, the loop would happen, and the IDE would crash again.

Eventually, after a couple weeks of being stuck on this lab, a technical coach and I narrowed it down to my play method. While it looked correct, Erika taught me a trick: **If you can narrow your issue down to one method, comment out every line in the method, and add each line back one at a time**--typing the line as a new line, and deleting the old, commented out version. If the code breaks, you know which line is the problem child. If the code doesn't break, and it magically works this time, hey, you have working code now.

I still have no idea what was wrong with my play method. When I added each line in, line by line, re-typing my code in, the loop was magically gone.

I hope this tip helps someone else as much as it helped me! It's still something I do.

One more thing I learned that really helped was learning how to use [pry](https://rubygems.org/gems/pry/versions/0.10.3). If you're a Flatiron Student starting with Ruby, I highly recommend joining a Study Group on how pry works, or pairing with a technical coach to learn about this Ruby gem.

-A

***

**Connect with Me**
[GitHub](https://github.com/helloamandamurphy)
[Intercoastals](https://theintercoastals.com/)
[Instagram](https://www.instagram.com/intercoastals/)
[LinkedIn](https://www.linkedin.com/in/helloamandamurphy)
[Twitter](https://twitter.com/babiescatscode)
