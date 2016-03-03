+++
title = "BlogEngine 1.3 upgrade issues"
summary = "For whatever reason, when I upgraded to BlogEngine 1.3, all of the permissions on my site vanished. [slnet0514:e8115c76-8306-4aaa-9bbe-66b3f72cec25]"
draft = false
comments = true
date = "2007-12-24T13:10:00-06:00"
modified = "2007-12-24T13:10:19-06:00"
slug = "BlogEngine-13-upgrade-issues"
blogengine = "e8115c76-8306-4aaa-9bbe-66b3f72cec25"
categories = ["software"]
tags = ["blogengine.net"]
+++

<p>
There&#39;s been quite the party for the last 30 minutes or so. 
</p>
<p>
BlogEngine 1.3 was released a couple of days ago, and I finally upgraded. Unlike what I should have done, I upgraded my live installation first. Yikes. 
</p>
<p>
For some reason, all of the permissions on the sub-folders and files was lost. Since web.config couldn&#39;t be accessed, the site went down - hard. 
</p>
<p>
After a bunch of Google searches, and no solutions, I started pressing buttons. 
</p>
<p>
If&nbsp;you go into the properties for a folder, go into the Permissions, and check the box &#39;Replace permission entries on all child objects with entries shown here that apply to child objects,&#39; it seems to add the relevant permissons back onto the files/folders. 
</p>
<p>
Whew.
</p>

