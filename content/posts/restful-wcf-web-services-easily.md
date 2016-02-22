+++
title = "RESTful WCF Web services, easily"
summary = "WCF WebHttp Services is the best of ASP.NET MVC and WCF. Or at least that seems to be the case."
draft = false
comments = true
date = "2010-06-15T22:47:00-05:00"
modified = "2010-06-15T23:09:45-05:00"
slug = "RESTful-WCF-Web-services-easily"
blogengine = "efcd62e7-87f9-45f7-a679-28e716d869af"
categories = ["technology"]
tags = ["asp.net", "wcf", "rest"]
+++

<p>I know I should know them better so I've been looking into WCF Web services, with a heavy lean towards an implementation based on REST principles.</p>
<p>After a good deal of research, where it was highly suggested that while ASP.NET MVC may make sense, WCF is still the way to go for Web services, I stumbled upon <a rel="external" href="http://blogs.msdn.com/b/endpoint/archive/2010/01/06/introducing-wcf-webhttp-services-in-net-4.aspx">WCF WebHttp Services</a>, which uses functionality released in .NET 4.</p>
<p>After a painless install via Visual Studio 2010's Extension Manager (<a rel="external" href="http://visualstudiogallery.msdn.microsoft.com/en-us/fbc7e5c1-a0d2-41bd-9d7b-e54c845394cd">more information</a>), and troubleshooting a stupid mistake on my end, I was able to quickly create a Web service that uses an assembly I had created to parse one of my <a rel="external" href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">iTunes Playlists to Xml</a> files and return a listing of tracks for a particular artist.</p>
<p>I am more than a little disappointed that it took months for me to find this, but the flexibility it allows, and the joy of working with it, makes up for it almost entirely.</p>
<h3>Updates</h3>
<p>10:04 P.M.: See also <a rel="external" href="http://msdn.microsoft.com/en-us/library/bb412169.aspx">WCF Web HTTP Programming Model</a>.</p>
