+++
title = "BlogEngine.NET running on Cassini Personal Web Server"
summary = "Cassini Personal Web Server may just be what you need to quickly work with BlogEngine.NET for extension and theme creation."
draft = false
comments = true
date = "2009-11-12T07:06:00-06:00"
modified = "2009-11-12T07:20:08-06:00"
slug = "BlogEngineNET-running-on-Cassini-Personal-Web-Server"
blogengine = "6be60cb9-04fe-43f8-8a67-5dd7d7a7b9af"
categories = ["software"]
tags = ["blogengine.net", "iis", "cassini", "asp.net"]
+++

<p>While Cassini is a built-in Web server part of Microsoft Visual Studio, it's also available as a stand-alone application, thanks to the work of Dmitry Robsman.</p>
<p>The current version can be downloaded from this post regarding <a href="http://blogs.msdn.com/dmitryr/archive/2009/04/23/cassini-support-for-friendly-urls-routing.aspx">version 3.5.0.2</a> but requires that you first build the solution (the code is available under a MS-PL license).</p>
<p><a href="http://cassinipp.codeplex.com/">Cassini++</a> is also available from Codeplex, and has GUI improvements, among other changes (but is based on an older 3.5 version of Dmitry's release).</p>
<p>I decided to start with Dmitry's release and downloaded and built the application. Since I'm looking into building extensions for <a href="http://www.dotnetblogengine.net/">BlogEngine.NET</a> (to work against some spam issues and for general knowledge), as well as wanting to work on themes, I decided to see if I could get BE working on Cassini.</p>
<p>And it does, right out of the box (version 1.5.0.7).</p>
<p>On a Windows XP Professional box memory usage jumped to approximately 100 MB (which is about what I see on my own blog, with a little over 780 posts). On my Windows 7 Home Premium (64-bit) machine, however, memory usage sat under 40 MB.</p>
<p>Either way, I was able to login just fine.</p>
<p>Next I'll probably see if I can get an MVC Web site up and running on Cassini as well.</p>
