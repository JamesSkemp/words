+++
title = "Personalize WordPress and save yourself a headache"
description = "Remove 'Powered by ...' language to save yourself headaches later."
draft = false
comments = true
date = "2005-10-20T19:48:00-05:00"
slug = "Personalize-WordPress-and-save-yourself-a-headache"
blogengine = "a6d152c1-7583-4861-81da-87746ee5d50d"
categories = ["software"]
tags = ["wordpress"]
+++

<p>
Did you know:
</p>
<p>
If you do a search on Google for &quot;Powered by [WP]&quot; (where [WP] is WordPress), you&#39;ll end up with over 25.3 million returned results?<!--more--><!--adsense-->
</p>
<p>
Did you know that this blog, which has gotten only 175+ views this month, was recently prodded for a vulnerability in WordPress code?
</p>
<p>
Did you know that by changing just a couple of words in a couple files, you can reduce malicious views by some-odd percent?
</p>
<p>
It&#39;s &quot;Powered by&quot; that you want to change (you&#39;ll notice, at the far bottom of this page, that I&#39;ve changed mine).  The <strong>four</strong> files you want to change are;
</p>
<ul>
	<li>wordpress/wp.php (1)</li>
	<li>wordpress/wp-content/themes/<strong>ThemeName</strong>/comments-popup.php (2)</li>
	<li>wordpress/wp-content/themes/<strong>ThemeName</strong>/footer.php (2)</li>
	<li>wordpress/wp-content/themes/<strong>ThemeName</strong>/sidebar.php (1)</li>
</ul>
<p>
Change these, and keep them changed.
</p>
<p>
And, of course, always make sure you <a href="http://www.tamba2.org.uk/wordpress/backup/">backup</a> ;)
</p>

