+++
title = "XML creation: Part 6"
summary = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part six I'll be using XSLT to modify the display of the XML document's contents so that it looks like the CSS-based output. [slnet0514:9e2ed0f1-ab72-4d78-85e2-0e7b162b666a]"
draft = false
comments = true
date = "2007-12-30T13:00:00-06:00"
modified = "2007-12-29T18:21:41-06:00"
slug = "XML-creation-Part-06"
blogengine = "9e2ed0f1-ab72-4d78-85e2-0e7b162b666a"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>
In this guide, I&#39;ll be creating an XML file to store the Playstation games I own, and ultimately make the XML file &#39;pretty&#39; for Web browsers. I&#39;ve done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>. 
</p>
<div class="note">
<p>
In part six I&#39;ll be using XSLT to modify the display of the XML document&#39;s contents so that it looks like the CSS-based output. 
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
In <a href="/words/post/XML-creation-Part-04.aspx">part four</a>,&nbsp;we made the XML file valid by associating a DTD. 
</p>
<p>
Finally, in <a href="/words/post/XML-creation-Part-05.aspx">part five</a> we started making the XML document pretty, in modern browsers, by using CSS. 
</p>
<h3>Overview</h3>
<p>
Now that we&#39;ve used CSS to stylize our XML document, and discovered some of the limitations of doing so, we&#39;ll use XSLT (Extensible Stylesheet Language Transformation)&nbsp;to modify the display. 
</p>
<p>
As with the DTD and CSS creations, we&#39;ll need to make&nbsp;a modification to the XML document, as well as create the XSLT itself.&nbsp; 
</p>
<h3>The XML change</h3>
<p>
To begin, we&#39;ll need to remove the line we added last time, that points to the CSS file, and replace it with one that points to the XSLT file. 
</p>
<blockquote>
	<p>
	&lt;?xml-stylesheet type=&quot;text/xsl&quot; href=&quot;http://strivinglife.com/files/xml_creation/part6.xslt&quot;?&gt; 
	</p>
</blockquote>
<p>
Obviously, update the location accordingly. 
</p>
<h3>The XSLT</h3>
<p>
Let&#39;s begin by creating an empty file at the above location. 
</p>
<p>
If we do so and load up our XML file, we&#39;ll see that this time there is an error when we try to display the file. This is because the XSLT must contain at minimum three lines. 
</p>
<blockquote>
	<p>
	&lt;?xml version=&quot;1.0&quot;?&gt;<br />
	&lt;xsl:stylesheet xmlns:xsl=&quot;http://www.w3.org/1999/XSL/Transform&quot; version=&quot;2.0&quot;&gt;<br />
	&lt;/xsl:stylesheet&gt; 
	</p>
</blockquote>
<p>
If you try&nbsp;viewing the XML file now you&#39;ll be presented with the XML contents, one piece of text immediately after another. This is similar to what we saw before, when we used an empty CSS file. 
</p>
<p>
This doesn&#39;t help us too much, so we&#39;ll try to tweak this a bit. 
</p>
<p>
In order to do so, we&#39;ll add the following between the second and third lines of the above. 
</p>
<blockquote>
	<p>
	&lt;xsl:template match=&quot;/&quot;&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/title&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/system/console&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/system/version&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/purchase/date&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/purchase/price&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/purchase/place&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/sell/date&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/sell/price&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/own&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;/games/game/notes&quot; /&gt;<br />
	&lt;/xsl:template&gt; 
	</p>
</blockquote>
<p>
If you view the XML file now, you&#39;ll see the information for the first game, MotorStorm. This somewhat helps, but not completely. 
</p>
<div class="note">
<p>
Note that this is the same as doing the following instead. 
</p>
<blockquote>
	<p>
	&lt;xsl:template match=&quot;games&quot;&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/title&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/system/console&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/system/version&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/purchase/date&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/purchase/price&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/purchase/place&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/sell/date&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/sell/price&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/own&quot; /&gt;<br />
	&nbsp;&nbsp; &lt;xsl:value-of select=&quot;game/notes&quot; /&gt;<br />
	&lt;/xsl:template&gt; 
	</p>
</blockquote>
</div>
<p>
What we really need to do is loop through each game. Of course, there is a way to do this. 
</p>
<blockquote>
	<p>
	&lt;xsl:template match=&quot;games&quot;&gt;<br />
	&nbsp;&nbsp; &lt;xsl:for-each select=&quot;game&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&lt;xsl:value-of select=&quot;title&quot; /&gt;<br />
	&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;system/console&quot; /&gt;<br />
	&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;system/version&quot; /&gt;<br />
	&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;purchase/date&quot; /&gt;<br />
	&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;purchase/price&quot; /&gt;<br />
	&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;purchase/place&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;xsl:value-of select=&quot;sell/date&quot; /&gt;<br />
	&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;sell/price&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;xsl:value-of select=&quot;own&quot; /&gt;<br />
	&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;notes&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;/xsl:for-each&gt;<br />
	&lt;/xsl:template&gt; 
	</p>
</blockquote>
<p>
Updating and running with this, we see that we&#39;re now seeing what we got when we ran it with just the first two, and the last, lines. 
</p>
<p>
Using the previous examples as a guide, we can get an idea of what we&#39;re doing. 
</p>
<p>
First, we&#39;re using <strong>xsl:template match=&quot;games&quot;</strong> to jump to the &#39;games&#39; element. Next, <strong>for-each</strong> &#39;game&#39; element, we&#39;re displaying the value of the elements listed. 
</p>
<div class="tip">
<p>
Using /games/game/title, for instance, here, instead of title, would still give the value for the first instance of that element. 
</p>
</div>
<p>
However, once again we&#39;re without proper spacing. 
</p>
<p>
First, we&#39;ll use divs and spans around the elements that we&#39;ll want to style. 
</p>
<blockquote>
	<p>
	&lt;?xml version=&quot;1.0&quot;?&gt;<br />
	&lt;xsl:stylesheet xmlns:xsl=&quot;http://www.w3.org/1999/XSL/Transform&quot; version=&quot;2.0&quot;&gt;<br />
	&nbsp;&lt;xsl:template match=&quot;games&quot;&gt;<br />
	&nbsp;&nbsp;&lt;div&gt;<br />
	&nbsp;&nbsp;&lt;xsl:for-each select=&quot;game&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;span&gt;&lt;xsl:value-of select=&quot;title&quot; /&gt;&lt;/span&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;system/console&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;system/version&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;purchase/date&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;purchase/price&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;purchase/place&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;sell/date&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;sell/price&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;own&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;notes&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&lt;/xsl:for-each&gt;<br />
	&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&lt;/xsl:template&gt;<br />
	&lt;/xsl:stylesheet&gt;&nbsp; 
	</p>
</blockquote>
<p>
Refreshing our XML file, we see that some elements are beginning to become styled. We can complete the look by adding in the actual style information. 
</p>
<div class="tip">
<p>
You may need to use &amp;#160; for spacing. Try removing some from the below to see what happens with the display. 
</p>
</div>
<blockquote>
	<p>
	&lt;?xml version=&quot;1.0&quot;?&gt;<br />
	&lt;xsl:stylesheet xmlns:xsl=&quot;http://www.w3.org/1999/XSL/Transform&quot; version=&quot;2.0&quot;&gt;<br />
	&nbsp;&lt;xsl:template match=&quot;games&quot;&gt;<br />
	&nbsp;&nbsp;&lt;div style=&quot;border:1px dashed #999;margin:.25em;padding:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&lt;xsl:for-each select=&quot;game&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin:1em 0;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;span style=&quot;font-size:120%;font-weight:bold;&quot;&gt;&lt;xsl:value-of select=&quot;title&quot; /&gt;&lt;/span&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&amp;#160;&lt;xsl:value-of select=&quot;system/console&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&amp;#160;&lt;xsl:value-of select=&quot;system/version&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;purchase/date&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&amp;#160;&lt;xsl:value-of select=&quot;purchase/price&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&amp;#160;&lt;xsl:value-of select=&quot;purchase/place&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;sell/date&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&amp;#160;&lt;xsl:value-of select=&quot;sell/price&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;own&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;font-style:italic;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:value-of select=&quot;notes&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&lt;/xsl:for-each&gt;<br />
	&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&lt;/xsl:template&gt;<br />
	&lt;/xsl:stylesheet&gt;&nbsp; 
	</p>
</blockquote>
<p>
Finally, we&#39;ll add in the text that we were&nbsp;adding in with&nbsp;before/after in the CSS file. 
</p>
<blockquote>
	<p>
	&lt;?xml version=&quot;1.0&quot;?&gt;<br />
	&lt;xsl:stylesheet xmlns:xsl=&quot;http://www.w3.org/1999/XSL/Transform&quot; version=&quot;2.0&quot;&gt;<br />
	&nbsp;&lt;xsl:template match=&quot;games&quot;&gt;<br />
	&nbsp;&nbsp;&lt;html&gt;<br />
	&nbsp;&nbsp;&lt;head&gt;<br />
	&nbsp;&nbsp;&lt;/head&gt;<br />
	&nbsp;&nbsp;&lt;body&gt;<br />
	&nbsp;&nbsp;&lt;div style=&quot;border:1px dashed #999;margin:.25em;padding:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&lt;xsl:for-each select=&quot;game&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin:1em 0;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;span style=&quot;font-size:120%;font-weight:bold;&quot;&gt;&lt;xsl:value-of select=&quot;title&quot; /&gt;&lt;/span&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;- &lt;xsl:value-of select=&quot;system/console&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&amp;#160;&lt;xsl:value-of select=&quot;system/version&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bought &lt;xsl:value-of select=&quot;purchase/date&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for $&lt;xsl:value-of select=&quot;purchase/price&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;at &lt;xsl:value-of select=&quot;purchase/place&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Sold &lt;xsl:value-of select=&quot;sell/date&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for $&lt;xsl:value-of select=&quot;sell/price&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Still own? &lt;xsl:value-of select=&quot;own&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style=&quot;font-style:italic;margin-left:1em;&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Notes: &lt;xsl:value-of select=&quot;notes&quot; /&gt;<br />
	&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&lt;/xsl:for-each&gt;<br />
	&nbsp;&nbsp;&lt;/div&gt;<br />
	&nbsp;&nbsp;&lt;/body&gt;<br />
	&nbsp;&nbsp;&lt;/html&gt;<br />
	&nbsp;&lt;/xsl:template&gt;<br />
	&lt;/xsl:stylesheet&gt; 
	</p>
</blockquote>
<div class="note">
<p>
While IE 7 will display the elements&nbsp;as we&#39;d expect, without the html and body elements, Firefox 2 will not. 
</p>
</div>
<p>
At this point <a href="/files/xml_creation/part6.xml" target="_blank">the XML file</a> displays very similar in IE 7 as it does in Firefox, as well as how it displays in Firefox <a href="/files/xml_creation/part5.xml" target="_blank">with CSS</a> (with the exception of some slight padding, which we could nonetheless remove if needed).
</p>
<p>
If you&#39;d like, you can <a href="/files/xml_creation/part6.xslt" target="_blank">view the XSLT document</a> using your browser, since it is also an XML file.
</p>
<h3>Where we&#39;re at</h3>
<p>
At this point we&#39;re at a very good place. We&#39;ve used XSLT to transform&nbsp;the display of our XML document&nbsp;so&nbsp;that it appears pleasing to the eye, in your standard,&nbsp;modern, browser. While a little more bulky than&nbsp;just using&nbsp;CSS alone, we can add important textual elements to the display, that would be difficult to do&nbsp;using simply CSS.&nbsp;&nbsp; 
</p>
<h3>What we&#39;re still missing</h3>
<p>
However, we&#39;re still missing some very important things; we need to be able to hide elements, like the sell information if the&nbsp;game hasn&#39;t been sold, as well as&nbsp;a proper sorting order. 
</p>
<p>
In part 7 we&#39;ll go ahead and look at a new XSLT function that will allow us to sort the order of the displayed elements. I&#39;ll also add in some Playstation 2 games, so we can look at a more advanced display.
</p>

