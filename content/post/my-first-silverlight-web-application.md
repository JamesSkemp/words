+++
title = "My first Silverlight Web application"
description = "I've finally created a Silverlight application. My first test queries against a WCF WebHttp service, parses the JSON data that's returned, and outputs it to the user."
draft = false
comments = true
date = "2010-07-19T22:37:00-05:00"
modified = "2010-07-19T22:50:48-05:00"
slug = "My-first-Silverlight-Web-application"
blogengine = "4309fa56-421a-4566-af87-77fe8fdc025c"
categories = ["StrivingLife"]
tags = ["wcf", "wcf webhttp", "silverlight"]
+++

<p>The more I do with Microsoft technologies the hard it becomes for me to want to move outside of them. With the .NET Framework and Visual Studio 2010, which is the best development tool I think I've ever used, it's easy to get sucked in.</p>
<p>Since I've wanted to experiment with it for a while, and since I needed to do some kind of development after slacking off this weekend, I looked into creating a simple Silverlight application that would use the same <a href="/post/tutorial-aspnet-c-sharp-wcf-webhttp-service-with-jquery-table-of-contents/">Web service I created late last month</a>.</p>
<p>I haven't hooked it up to any pages within the site yet, since it still needs some styling work, but ... here's&nbsp;<a rel="external" href="http://jamesrskemp.com/Projects/MusicServiceSilverlight">a Silverlight application using&nbsp;my MusicService project</a>. Note this requires Silverlight 4.0.</p>
<p>At this time it only works with one of the methods, and the output is a little clunky, but when I have time this week over lunch, or over the weekend, I'll try to clean it up.</p>
<p>This was a nice little exercise, involving a purely test project/solution to figure out how to make it work, and then adding a&nbsp;new project to my ASP.NET MVC 2.0 project that is the Web site. A cross domain policy file had to be added to the services site so that Silverlight could access it (otherwise it was erroring but seemingly without a message).</p>
<p>That's about two hours of work, and outside of about 15 minutes wasted because of some stupidity on my part (I'll blame the small amount of real-estate on my laptop monitor), it went fairly smoothly.</p>
