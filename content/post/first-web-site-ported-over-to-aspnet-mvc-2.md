+++
title = "First Web site ported over to ASP.NET MVC 2"
description = "Thoughts on porting my first Web site over to ASP.NET MVC."
draft = false
comments = true
date = "2010-05-23T08:00:00-05:00"
modified = "2010-05-22T21:22:48-05:00"
slug = "First-Web-site-ported-over-to-ASPNET-MVC-2"
blogengine = "1566136a-763d-408f-9ab1-65ecc2a9968f"
categories = ["review", "StrivingLife"]
tags = ["asp.net mvc"]
+++

<p>On Saturday (when I'm actually writing this, but I can't have 3 posts on one day, after my posting history the last handful of months) I finally ported a Web site over to ASP.NET MVC.</p>
<p>The existing Web site was for a client who just needs a simple, static, Web site, with a half dozen areas for content. However, if they were given the ability to directly post content to the site - news, specials, etcetera - I believe they might. There's also a weekly update that I perform that I wanted to simplify&nbsp;- not that it takes much time now - but that I didn't really do in this port, but now at least can.</p>
<p>There were perhaps 6 or 7 static HTML files, each&nbsp;of which, save one, was in its own sub-directory. On IIS 7.5, the application pool serving the site used approximately 6188 K of memory. Approximately. I used a mix of Visual Studio 2008 and Notepad to update the site, with Visual Studio 2010 being swapped in for the former the day after the final release. FTP was used to move the changed files to the production server.</p>
<p>I used Visual Studio 2010 to create the new site, and the Web publish functionality to, at the moment, publish it locally for FTPing it to the server. This might change, or I might just push the one View and two or four files that I need to push. I'll probably see what happens when I make that update.</p>
<p>Memory usage on the server for the application pool is now approximately 22348 K, with it jumping below that every so often.</p>
<p>For converting the static site over, it wasn't all that bad. I did have some repository cleanup to do as well, so I believe it took me just short of 2 hours, including some time researching on whether I could redirect a request to another Web site entirely using routing. I seem to recall Scott Hanselman had mentioned this in one of his videos, but it may have just been on redirecting to a Web forms page instead.</p>
<p>Overall, I'm pretty happy with the move, although now that I know memory usage jumped 16 M with ASP.NET MVC 2 being used (<em>without</em> any login functionality, by the way), I'm not sure I would have switched this particular site over so quickly. But there's only two others that I could have moved over, and one is going to be a pain, and the other is going to involve a level of complexity that this one did not.</p>
<p>I've known since <a href="http://strivinglife.com/words/post/Review-Professional-ASPNET-MVC-10.aspx">October</a> that I really wanted to work almost exclusively in ASP.NET MVC for the Web; I'm glad I'm finally able to start moving in that direction.</p>
