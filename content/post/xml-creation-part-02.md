+++
title = "XML creation: Part 2"
description = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part two, I'll be creating the layout, that I think will work. [slnet0514:14f06e8e-c839-4c24-bd42-92ed61c72916]"
draft = false
comments = true
date = "2007-12-26T23:00:00-06:00"
modified = "2007-12-26T23:31:03-06:00"
slug = "XML-creation-Part-02"
blogengine = "14f06e8e-c839-4c24-bd42-92ed61c72916"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>
In this guide, I&#39;ll be creating an XML file to store the Playstation games I own, and ultimately make the XML file &#39;pretty&#39; for Web browsers. I&#39;ve done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>. 
</p>
<div class="note">
<p>
In part two, I&#39;ll be creating the layout, that I think will work. 
</p>
</div>
<h3>Last time ...</h3>
<p>
If you recall, in <a href="/words/post/XML-creation-Part-01.aspx">part one</a>, I went over the idea of what the XML file would store, and what layout I thought it might need. 
</p>
<p>
This time, I&#39;ll actually create the XML document&#39;s layout, using elements. 
</p>
<h3>The structure realized</h3>
<div class="note">
<p>
(There is some indenting, but it is a bit difficult to see here.) 
</p>
</div>
<blockquote>
	<p>
	&lt;?xml version=&quot;1.0&quot;?&gt;<br />
	&lt;games&gt;<br />
	&nbsp;&lt;game&gt;<br />
	&nbsp;&nbsp;&lt;title&gt;&lt;/title&gt;<br />
	&nbsp;&nbsp;&lt;system&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;console&gt;&lt;/console&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;version&gt;&lt;/version&gt;<br />
	&nbsp;&nbsp;&lt;/system&gt;<br />
	&nbsp;&nbsp;&lt;purchase&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;date&gt;&lt;/date&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;price&gt;&lt;/price&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;place&gt;&lt;/place&gt;<br />
	&nbsp;&nbsp;&lt;/purchase&gt;<br />
	&nbsp;&nbsp;&lt;sell&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;date&gt;&lt;/date&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;price&gt;&lt;/price&gt;<br />
	&nbsp;&nbsp;&lt;/sell&gt;<br />
	&nbsp;&nbsp;&lt;own&gt;&lt;/own&gt;<br />
	&nbsp;&nbsp;&lt;notes&gt;&lt;/notes&gt;<br />
	&nbsp;&lt;/game&gt;<br />
	&lt;/games&gt;&nbsp; 
	</p>
</blockquote>
<p>
There it is. Based upon what we determined last time, we decided that there would be individual games within one larger grouping. For the individual game, there would be information relevant to that game. 
</p>
<p>
You can <a href="/files/xml_creation/part2.xml" target="_blank">see this in action</a> in most current browsers. 
</p>
<div class="tip">
<p>
You may not that some browsers, such as IE 7, will change empty elements, such as <strong>&lt;date&gt;&lt;/date&gt;</strong> to simply <strong>&lt;date /&gt;</strong>. Since the element contains no information, there&#39;s little need to have a closing, when the open can function as both. 
</p>
<p>
If you View Source, you can usually see what really underlies the file. You can also do this for the <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>, which will give you a very interesting perspective of what the content is, versus the design elements. 
</p>
</div>
<h3>Where we stand</h3>
<p>
Currently, the XML document has structure, but no content. This is the framework that we&#39;ll use in our next part to actually fill in some data. 
</p>
<p>
However, don&#39;t be confused and think that this framework is the best it could be. In another, later, part, we&#39;ll go over a much more robust &#39;framework&#39; that we should really be using. 
</p>
<h3>Next time ...</h3>
<p>
In part three, I&#39;ll be filling out our framework with actual data. Once we have the data in place, we can determine what rules should be in place for each element, and then work on styling the document for display in browsers. 
</p>
<p>
We&#39;ll also work on getting our XML document to <a href="http://www.validome.org/xml/validate/" target="_blank">validate</a>. 
</p>

