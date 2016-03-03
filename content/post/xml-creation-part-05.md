+++
title = "XML creation: Part 5"
summary = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part five, I'll be using CSS to modify the display of the XML document's contents. [slnet0514:ff7ebd10-c6ee-491a-8f7f-08c925d84ce4]"
draft = false
comments = true
date = "2007-12-29T13:00:00-06:00"
modified = "2007-12-29T12:08:11-06:00"
slug = "XML-creation-Part-05"
blogengine = "ff7ebd10-c6ee-491a-8f7f-08c925d84ce4"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>
In this guide, I&#39;ll be creating an XML file to store the Playstation games I own, and ultimately make the XML file &#39;pretty&#39; for Web browsers. I&#39;ve done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>. 
</p>
<div class="note">
<p>
In part five I&#39;ll be using CSS to modify the display of the contents of the XML document. 
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
<h3>Overview</h3>
<p>
As with the DTD, there are two things we need to do to make our XML file display differently, using CSS. 
</p>
<p>
First, we&#39;ll need to make a quick modification to the XML file, followed by actually creating the CSS document. 
</p>
<p>
I&#39;ll be assuming that you know CSS, so I won&#39;t be going into it too much. As they always recommend when it comes to these things, feel free&nbsp;to play around with the code on your own. 
</p>
<h3>The XML addition</h3>
<p>
To begin, we&#39;ll need to add a single line to the XML document itself. 
</p>
<p>
Immediately after the second line, which begins with &lt;!DOCTYPE , add the following line, correcting the URL as necessary. 
</p>
<blockquote>
	<p>
	&lt;?xml-stylesheet type=&quot;text/css&quot; href=&quot;http://strivinglife.com/files/xml_creation/part5.css&quot;?&gt; 
	</p>
</blockquote>
<p>
If you&#39;re familar with HTML, this is nothing new to you. Basically we just need to tell the parser, whether it be browser or something else, what styles should be used for this document. 
</p>
<h3>The CSS document</h3>
<p>
Let&#39;s begin by creating an empty CSS file at the location previously specified. 
</p>
<p>
If we do so and load up our XML file, we&#39;ll see that the text runs together. Unfortunately, this isn&#39;t going to work. 
</p>
<p>
Since I&#39;m assuming you&#39;re familar with CSS, I can say that you may be&nbsp;aware that browsers automatically add certain styles to elements in HTML files. For instance, the head element does not display, which includes the title element. 
</p>
<p>
You can give certain elements, like paragraphs - p - certain styles, by doing something like the following. 
</p>
<blockquote>
	<p>
	p {<br />
	&nbsp;&nbsp; margin:10px 0;<br />
	} 
	</p>
</blockquote>
<p>
For our new CSS file,&nbsp;instead of using &#39;p&#39;, we&#39;ll be using the&nbsp;names of our own elements. 
</p>
<p>
So, to get these on separate lines, we could start with something simple like the following. 
</p>
<blockquote>
	<p>
	game {<br />
	&nbsp; display:block;<br />
	} 
	</p>
</blockquote>
<p>
Now each of our individual games is on its own line. 
</p>
<p>
We can add a number of other styles to make the document a little more accessible. 
</p>
<blockquote>
	<p>
	games, game, purchase, sell, own, notes {<br />
	&nbsp;display:block;<br />
	}<br />
	games {<br />
	&nbsp;border:1px dashed #999;<br />
	&nbsp;margin:.25em;<br />
	&nbsp;padding:1em;<br />
	}<br />
	game {<br />
	&nbsp;margin:1em 0;<br />
	}<br />
	title {<br />
	&nbsp;font-size:120%;<br />
	&nbsp;font-weight:bold;<br />
	}<br />
	purchase, sell, own, notes {<br />
	&nbsp;margin-left:1em;<br />
	}<br />
	notes {<br />
	&nbsp;font-style:italic;<br />
	} 
	</p>
	<p>
	title:after {<br />
	&nbsp;content:&quot; -&quot;;<br />
	}<br />
	price:before {<br />
	&nbsp;content:&quot;for $&quot;;<br />
	}<br />
	purchase date:before {<br />
	&nbsp;content:&quot;Bought &quot;;<br />
	}<br />
	purchase place:before {<br />
	&nbsp;content:&quot;at &quot;;<br />
	}<br />
	sell date:before {<br />
	&nbsp;content:&quot;Sold &quot;;<br />
	}<br />
	own:before {<br />
	&nbsp;content:&quot;Still own? &quot;;<br />
	}<br />
	notes:before {<br />
	&nbsp;content:&quot;Notes: &quot;;<br />
	} 
	</p>
</blockquote>
<div class="note">
<p>
You can also&nbsp;<a href="/files/xml_creation/part5.css" target="_blank">view the CSS file</a> for all of the above. 
</p>
</div>
<p>
This gives us a little cleaner output/display, which we can <a href="/files/xml_creation/part5.xml" target="_blank">view in our browser</a>. 
</p>
<p>
However, because&nbsp;we&#39;re using some advanced CSS features, not all browsers will display this the same (try Firefox 2 for the before/after functionality). 
</p>
<p>
In fact, this is one of the major problems with relying on CSS-only. Since we really want to display more text than what is contained within the XML document, as well as conditional logic, CSS can&#39;t provide all we need. 
</p>
<p>
For instance, I can&#39;t hide the sell data if there is no data, nor only display the notes if there is notes. I also can&#39;t change the sorting order from how it currently is, which is based solely on how they&#39;re entered into the document, to something sorting based on, for instance, the title.&nbsp;For these features, we&#39;d have to look at a server- or client-side language that could handle this. 
</p>
<h3>Next time ...</h3>
<p>
Next time we&#39;ll look at using&nbsp;XSLT (that&#39;s Extensible Stylesheet Language Transformation) to display our data, which will allow us to do a bit more with how, and what, we&#39;re displaying. 
</p>

