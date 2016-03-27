+++
title = "XML creation: Part 8"
description = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part eight I'll be expanding upon our XSLT to group games based upon the system they belong to, as well as modify our XSLT to use xsl:appy-templates. [slnet0514:ddf229c2-23de-44be-b801-c1b8b9736632]"
draft = false
comments = true
date = "2008-01-01T13:00:00-06:00"
modified = "2009-06-01T22:52:00-05:00"
slug = "XML-creation-Part-08"
blogengine = "ddf229c2-23de-44be-b801-c1b8b9736632"
categories = ["tutorials / guides"]
tags = ["xml", "playstation"]
+++

<p>In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. I've done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>.</p>
<div class="note">
<p>In part eight I'll be expanding upon our XSLT to group games based upon the system they belong to, as well as modify our XSLT to use xsl:appy-templates.</p>
</div>
<h3>This time ...</h3>
<p>I won't be going into a recap of what I've done in all seven of the previous parts. Check <a href="/words/post/XML-creation-Part-07.aspx" target="_blank">part 7</a> for that.</p>
<p>For part eight, I've modified the XML document by adding games for the Playstation 1 and 2.</p>
<p>While our XSLT will handle these, it ends up sorting the games altogether, by alphabetical title. This is well enough, however, what I'd like to do is separate these out so that the Playstation 1, 2, and 3 games are listed alphabetically by system.</p>
<h3>Grouping by sorting</h3>
<p>The easiest way to do this is to add the following two sorts before the existing sort. So we'll take the following line:</p>
<blockquote>
<p>&lt;xsl:sort select="title" data-type="text" /&gt;</p>
</blockquote>
<p>We'll change this to the following (new lines in bold):</p>
<blockquote>
<p><strong>&lt;xsl:sort select="system/console" data-type="text" /&gt;<br />&lt;xsl:sort select="system/version" data-type="number" /&gt;</strong><br />&lt;xsl:sort select="title" data-type="text" /&gt;</p>
</blockquote>
<h3>xsl:apply-templates</h3>
<p>As you may realize, we're using xsl:for-each to loop through our XML elements, and output the values. However, there is another way to do this.</p>
<p>Instead of using xsl:for-each we can use xsl:apply-templates.</p>
<p>For instance, we're listing the date and price in two different places. However, we're formatting this the same way.</p>
<p>First, we'll&nbsp;add the following, immediately before the closing of xsl:stylesheet.</p>
<blockquote>
<p>&lt;xsl:template match="price"&gt;<br />&nbsp;&nbsp; for $&lt;xsl:value-of select="." /&gt;<br />&lt;/xsl:template&gt;</p>
</blockquote>
<p>To some extent, we've seen this before, for our main template, with the exception of using game instead of price.</p>
<p>Next, we'll change the two price lines to the following, accordingly.</p>
<blockquote>
<p>&lt;xsl:apply-templates select="purchase/price" /&gt;</p>
<p>&lt;xsl:apply-templates select="sell/price" /&gt;</p>
</blockquote>
<p>After refreshing the XML file, you shouldn't notice any changes. However, if you make a modification to the xsl:template for price, you'll notice that the changes are made to the two price outputs.</p>
<p>If we were doing more with the date, we could do the same for these two elements.</p>
<p>You can see <a href="/files/xml_creation/part8.xml" target="_blank">the XML file</a> for this, as well as <a href="/files/xml_creation/part8.xslt" target="_blank">the XSLT file</a>.</p>
<h3>In that case ... another way of sorting</h3>
<p>Since we can use xsl:apply-templates, how about using this in place of our xsl:for-each?</p>
<p>We begin with our current XSLT.</p>
<pre class="code"><code class="xml">
&lt;?xml version="1.0"?&gt;
&lt;xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="2.0"&gt;
&nbsp;&lt;xsl:template match="games"&gt;
&nbsp;&nbsp;&lt;html&gt;
&nbsp;&nbsp;&lt;head&gt;
&nbsp;&nbsp;&nbsp;&lt;title&gt;James Skemp's video games&lt;/title&gt;
&nbsp;&nbsp;&lt;/head&gt;
&nbsp;&nbsp;&lt;body&gt;
&nbsp;&nbsp;&lt;h1&gt;James Skemp's video game collection&lt;/h1&gt;
&nbsp;&nbsp;&lt;p&gt;The following is a list of video games owned by James Skemp, of &lt;a href="http://strivinglife.com/"&gt;StrivingLife&lt;/a&gt;.&lt;/p&gt;
&nbsp;&nbsp;&lt;div style="border:1px dashed #999;margin:.25em;padding:1em;"&gt;
&nbsp;&nbsp;&lt;xsl:for-each select="game"&gt;
&nbsp;&nbsp;&nbsp;&lt;xsl:sort select="system/console" data-type="text" /&gt;
&nbsp;&nbsp;&nbsp;&lt;xsl:sort select="system/version" data-type="number" /&gt;
&nbsp;&nbsp;&nbsp;&lt;xsl:sort select="title" data-type="text" /&gt;
&nbsp;&nbsp;&nbsp;&lt;div style="margin:1em 0;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;span style="font-size:120%;font-weight:bold;"&gt;&lt;xsl:value-of select="title" /&gt;&lt;/span&gt;
&nbsp;&nbsp;&nbsp;&nbsp;- &lt;xsl:value-of select="system/console" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&amp;#160;&lt;xsl:value-of select="system/version" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style="margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bought &lt;xsl:value-of select="purchase/date" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:apply-templates select="purchase/price" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;at &lt;xsl:value-of select="purchase/place" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:if test="own = 'no'"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style="margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Sold &lt;xsl:value-of select="sell/date" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:apply-templates select="sell/price" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/xsl:if&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style="margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Still own? &lt;xsl:value-of select="own" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:if test="notes != ''"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style="font-style:italic;margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Notes: &lt;xsl:value-of select="notes" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/xsl:if&gt;
&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&lt;/xsl:for-each&gt;
&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&lt;/body&gt;
&nbsp;&nbsp;&lt;/html&gt;
&nbsp;&lt;/xsl:template&gt;
&nbsp;&lt;xsl:template match="price"&gt;
&nbsp;&nbsp;for $&lt;xsl:value-of select="." /&gt;
&nbsp;&lt;/xsl:template&gt;
&lt;/xsl:stylesheet&gt;&nbsp;
</code></pre>
<p>After some modifications, we'll end up with the following XSLT, which also puts games for newer versions of consoles at the top.</p>
<pre class="code"><code class="xml">
&lt;?xml version="1.0"?&gt;
&lt;xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="2.0"&gt;
&nbsp;&lt;xsl:template match="games"&gt;
&nbsp;&nbsp;&lt;html&gt;
&nbsp;&nbsp;&lt;head&gt;
&nbsp;&nbsp;&nbsp;&lt;title&gt;James Skemp's video games&lt;/title&gt;
&nbsp;&nbsp;&lt;/head&gt;
&nbsp;&nbsp;&lt;body&gt;
&nbsp;&nbsp;&lt;h1&gt;James Skemp's video game collection&lt;/h1&gt;
&nbsp;&nbsp;&lt;p&gt;The following is a list of video games owned by James Skemp, of &lt;a href="http://strivinglife.com/"&gt;StrivingLife&lt;/a&gt;.&lt;/p&gt;
&nbsp;&nbsp;&lt;div style="border:1px dashed #999;margin:.25em;padding:1em;"&gt;
&nbsp;&nbsp;&nbsp;&lt;xsl:apply-templates select="game"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:sort select="system/console" data-type="text" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:sort select="system/version" data-type="number" order="descending" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:sort select="title" data-type="text" /&gt;
&nbsp;&nbsp;&nbsp;&lt;/xsl:apply-templates&gt;
&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&lt;/body&gt;
&nbsp;&nbsp;&lt;/html&gt;
&nbsp;&lt;/xsl:template&gt;
&nbsp;&lt;xsl:template match="game"&gt;
&nbsp;&nbsp;&lt;div style="margin:1em 0;"&gt;
&nbsp;&nbsp;&nbsp;&lt;span style="font-size:120%;font-weight:bold;"&gt;&lt;xsl:value-of select="title" /&gt;&lt;/span&gt;
&nbsp;&nbsp;&nbsp;- &lt;xsl:value-of select="concat(system/console, ' ', system/version)" /&gt;
&nbsp;&nbsp;&nbsp;&lt;div style="margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;Bought &lt;xsl:value-of select="purchase/date" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:apply-templates select="purchase/price" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;at &lt;xsl:value-of select="purchase/place" /&gt;
&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&lt;xsl:if test="own = 'no'"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style="margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Sold &lt;xsl:value-of select="sell/date" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;xsl:apply-templates select="sell/price" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&lt;/xsl:if&gt;
&nbsp;&nbsp;&nbsp;&lt;div style="margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;Still own? &lt;xsl:value-of select="own" /&gt;
&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&lt;xsl:if test="notes != ''"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;div style="font-style:italic;margin-left:1em;"&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Notes: &lt;xsl:value-of select="notes" /&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&nbsp;&nbsp;&lt;/xsl:if&gt;
&nbsp;&nbsp;&lt;/div&gt;
&nbsp;&lt;/xsl:template&gt;
&nbsp;&lt;xsl:template match="price"&gt;
&nbsp;&nbsp;for $&lt;xsl:value-of select="." /&gt;
&nbsp;&lt;/xsl:template&gt;
&lt;/xsl:stylesheet&gt;
</code></pre>
<p>You can view the 'finished' <a href="/files/xml_creation/part8-2.xml" target="_blank">XML</a> and <a href="/files/xml_creation/part8-2.xslt" target="_blank">XSLT</a>.</p>
<h3>Next time ... ?</h3>
<p>At this point all I really need to do is finish adding the games that I own. While it would be nice to have some other features, it's not completely necessary.</p>
<p><a href="http://jamesrskemp.net/video_games.xml" target="_blank">My video games</a>.</p>
