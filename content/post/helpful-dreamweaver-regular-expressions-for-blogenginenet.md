+++
title = "Helpful Dreamweaver regular expressions for BlogEngine.NET"
description = "Regular expression to find post titles in the relevant BlogEngine.NET directory."
draft = false
comments = true
date = "2007-07-21T05:34:00-05:00"
slug = "Helpful-Dreamweaver-regular-expressions-for-BlogEngineNET"
blogengine = "759e3135-c630-4796-afb7-24881c282d3c"
categories = ["StrivingLife", "software"]
tags = ["blogengine.net"]
+++

<p>
While looking for posts, in the App_Data/posts directory, I needed a find and replace for the title of the posts.&nbsp; It&#39;s a simple query, and here it is:
</p>
<p>
&lt;title&gt;[\s\S]*&lt;/title&gt;
</p>
<p>
Note: This post is probably more for me than anyone else ;)&nbsp;
</p>

