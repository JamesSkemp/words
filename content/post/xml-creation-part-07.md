+++
title = "XML creation: Part 7"
summary = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part seven I'll be expanding upon our XSLT to remove elements that are empty, and change the sort order, for our existing XML file. [slnet0514:680bb8b9-f4f2-4e57-82a1-96a763c03a55]"
draft = false
comments = true
date = "2007-12-31T13:00:00-06:00"
modified = "2007-12-29T23:56:04-06:00"
slug = "XML-creation-Part-07"
blogengine = "680bb8b9-f4f2-4e57-82a1-96a763c03a55"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>
In this guide, I&#39;ll be creating an XML file to store the Playstation games I own, and ultimately make the XML file &#39;pretty&#39; for Web browsers. I&#39;ve done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>. 
</p>
<div class="note">
<p>
In part seven I&#39;ll be expanding upon our XSLT to remove elements that are empty, and change the sort order, for our existing XML file. 
</p>
</div>
<h3>Last time ...</h3>
<p>
Up until now we&#39;ve decided what we want to store, and how we want to store it, in an XML file. 
</p>
<p>
Then, in <a href="/words/post/XML-creation-Part-03.aspx">part three</a>, we actually added some of the data we want to store. 
</p>
<p>
In <a href="/words/post/XML-creation-Part-04.aspx">part four</a>, we made the XML file valid by associating a DTD. 
</p>
<p>
In <a href="/words/post/XML-creation-Part-05.aspx">part five</a> we started making the XML document pretty, in modern browsers, by using CSS. In part six we were able to mimic this look using an XSLT file instead. 
</p>
<h3>Overview</h3>
<p>
However, while we&#39;ve been able to mimic the CSS output, what we really want to do is make it better. 
</p>
<p>
To do this we&#39;ll want to hide elements that are empty, such as when a&nbsp;game hasn&#39;t been sold, as well as change the sort order from according to how they&#39;re entered in the XML file, to one based upon game title. 
</p>
<h3>Using&nbsp;XSLT to sort the content</h3>
<p>
Adding a new sort order is super easy. All we need to do is add an xsl:sort immediately after our xsl:for-each. 
</p>
<p>
So,&nbsp;find the following line. 
</p>
<blockquote>
	<p>
	&lt;xsl:for-each select=&quot;game&quot;&gt; 
	</p>
</blockquote>
<p>
Now add this line immediately after it. 
</p>
<blockquote>
	<p>
	&lt;xsl:sort select=&quot;title&quot; data-type=&quot;text&quot; /&gt; 
	</p>
</blockquote>
<p>
If we wanted to add another sort, we could simply add another line, like the above, after this addition. Pretty simple, huh? 
</p>
<h3>Using XSLT to hide empty elements</h3>
<p>
Now that we&#39;re sorting, we&#39;ll attempt to hide any elements which are empty, which in this case means the sell data, and the notes. 
</p>
<p>
First, we&#39;ll use conditional logic to hide the sell data, depending upon whether <strong>own</strong> is equal to no or yes. 
</p>
<blockquote>
	<p>
	&lt;xsl:if test=&quot;own = &#39;no&#39;&quot;&gt;<br />
	&nbsp;&nbsp; &lt;div style=&quot;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp; &nbsp; Sold &lt;xsl:value-of select=&quot;sell/date&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;for $&lt;xsl:value-of select=&quot;sell/price&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;/div&gt;<br />
	&lt;/xsl:if&gt; 
	</p>
</blockquote>
<p>
As you can see, we&#39;ve added two new lines. On the first line we&#39;ve added an if statement. If the value of own is &#39;no&#39;, we&#39;ll display the sell data. Otherwise, we won&#39;t. 
</p>
<p>
For notes, we can do something similar. 
</p>
<blockquote>
	<p>
	&lt;xsl:if test=&quot;notes != &#39;&#39;&quot;&gt;<br />
	&nbsp;&nbsp; &lt;div style=&quot;font-style:italic;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Notes: &lt;xsl:value-of select=&quot;notes&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;/div&gt;<br />
	&lt;/xsl:if&gt;&nbsp; 
	</p>
</blockquote>
<p>
Here we&#39;re checking to see if notes is empty, and if it is not, we&#39;re displaying the notes. 
</p>
<h3>Where we&#39;re at now</h3>
<p>
Now we&#39;ve got <a href="/files/xml_creation/part7.xml" target="_blank">an XML document</a>, with <a href="/files/xml_creation/part7.xslt" target="_blank">XSLT</a>, that displays more like we&#39;d expect. 
</p>
<h3>Next time ...</h3>
<p>
Even though I was going to go over it here, I decided to hold off adding additional games until the next part. In that part I&#39;ll be adding some additional games, from the Playstation 2, and changing the display so that we can easily separate them out. 
</p>

