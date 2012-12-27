---
layout: post
title: Textcasting
permalink: textcasting
published: true
---

When looking at documentation about technical topics I like reading a lot more than a looking at a video. Especially when I'm dealing with reference information or how-tos about some technology. It's a lot easier to just get back at written documentation or reference it from emails or blog posts. I can even copy and paste code if I need to.

On the other hand screencasts are useful when learning about something new. When I need to get an overview on some library and there's a video for it, I immediately watch it. I did this with the awesome RailsCasts: watching the videos first and keeping the AsciiCast at hand for reference. For example: [this](http://railscasts.com/episodes/417-foundation) vs [that](http://railscasts.com/episodes/417-foundation?view=asciicast).

While a good formatted and highlighted code snippet is useful, Videos are more adapt than text when presenting *dynamic* information. One example is when showing what happens on a console when running commands. Another is when describing a particular interaction on a GUI.

Mixing text, code and tiny screencasts could be an effective way to write about a technical topic (I don't know if this is a word but I call them "textcasts")

Yesterday I was preparing this week's message to the mailing list and I needed to describe what happens when commands from the [heroku toolbelt](https://toolbelt.herokuapp.com/) are run. I didn't want to make the message longer than needed by including long console logs, so I thought that this could be the perfect use case to try doing it!

I had just [read on producthunt](http://www.producthunt.co/posts/1727) about [LICEcap](http://www.cockos.com/licecap/):

> LICEcap can capture an area of your desktop and save it directly to .GIF (for viewing in web browsers, etc)

It's a very small and unobtrusive app that let's you select an area of the screen, records what happens on screen and saves the video as an animated gif.
The gifs can be embedded in blog posts, emails, included in github comments, shared on a chat. 

Here is an example:

![editing this post](/images/editing_this_post.gif)

We can even have the clicks visible in the video which can be very useful when explaining how to interact with a GUI.

The generated images can be modified if needed with any program that permits editing animated GIFs. This is useful because sometimes we want to show processes that may halt for a while like a bash script that waits for a remote server response. In these cases it's better to adjust the timing in the recorded video to eliminate the wait, or to make it shorter.

I've used gimp to modify the animated GIFs created with LICEcap, changing the timing of some of the frames that were too long:

![Modify and image with GIMP](/images/gimp_editing.gif)


Here is a preview of one of the GIFs I've prepared for the newsletter:

![Heroku toolbelt - deploy](/images/heroku-deploy.gif)

Interspersing animations with text blocks might help clarify some points, plus it's super easy to make these screencasts and the results look nicer than plain images.  

