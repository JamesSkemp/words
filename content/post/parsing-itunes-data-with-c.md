+++
title = "Parsing iTunes data with C#"
description = "In the quest to better synch iTunes and my iPod, I've been digging into ways to export library information. Here's a test app for Windows, written in C#."
draft = false
comments = true
date = "2009-02-22T22:40:00-06:00"
modified = "2009-03-02T07:56:45-06:00"
slug = "Parsing-iTunes-data-with-C"
blogengine = "c4c82bef-59a5-4c2b-a0dd-f5b64db6e404"
categories = ["software", "StrivingLife"]
tags = ["ipod", "c#", "windows"]
+++

<div class="warning">
<p>
This application has since been updated. <a href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">Read about the current version of iTunes Playlists to Xml.</a> 
</p>
</div>
<p>
For better or worse, when I began setting up my iPod I opted to manually organize my iPod. In large part, this was because at the time I had a machine with a pretty small hard drive, and couldn&#39;t keep all of my music on it. 
</p>
<p>
However, with a new HP, I was able to store all my music on that computer, as well as back it up to a USB drive. 
</p>
<p>
Unfortunately, that means that my playlists, ratings, play counts, etcetera, are stored solely on my iPod. Not a good situation to be in. If we could export our iPod library using iTunes, like we can for the library on our computer, it might not be so bad. However, that&#39;s not the case. 
</p>
<p>
I&#39;ve tried manually rating my music on my computer, every once in a while, but it&#39;s ended up a disaster. 
</p>
<p>
While I was digging into the iTunesDB, I found a post on how to use a custom library to query this file using C#. Further digging revealed that once you install iTunes you can use C# (etcetera) to access a COM, thereby getting results directly out of iTunes. 
</p>
<p>
But, it seems to be very resource intensive to query iTunes and pull information. 
</p>
<p>
I&#39;ve created a test application (called <strong>iTunes Application</strong>) that queries iTunes and outputs the following information; 
</p>
<ul>
	<li>
	<div>
	sources of the kind library or iPod 
	</div>
	</li>
	<li>
	<div>
	playlist names and kinds&nbsp;on those sources 
	</div>
	</li>
	<li>
	<div>
	the first 10 songs, with the number of stars, on any &quot;Music&quot; playlists 
	</div>
	</li>
</ul>
<p>
Because of the way it operates, if iTunes isn&#39;t started, it will be when the application begins. Outside of writing to a text box and label, no writing occurs, so the application should be pretty safe. Tested on Windows Vista Ultimate and Windows XP Home, with iTunes 8.0.2.20. .NET is required (probably 3.5). 
</p>
<p>
What I&#39;d like to do is have it allow you to pull the songs/ratings for any playlist, on any device. Then I can do a compare to determine what songs are different. 
</p>
<p>
<a href="http://jamesrskemp.com/applications/iTunesApplication.zip" title="iTunes Application pre-alpha">Download iTunes Application pre-alpha</a>. 
</p>

