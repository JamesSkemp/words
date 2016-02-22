+++
title = "XML Schema Definition creation: Journal - Part 1: Primary layout"
summary = "In part 1 of a new series, I cover how I created a new XML Schema Definition for journal-like XML files."
draft = false
comments = true
date = "2009-12-21T07:50:00-06:00"
modified = "2009-12-21T08:01:08-06:00"
slug = "XML-Schema-Definition-creation-Journal-Part-1-Primary-layout"
blogengine = "0f491b03-1705-4314-bb09-9ad8630cfcf2"
categories = ["tutorials / guides"]
tags = ["xml", "xml schema definition", "xsd"]
+++

<p>In <a href="http://strivinglife.com/words/post/XML-creation-Part-01.aspx">a previous series</a>, I went over the process of creating a new XML document to store <a href="http://jamesrskemp.com/video_games.xml">my video games</a>. (Although in that case I used a DTD.)</p>
<p>This time I'm going to work on a schema to store quasi-journal entries, which I'm hoping will help with my goal to write every day.</p>
<h3>What I hope to accomplish</h3>
<p>Ultimately I want to store a bit of text for any particular day. The entry should have a date and time associated with it, for both when it was initially created, as well as last updated.</p>
<p>The format should also allow supplemental content to be added and associated with an entry. This supplemental content could be added the same day, or years later.</p>
<p>The content should accept HTML formatting. Comments from non-authors don't need to be stored or tracked.</p>
<h3>Sample layout</h3>
<p>After thinking about these needs, I came up with a structure like this on the 15th. Thus far, I haven't seen much need to expand it.</p>
<ul>
<li>journal source 
<ul>
<li>entry id 
<ul>
<li>author 
<ul>
<li>name</li>
</ul>
</li>
<li>dateCreated</li>
<li>dateUpdated</li>
<li>text</li>
<li>supplements 
<ul>
<li>supplement id 
<ul>
<li>dateAdded</li>
<li>text</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<h3>Explanation of elements</h3>
<p>The journal element is what ties it all together. It has a source attribute, which ties all individual journals, from a particular source (hence the name),&nbsp;to a single URI. The source could be a site, service, or person, although each entry could be associated with someone.</p>
<p>Within the journal element is one or more entry elements, which have a unique id attribute. When designing, I envisioned this as GUID (modelling after BlogEngine.NET, with GUIDs being assigned to each post). I also saw each entry being a daily addition. Either way, once a core entry is created (the text element), I didn't see that it (the core entry text)&nbsp;would be updated any further.</p>
<p>There's an author element next, which currently stores a name, but could be extended to include an email, Web site, and etcetera.</p>
<p>The next two date elements are fairly obvious, with the first being permanent, and the second being set to the first when the entry is initially created, then updated as each supplement is added.</p>
<p>The text element -&nbsp;which was&nbsp;initially&nbsp;called entry before adding the parent - stores the HTML content of the entry. Again, outside of minor edits, I don't see this content as changing, much like an actual paper journal.</p>
<p>The supplements element contains one or more supplement elements. These have a dateAdded element, but no element to store an update date. It also has an id attribute (an addition from what I intially outlined on paper), which is just an increasing number, from 1 up, unique to the entry. Like the core entry, it has a text element that stores HTML content of the addition.</p>
<p>The supplements are meant to add additional notes or comments to the original entries, by the author of the original. Again, I did not envision this having any commenting, outside of that by the author.</p>
<p>I also initially saw each entry as being within its own file, but after further thought, believe that a single file could store a month or year's worth of entries.</p>
<h3>Next steps</h3>
<p>Before starting on the schema itself I want to research XInclude, to determine whether this would work for pulling multiple entries into a single core XML document. Depending upon what that suggests will determine how the base layout changes, if at all.</p>
<h3>Update: XInclude research</h3>
<div class="note">
<p>Not per se an update for users, since the post is scheduled for the day after I actually wrote it, but ...</p>
</div>
<p>While my editor, &lt;oXygen&gt; XML Editor, supports XInclude, for the purposes of this schema I don't believe XInclude is going to be all that helpful.</p>
<p>It might just be that the source referred to will have to handle the individual journal files, however it sees fit. This allows each entry to&nbsp;be either a single entity or contain a number of entries, depending upon the needs and use of the individual author(s).</p>
<p>If you're interested, here's the source I used. Pulling this up in Internet Explorer 8.0, as is, doesn't display it as&nbsp;I would expect, but Author mode in &lt;oXygen/&gt; XML Editor displays it correctly.</p>
<h4>parent.xml</h4>
<pre class="code"><code class="xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;testParent xmlns:xi="<a href="http://www.w3.org/2001/XInclude">http://www.w3.org/2001/XInclude</a>"&gt;
	&lt;xi:include href="child1.xml"/&gt;
	&lt;xi:include href="child2.xml"/&gt;
	&lt;xi:include href="child3.xml"/&gt;
&lt;/testParent&gt;</code></pre>
<h4>child<em>x</em>.xml</h4>
<p>The same content was used for each of the three.</p>
<pre class="code"><code class="xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;child&gt;
	&lt;text&gt;asdf&lt;/text&gt;
&lt;/child&gt;</code></pre>
