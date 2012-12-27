---
layout: post
title: Have you heard?
permalink: have-you-heard
published: true
---

"Hey, have you heard what happened to Newbie inc.?". *Tom looked worried saying this.*

"Yep" *I nodded.*

*Newbie inc website was hacked a few hours earlier. That happened just a day after they decided to open source the code for their site CMS and put it on github.*

*The site, powered by a cool ruby on rails application, had actually been online for a few months without any problem.* "It cannot be accidental, the code release should have had some role in this..." *Tom was puzzled.* 

*I opened a browser, got on the github page for Newbie's CMS, clicked a couple of links, and:* "There it is" *I said.* "They forgot to sanitise their code before releasing it."

"What happened exactly?" *Tom, a junior developer on our team was waiting for more.*

"When you run the rails command to create a new project, one of the files that gets generated is ```config/initializers/secret_token.rb``` *I explained.* 

"It contains instructions to initialise the application secret key used to verify the integrity of signed cookies. It is important to keep this key ... well ... secret."

"If a third party knows the key bad things can happen: the application will not be able to trust cookies it receives and, even worse, an attacker could craft cookies that result in [arbitrary code execution on the web server](http://daniel.fone.net.nz/blog/2013/05/20/a-better-way-to-manage-the-rails-secret-token/#comment-902646816)." 

"Newbie inc left the secret key used on the production server in the ```secret_token.rb``` file when it put the code online, thus opening the door to the attackers."

*Tom stared at the screen and asked* "I understand, but how could I avoid this?"

"First of all" *I said* "You need to separate the code from what is just configuration details of the application."

"Ok, this could get complicated ... Are there are libs to help with this stuff?" *Tom wasn't convinced*

"Yea" *I said,* "[You should really have signed up for my mailing list](https://spazidigitali.com)"

*I added:* "In the next message I'm going to send tomorrow, I'll show two different gems that help managing the configuration of your app. The first is purely YAML-file based, the second one is an ENV based solution, that nonetheless remains usable also through configuration files."

"Here is how they work", *then I went on, starting one of my lengthy talks ...*

