---
layout: post
title: Handling Legacy Passwords In Devise
permalink: legacy-password-in-devise
published: true
---

A while ago I was working on a Ruby on Rails project which had to replace (or better sidestep and extend) an existing web application.

The legacy system had already been open to the public for quite some time, so there were the requirement to let the users keep their username and passwords, but move the login system to the new web application. In the RoR application I chose [Devise](https://github.com/plataformatec/devise) for the authentication subsystem, as it offered out of the box most of the features that were required, including handling signups and logins through social accounts (Twitter and Facebook).

What remained to be integrated was handling the migration from the old login system to the new one. I was relieved to see that the old system did not store the passwords in the clear in the database (oh I still see this happen sometimes...). Nonetheless it still stored a simple hash of the password. This is still just marginally better than storing the raw passwords so I wanted to avoid using the same system going forward on the new app. Devise instead uses a much better algorithm to handle the password hashing (bcrypt).

What was needed was:

- let the users login with their current username and password, without asking them to change it or reset. The users in this case are not particularly tech savvy and the risk by resetting their password was to lose them
- have the accounts migrated to the new database, use the improved security offered by Devise going forward.

What I did was the following:

- the old data was migrated to the new database, the user table was augmented with a ```legacy_password``` column where we copied the old hashed password
- on the first login the user is authenticated with the old password, if the check passed the ```legacy_password``` field is emptied and it is saved in the regulard devise field

This seamlessly transitioned the authentication to the new scheme while it minimized the window where the old password were on the new database.

Here is a simplified version of the code. To make it work I decided to _hook_ into devise's ```DatabaseAuthenticatable```:

{% gist 9828269 legacy_database_authenticatable.rb %}

The code overrides the ```valid_password?``` method to check and empty the old password, moreover it hooks also into the ```Recoverable``` module to make sure that if the user asks for a password reset we immediately blank the legacy password field. 

The code that checks the old password is in the ```Legacy::PasswordChecker``` class.

{% gist 9828269 legacy_password_checker.rb %}

The interesting bit here is the constant time string comparison function ```time_constant_compare```. This is something that you want to really do when comparing strings for authentication (whether they are hashed passwords or API tokens), as it makes a lot harder to use [timing attacks](http://codahale.com/a-lesson-in-timing-attacks/) on your application.

