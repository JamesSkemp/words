+++
title = "Browser environments for testing"
description = "The three virtual environments I'd recommend for in-depth browser testing, for Web applications."
draft = false
comments = true
date = "2008-11-20T22:40:00-06:00"
modified = "2008-11-20T22:44:23-06:00"
slug = "Browser-environments-for-testing"
blogengine = "f130d500-7164-40fd-8678-f19d5ada3cfd"
categories = ["Internet", "software"]
tags = ["virtualization", "microsoft", "internet explorer", "firefox", "opera", "safari", "chrome", "analytics", "web development"]
+++

<p>
In <a href="/words/post/How-to-really-compact-Virtual-PC-hard-drives.aspx">a previous post</a> I mentioned using virtual machines for testing.
</p>
<p>
Here&#39;s the three virtual machines that I feel cover the most options for browser testing (on Windows):&nbsp;
</p>
<h3>Current versions</h3>
<p>
Looking at the top 10 browsers for this site, using data from Google Analytics, we have; Internet Explorer, Firefox, Safari, Chrome, Mozilla, Opera, Playstation 3, Konqueror, SeaMonkey, and Camino.
</p>
<p>
Of those, Internet Explorer and Firefox, obviously, account for the largest amount of traffic, at about 86% of all visits. Safari is a respectable 6.6%, Chrome at about 2.7%, Mozilla at 2.1%, and Opera at 1.8%.
</p>
<p>
Some&nbsp;may think&nbsp;I&#39;m a bit&nbsp;off, but I&nbsp;consider Opera a fairly good browser, while Mozilla doesn&#39;t much concern me. So, that gives us our top five browsers, all of which&nbsp;can&nbsp;be installed on Windows.&nbsp;
</p>
<p>
So, any&nbsp;test&nbsp;environment for current versions of browsers (on Windows), should include the following (in order of importance).
</p>
<ol>
	<li>
	<div>
	Internet Explorer 7
	</div>
	</li>
	<li>
	<div>
	Firefox 3
	</div>
	</li>
	<li>
	<div>
	Safari 3
	</div>
	</li>
	<li>
	<div>
	Chrome 0
	</div>
	</li>
	<li>
	<div>
	Opera 9
	</div>
	</li>
</ol>
<p>
There&#39;s talk that Chrome may replace Firefox, if Google stops supporting Mozilla, so while Chrome may have low usage numbers, it&#39;s fairly standards-compliant.
</p>
<p>
This is also why I feel that not including Opera would be a very big mistake.
</p>
<p>
This rounds out our first virtual machine to 5 unique browsers.
</p>
<h3>Previous versions&nbsp;</h3>
<p>
While it would be great if it wasn&#39;t the case, you&#39;ll always need to support older versions of popular browsers.
</p>
<p>
Again, looking at Google Analytics for this site, almost 25% of Internet Explorer users are using version 6. Firefox, which supposedly has some issues in version 3, that are keeping users back in version 2, is about the same, with 75% of users on version 3.0.3 or 3.0.4 (I suppose there may be some overlap there).
</p>
<p>
Most other browsers don&#39;t actively support so many previous versions, which means that a virtual environment for past versions of browsers can stick with the following.
</p>
<ol>
	<li>
	<div>
	Internet Explorer 6
	</div>
	</li>
	<li>
	<div>
	Firefox 2
	</div>
	</li>
</ol>
<h3>Upcoming versions</h3>
<p>
This virtual machine is really focused on browsers currently in beta, or that may otherwise not be in the top listing.
</p>
<p>
Primarily, that means the following should almost certainly be included.
</p>
<ol>
	<li>
	<div>
	Internet Explorer 8
	</div>
	</li>
</ol>
<p>
That&#39;s right, Internet Explorer 8. That&#39;s all I&#39;d absolutely need, especially looking at stats.
</p>
<p>
However, to a great extent, Chrome, like most of Google&#39;s other <strike>products</strike> applications is truly a beta browser (and one that I&#39;ve had numerous issues with, probably due to that fact) and that might suggest that it should truly be installed in this environment.
</p>
<h3>What about Linux and Mac?&nbsp;</h3>
<p>
The top browsers for Linux, again according to this site, are Firefox and Mozilla, which should&nbsp;function the same as they are on Windows (and, again, I consider Firefox and Mozilla to be basically the same). It&#39;s extremely easy, and free, to get started with any number of Linux environments, but I just don&#39;t know that it makes all that much sense. (Keep reading for the clarification of this statement.)
</p>
<p>
For Mac&nbsp;we have Safari and Firefox. The latter should be very similar to the Windows version.
</p>
<p>
For Safari Apple was kind enough to give Windows users this browser. As to whether it&#39;s the same as the Mac version, well, it looks very similar. But, unless you&#39;re willing to pay the Apple premium, the Windows version should suffice.
</p>
<p>
For these reasons, basic Web development doesn&#39;t need to dive too deep into Linux and Mac environments.<sup>1</sup>
</p>
<h3>Mobile browsers?</h3>
<p>
But what about browsers on mobile devices?
</p>
<p>
Both Safari, Opera, and Internet Explorer have mobile versions available (in the case of Opera, they have two), which will definitely change the output of your site.
</p>
<p>
To some extent <a href="/lynx/">Lynx</a> fills this hole by providing a text version of your site, and therefore might make sense installed on a virtual machine.
</p>
<p>
The standard Opera browser also provides a mobile-like &#39;emulator&#39; for your site, by way of the Small View functionality.
</p>
<p>
However, for the mobile version of Internet Explorer (which won&#39;t be tracked by Analytics, as it doesn&#39;t support JavaScript (speaking of Windows Mobile 6)) accessing an emulator is not quite as easy.
</p>
<p>
As to the solution, I can&#39;t say I can provide one, but as we move more and more towards mobile devices, perhaps we&#39;ll be virtualization for these environments much more readily available.
</p>
<h3>Conclusion</h3>
<p>
Above I&#39;ve suggested three virtual environments, for Web site development. For the majority of projects, I think having current versions of the top three browsers - Internet Explorer, Firefox, and Safari - would be quite enough.
</p>
<p>
What do you think? What do you develop for?
</p>
<h3>Notes</h3>
<p>
1. Of course, I realize that if you were going to create&nbsp;a Flash or Silverlight application, you&#39;d naturally want to test on both Mac and Linux (or if your app becomes popular, you&#39;ll get some backlash on Slashdot). At that point what you&#39;re really testing is the environment, and not just the browser. But, for the &#39;majority&#39; of Web sites, I personally feel that virtual Mac and Linux environments are unnecessary. Compare this to my feelings a number of years ago, <a href="/words/post/Four-working-browsers-(at-least).aspx">before Safari was available for Windows</a>, and you&#39;d see a different view.<sup>2</sup>
</p>
<p>
2. I also recommended Lynx and Netscape in that post, but no longer see that as necessary, entirely.
</p>

