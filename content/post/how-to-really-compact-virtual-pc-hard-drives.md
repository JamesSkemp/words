+++
title = "How to really compact Virtual PC hard drives"
summary = "Experience with Virtual PC hard drives that just didn't want to compact (and what I was doing wrong)."
draft = false
comments = true
date = "2008-11-18T20:16:00-06:00"
modified = "2008-11-18T20:28:57-06:00"
slug = "How-to-really-compact-Virtual-PC-hard-drives"
blogengine = "4c296da9-6a04-4eec-a94a-3b976967869c"
categories = ["software"]
tags = ["microsoft", "virtualization"]
+++

<p>
No names mentioned, but I&#39;ve recently been using a number of virtual machines for testing purposes.
</p>
<p>
One machine has Internet Explorer 6 and Firefox 2 installed, while a second has Internet Explorer 7, Firefox 3, and the most recent versions of Opera, Safari (for Windows) and Chrome.
</p>
<p>
However, the virtual hard drives were 10 GB each, due to a large number of apps being installed that didn&#39;t need to be, for our browser-based testing.
</p>
<p>
Yikes?
</p>
<p>
Even after uninstalling all of the unnecssary applications, and no matter how much compacting I did, they just didn&#39;t seem to want to shrink.
</p>
<p>
And then I started looking at using difference disks and found this great post by Andrew Connell, titled <a href="http://www.andrewconnell.com/blog/articles/UseVirtualPCsDifferencingDisksToYourAdvantage.aspx" target="_blank">HOWTO: Use Virtual PC&#39;s Differencing Disks to your Advantage</a>.
</p>
<blockquote>
	<p>
	Before I start creating differencing disks, I want to optimize these two images.&nbsp;
	</p>
</blockquote>
<p>
Score.
</p>
<p>
After performing the steps Andrew lays out I&#39;m down to under 5 gig each. Now that&#39;s some savings.
</p>
<p>
As an aside, I ran a defrag on my work computer as well, since I&#39;m positive one hasn&#39;t been run in well over a year (I don&#39;t recall when I got it, which also is when it was bought, but it&#39;s been that long). If I thought the amount of space I saved after the compacting worked I was very wrong. Unfortunately, even after running <a href="http://technet.microsoft.com/en-us/sysinternals/" target="_blank">Contig</a> I&#39;m still extremely fragmented, but even with 20+ gigs free it just can&#39;t defrag any further ...
</p>
<p>
How&#39;s your work/home machine looking?
</p>

