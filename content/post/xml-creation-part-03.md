+++
title = "XML creation: Part 3"
summary = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part three, I'll be adding the actual data that we'll start with. [slnet0514:22e73a03-3931-480a-8260-fbb1986356c8]"
draft = false
comments = true
date = "2007-12-27T19:15:00-06:00"
modified = "2007-12-27T19:19:37-06:00"
slug = "XML-creation-Part-03"
blogengine = "22e73a03-3931-480a-8260-fbb1986356c8"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>
In this guide, I&#39;ll be creating an XML file to store the Playstation games I own, and ultimately make the XML file &#39;pretty&#39; for Web browsers. I&#39;ve done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>. 
</p>
<div class="note">
<p>
In part three, I&#39;ll be adding the actual data that we&#39;ll start with. 
</p>
</div>
<h3>Last time ...</h3>
<p>
In <a href="/words/post/XML-creation-Part-01.aspx">part one</a>, I went over what kind of data would be stored in our XML document. 
</p>
<p>
In <a href="/words/post/XML-creation-Part-02.aspx">part two</a>, I created a structure that I believe will work for the data. 
</p>
<h3>The data</h3>
<p>
This time, we&#39;ll start adding actual data into the XML file. 
</p>
<p>
Listed below are the Playstation 3 games I currently own. 
</p>
<p>
<table border="1" cellspacing="0" style="background-color: #fff">
	<caption><strong>PlayStation Games</strong></caption>
	<thead>
		<tr>
			<th>Game Name</th><th>System</th><th>Bought At</th><th>Bought Date</th><th>Bought Price</th><th>Comments</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>flOw Expansion Pack (Add-On Content)</td>
			<td>PS3</td>
			<td>Playstation Network</td>
			<td>2007.11.20</td>
			<td align="right">$2.99</td>
			<td>&nbsp;</td>
		</tr>
		<tr valign="top">
			<td>flOw</td>
			<td>PS3</td>
			<td>Playstation Network</td>
			<td>2007.11.17</td>
			<td align="right">$7.99</td>
			<td>Bought online.</td>
		</tr>
		<tr valign="top">
			<td>Everyday Shooter (Full Game)</td>
			<td>PS3</td>
			<td>Playstation Network</td>
			<td>2007.12.13</td>
			<td align="right">$9.99</td>
			<td>&nbsp;</td>
		</tr>
		<tr valign="top">
			<td>Warhawk</td>
			<td>PS3</td>
			<td>Best Buy #59 - Madison 53704 (East)</td>
			<td>2007.12.24</td>
			<td align="right">$45.99</td>
			<td>Bought online, using $15 in reward zone points. Came with headset.</td>
		</tr>
		<tr valign="top">
			<td>Uncharted: Drake&#39;s Fortune</td>
			<td>PS3</td>
			<td>Best Buy #59 - Madison 53704 (East)</td>
			<td>2007.12.10</td>
			<td align="right">$59.99</td>
			<td>&nbsp;</td>
		</tr>
		<tr valign="top">
			<td>Heavenly Sword</td>
			<td>PS3</td>
			<td>Best Buy #59 - Madison 53704 (East)</td>
			<td>2007.11.19</td>
			<td align="right">$53.99</td>
			<td>10% off coupon used</td>
		</tr>
		<tr valign="top">
			<td>MotorStorm</td>
			<td>PS3</td>
			<td>Best Buy #208 (West Madison)</td>
			<td>2007.11.17</td>
			<td align="right">$0.00</td>
			<td>Came with PS3.</td>
		</tr>
	</tbody>
	<tfoot>
	</tfoot>
</table>
</p>
<h3>Importing the data</h3>
<p>
Now that we know what we need to enter, it&#39;s just a matter of actually adding it. You can use a tool to do this, but, for now, I&#39;ll just manually enter it in. 
</p>
<h3>The new XML file</h3>
<p>
Skipping ahead, here&#39;s <a href="/files/xml_creation/part3.xml" target="_blank">the XML file with the seven records added</a>. 
</p>
<p>
With the exception of adding an &#39;id,&#39; the XML file shouldn&#39;t contain anything that wasn&#39;t in <a href="/files/xml_creation/part2.xml" target="_blank">the first iteration</a>. 
</p>
<h3>Next time ...</h3>
<p>
You may or may not have noticed (you probably didn&#39;t) that the file won&#39;t validate. In part four, we&#39;re make this validate according to a Document Type Declarations/Definitions (DTD). 
</p>
<p>
While we could work with layout first, I think validation is much more important ... 
</p>

