+++
title = "Setting up Dreamweaver and Nvu to recognize your server"
summary = "Now that we've setup Apache on our local computer, and effectively created a basic Web server, it's time to look at setting up some popular programs to work with these sites.  I'll be looking at two programs, the costly Dreamweaver (8) and the free Nvu (1.0)."
draft = false
comments = true
date = "2006-02-19T10:53:00-06:00"
modified = "2009-12-21T08:00:02-06:00"
slug = "Setting-up-Dreamweaver-and-Nvu-to-recognize-your-server"
blogengine = "42136e5c-dcbe-40d0-b669-a39d5e700394"
categories = ["software", "tutorials / guides"]
tags = ["dreamweaver", "nvu"]
+++

<p>Now that we've <a href="http://strivinglife.com/words/post/Installing-Apache-to-a-Windows-based-computer-locally.aspx">setup Apache on our local computer</a>, and effectively created a basic Web server, it's time to look at setting up some popular programs to work with these sites. I'll be looking at two programs, the costly Dreamweaver (8) and the free Nvu (1.0).<!--more--></p>
<h3>Dreamweaver setup</h3>
<p>For those of you using Dreamweaver as your editor, I'll be outlining how to set it up to recognize your new sites. While I'll specifically be dealing with Dreamweaver 8, the basics should be enough for other versions, as well as for other programs.<!--adsense--></p>
<p>Open Dreamweaver and go to Site &gt; New Site... First, we'll setup our site at C:\home\website\public_html\. Give the site a name in the Site name field &ndash; in this case, let's use &ldquo;website&rdquo;. In Local root folder, we'll use C:\home\website\public_html. We'll leave the other options alone, but check &ldquo;Use case-sensitive link checking&rdquo;. While Windows accepts case-insensitive links, we'll do ourselves a favor by forcing ourselves to keep case in mind.</p>
<p>Finally, under Testing Server, we'll leave Server model alone, since we don't yet have a server matching either of these. Change Access to Local/Network, and when the window refreshes, change URL prefix to <a href="http://website.localhost/">http://website.localhost/</a>. Testing server folder should be correct, and we don't need to check the box.</p>
<p>Once we've made these changes, we'll go ahead and complete the creation process by saying OK. We can now go ahead and create a new site for each of the other sites &ndash; C:\home\website2\public_html\ and any other sites we may have setup - with the appropriate changes.</p>
<p>As we progress in our setup of our server, we can change our Server model accordingly. For now, however, we're set leaving things as they are. Whenever we create any additional sites, we can go ahead and add them the same way as we've done above.</p>
<h3>Nvu setup</h3>
<p>The freely available Nvu (as of this writing, version 1.0 is available at <a rel="nofollow external" href="http://nvu.com/">http://nvu.com/</a>) is also a snap to setup to work with our new server. Open Nvu and go to Edit &gt; Publishing Site Settings... Click New Site.</p>
<p>In the Site Name field, type in a site name, such as website. In HTTP address of your homepage, enter <a rel="nofollow" href="http://website.localhost/">http://website.localhost/</a>. In Publishing address, enter file:///C:/home/website/public_html/ or browse to C:\home\website\public_html\. Add any additional sites, and you're done.</p>
<p>You should see a listing of the two sites on the left-side of the main Nvu window (although you may have to close and reopen Nvu first, or press the Edit sites button under the Nvu Site Manager area).</p>
<h3>Call for comments and additional programs</h3>
<p>If you'd like me to include other programs (such as freely available programs), please post in the comments.</p>
