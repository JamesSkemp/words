+++
title = "WordPress 2.2.1 Import/Export function problems"
description = "Having problems with WordPress importing? Try chunking the data."
draft = false
comments = true
date = "2007-07-18T19:18:00-05:00"
modified = "2007-07-22T17:49:02-05:00"
slug = "WordPress-221-ImportExport-function-problems"
blogengine = "62a8d65f-52e3-4f8f-8d91-b9a3c7d952ad"
categories = ["StrivingLife", "software"]
tags = ["wordpress"]
+++

<p>
I had the &#39;opportunity&#39; today to import a WordPress blog from one server to another. While WordPress 2.2.x no comes with built-in functionality to export, and then import, an XML file, I&#39;ve found that it&#39;s anything but simple and trustworthy.
</p>
<p>
It seems that there may be a built-in limit to the amount of posts that can be imported. For me, I had to do an initial import (the XML file was approximately 2.3 MB), then determine which posts did come through. It turned out that it was the latter ones. After moving the relevant items into another XML file, and importing those separately, I was able to move all of the posts over.
</p>
<p>
Whew.
</p>
<p>
What you want to do is move the items into these extra XML files - just run the category once and you&#39;re all set.
</p>
<p>
However, don&#39;t expect your category numbers to necessarily match up, nor your posts. However, using category view may give you a good indication of where you&#39;re missing posts. 
</p>

