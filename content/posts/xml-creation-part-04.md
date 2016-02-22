+++
title = "XML creation: Part 4"
summary = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part four, I'll be adding a DTD so our XML document validates. [slnet0514:769eb188-7161-431e-ac7d-dbce70e0708d]"
draft = false
comments = true
date = "2007-12-28T19:00:00-06:00"
modified = "2007-12-27T22:00:21-06:00"
slug = "XML-creation-Part-04"
blogengine = "769eb188-7161-431e-ac7d-dbce70e0708d"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>
In this guide, I&#39;ll be creating an XML file to store the Playstation games I own, and ultimately make the XML file &#39;pretty&#39; for Web browsers. I&#39;ve done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>. 
</p>
<div class="note">
<p>
In part four, I&#39;ll be adding a DTD so our XML document validates. 
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
While it displays, and is basically formatted correctly, <a href="/files/xml_creation/part3.xml" target="_blank">the XML file</a> won&#39;t <a href="http://www.validome.org/xml/validate/" target="_blank">validate</a>. Time to fix this. 
</p>
<h3>Overview</h3>
<p>
In order to make the file validate we can do a number of things. For now, we&#39;ll create a DTD file - a Document Type Definitions file - which is probably the easiest to make. 
</p>
<p>
We&#39;ll need to create the DTD, as well as make a couple of modifications to the XML file. 
</p>
<h3>XML file modifications</h3>
<p>
The modifications we&#39;ll be making to the XML file are pretty simple. 
</p>
<p>
First, we&#39;ll state that the XML file requires another file. To do this&nbsp;we need merely change the first line from: 
</p>
<blockquote>
	<p>
	&lt;?xml version=&quot;1.0&quot;?&gt; 
	</p>
</blockquote>
<p>
to: 
</p>
<blockquote>
	<p>
	&lt;?xml version=&quot;1.0&quot; <strong>standalone=&quot;no&quot;</strong>?&gt; 
	</p>
</blockquote>
<p>
The addition is now in bold. 
</p>
<p>
Next, we need to add a second line, as follows: 
</p>
<blockquote>
	<p>
	&lt;!DOCTYPE games SYSTEM &quot;http://strivinglife.com/files/xml_creation/part4.dtd&quot;&gt; 
	</p>
</blockquote>
<p>
Here I&#39;ve actually already determined where I&#39;ll be storing the file. 
</p>
<div class="tip">
<p>
You&#39;ll want to use a better filename than what I&#39;ve used, when you really create your DTD. 
</p>
</div>
<p>
You can view the source of <a href="/files/xml_creation/part4.xml" target="_blank">the modified XML file</a> to see this. 
</p>
<h3>The Document Type Definitions (DTD)</h3>
<p>
Here it is. We&#39;ll go over the details after the code. 
</p>
<blockquote>
	<p>
	&lt;!ELEMENT games (game*)&gt; 
	</p>
	<p>
	&lt;!ELEMENT game (title, system*, purchase*, sell*, own, notes)&gt;<br />
	&lt;!ATTLIST game id CDATA #REQUIRED&gt; 
	</p>
	<p>
	&lt;!ELEMENT title (#PCDATA)&gt;<br />
	&lt;!ELEMENT system (console, version)&gt;<br />
	&lt;!ELEMENT purchase (date, price, place)&gt;<br />
	&lt;!ELEMENT sell (date, price)&gt;<br />
	&lt;!ELEMENT own (#PCDATA)&gt;<br />
	&lt;!ELEMENT notes (#PCDATA)&gt; 
	</p>
	<p>
	&lt;!ELEMENT console (#PCDATA)&gt;<br />
	&lt;!ELEMENT version (#PCDATA)&gt; 
	</p>
	<p>
	&lt;!ELEMENT date (#PCDATA)&gt;<br />
	&lt;!ELEMENT price (#PCDATA)&gt; 
	</p>
	<p>
	&lt;!ELEMENT place (#PCDATA)&gt;&nbsp; 
	</p>
</blockquote>
<p>
First, we have <strong>&lt;!ELEMENT games (game*)&gt;</strong> .&nbsp; We&#39;ll use ELEMENT for each element that is used within the XML document, so you&#39;ll notice one for each. 
</p>
<p>
In this case, we&#39;re stating that the <strong>games</strong> element has the sub-element, or child,&nbsp;of <strong>game</strong>,&nbsp;which can&nbsp;occur zero&nbsp;or more times&nbsp;(note the asterisk). Since the other elements do not have an asterisk, that means that that element can only occur once. Other options include: 
</p>
<ul>
	<li>+ : Minimum of one occurrence</li>
	<li>? : Zero or one occurrence</li>
</ul>
<p>
Further down, we have <strong>&lt;!ATTLIST game id CDATA #REQUIRED&gt;</strong> . In this case, we see that the <strong>game</strong> element has an <strong>id</strong> attribute, and consists of character data; <strong>CDATA</strong> signifies character&nbsp;data. This attribute is also required. 
</p>
<p>
Following that we have <strong>&lt;!ELEMENT title (#PCDATA)&gt;</strong> . Instead of a listing of elements, we instead have <strong>#PCDATA</strong>, which means this element contains &#39;parsed&#39; character data. Whatever parses, or reads, this XML data will also examine this element, in this case the title element, for entities and markup. 
</p>
<p>
Once we save this file to the place denoted in the XML file, we&#39;re ready to run it past validation. 
</p>
<p>
Validome has a great validator, which handles a number of different formats. You can <a href="http://www.validome.org/xml/validate/?lang=en&amp;url=http://strivinglife.com/files/xml_creatio" target="_blank">view the results of validation</a> by entering your own URL, or <a href="/files/xml_creation/part4.xml" target="_blank">using mine</a>. 
</p>
<div class="note">
<p>
You&#39;ll notice that both the XML and DTD will show under validated files. If both don&#39;t appear, then the DTD isn&#39;t &#39;linked to&#39; from the XML file, or you&#39;re not validating the XML file. 
</p>
</div>
<h3>Another way to work through the DTD</h3>
<p>
If you&#39;d like, you can also work through the DTD by emptying the DTD and validating the XML file. Then, you can add lines as needed, to clear up errors. 
</p>
<h3>Next time ...</h3>
<p>
In part five, we&#39;ll be using a CSS file to style our XML file. 
</p>
<p>
Then, in part six, we&#39;ll be using an XSLT file to style our XML file, instead. 
</p>
<p>
Each has it&#39;s benefits, and since they&#39;re both different, we&#39;ll cover them separate for ease. 
</p>

