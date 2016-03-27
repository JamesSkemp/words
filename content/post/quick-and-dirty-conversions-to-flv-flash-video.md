+++
title = "Quick and dirty conversions to FLV (Flash Video)"
description = "Using one tool, it's easy to convert a wide variety of video formats to FLV, for posting on your site. [slnet0514:0619b657-9369-4afb-af08-1de033f0e7b8]"
draft = false
comments = true
date = "2008-02-23T12:45:00-06:00"
modified = "2008-02-23T12:46:27-06:00"
slug = "Quick-and-dirty-conversions-to-FLV-Flash-Video"
blogengine = "0619b657-9369-4afb-af08-1de033f0e7b8"
categories = ["article", "dvd / movie", "Internet", "software", "technology"]
tags = ["iis", "internet video convertor", "casio ex-z1200", "flash"]
+++

<p>
I purchased a Casio EX-Z1200 a bit ago, which I&#39;ve been playing around with. Overall, I&#39;ve been very happy with it, however, it outputs movies to the MOV format. While this seemed great for Apple, it wasn&#39;t the best for me. 
</p>
<p>
After testing out QuickTime Pro (7. something) and Ulead Movie Wizard 3.2 SE VCD (which came with the camera), I was about to settle for less than I hoped for. 
</p>
<p>
However, along came <a href="http://ivcsoft.free.fr/" target="_blank">Internet Video Convertor (IVC)</a>. 
</p>
<div class="tip">
<p>
Of all the people in the world, it is the French who are most likely to create a multi-language site/piece of software. 
</p>
</div>
<p>
I haven&#39;t played with it enough to be fully satisifed, but I&#39;m extremely happy with what I&#39;ve got thus far. 
</p>
<p>
One of the things that IVC can do is convert to FLV format, which is similar to SWF, except it allows for streaming Flash video. Yes, streaming Flash. 
</p>
<p>
While one can host videos on a variety of sites, I&#39;d really like to be able to host on my own server, when possible (and/but still post to those other sites as well). 
</p>
<p>
Per this Adobe TechNote (<a rel="nofollow" href="http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_19439&amp;sliceId=2" target="_blank">Windows 2003 Server does not stream FLV videos</a>) I just needed to add a simple MIME type (<strong>.flv</strong> as <strong>flv-application/octet-stream</strong>) and I could then use the IVC outputs (Video-to-Flash) to play any file from my server. 
</p>
<div class="tip">
<p>
You can, if you so desire (I did) add this MIME type to just one site, instead of to the entire server. Adding it to the server allows any site to &#39;understand&#39;&nbsp;FLV files, which may or may not be what you want in your particular situation(s). 
</p>
</div>
<p>
While I could have played other formats as well, the benefit of this is that other OS users can run this as well. 
</p>
<p>
If you&#39;re interested in finding out more about FLV&nbsp;and/versus SWF&nbsp;files, there&#39;s an interesting article from Macromedia, <a href="http://www.adobe.com/devnet/flash/articles/flv_download.html" target="_blank">Delivering Flash Video: Understanding the Difference Between Progressive Download and Streaming Video</a>&nbsp;(2004). 
</p>
<p>
<a href="http://media.strivinglife.com/video/20060924_DW8Snippets.html" target="_blank">Watch Creating snippets in Dreamweaver 8 (Windows)</a>. 
</p>
<h3>File conversion details</h3>
<p>
Here are some details on the conversion: 
</p>
<p>
The source file was a 108 MB AVI file, captured using&nbsp;CamStudio 2.00, at 640x480. 
</p>
<p>
Converting this into a 320x240 FLV file resulted in a 4.93 MB file. However, at that size the text was difficult to read. 
</p>
<p>
Upgrading to 640x480 resulted in a 38.2 MB file. 
</p>
<p>
The SWF player necessary to actually server the FLV added another 90 KB. 
</p>
<p>
Despite all that, the file looks remarkably well, even better than the <a rel="nofollow" href="http://video.google.com/videoplay?docid=3586025281835355534" target="_blank">Google Video version</a> (which was resized, obviously). 
</p>
<p>
For non-text video, however, I&#39;d say 320x240 may have worked (once I have some good video from my Casio, I&#39;ll be uploading that through the same process). 
</p>
<p>
The six-and-a-half minute video didn&#39;t take all that long to convert to FLV, from AVI. The MOV files that I&#39;ve converted seem to take longer, despite being shorter in length. 
</p>
<p>
It seems it&#39;s also possible to stream FLV files using IIS and&nbsp;.NET, but I haven&#39;t dug into it quite yet. More on&nbsp;that in&nbsp;<a href="http://blogs.ugidotnet.org/kfra/archive/2006/10/04/50003.aspx" target="_blank">FLV Flash video streaming with ASP.NET 2.0, IIS and HTTP handler</a>. 
</p>
<p>
Further updates to follow. 
</p>

