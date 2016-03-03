+++
title = "More comments in WordPress 2.1.2"
summary = "AdSense-Deluxe ads not displaying in WordPress 2.1.2? Here's something to try."
draft = false
comments = true
date = "2007-03-25T20:45:00-05:00"
modified = "2007-07-22T19:29:47-05:00"
slug = "More-comments-in-WordPress-212"
blogengine = "fecb0c69-e4b8-4dda-b397-5ab973964c80"
categories = ["software"]
tags = ["wordpress"]
+++

<p>
I noticed the other day that after upgrading to WordPress 2.1.2, many of the ads that the AdSense-Deluxe plugin was adding were not getting really getting added.
</p>
<p>
Normally I add the necessary AdSense-Deluxe (ASD) code immediately after the &#39;more&#39; comment. However, if I changed the location of the ASD code, the ads displayed correctly. Eh?<!--more--><!--adsense-->
</p>
<p>
Here&#39;s what I did:
</p>
<p>
Open /wp-includes/post-template.php and change line 83 from:
</p>
<p>
if ( preg_match(&#39;/&lt;!--more(.+?)?--&gt;/&#39;, $content, $matches) ) {
</p>
<p>
to:
</p>
<p>
if ( preg_match(&#39;/&lt;!--more--&gt;/&#39;, $content, $matches) ) {
</p>
<p>
For whatever reason, it replaces any one comment immediately after the more comment. Since the more comment should be entered in that format ...
</p>

