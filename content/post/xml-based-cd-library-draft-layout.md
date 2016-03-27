+++
title = "XML-based CD library: Draft layout"
description = "Draft layout for an XML-based CD/album library."
draft = false
comments = true
date = "2009-01-09T17:04:00-06:00"
modified = "2009-01-09T17:32:21-06:00"
slug = "XML-based-CD-library-Draft-layout"
blogengine = "83edd19a-ebf1-4623-9b4e-404b17b83566"
categories = ["article", "StrivingLife"]
tags = ["xml"]
+++

<p>
Following close on the heels of my <a href="/words/post/XML-based-book-library-Draft-layout.aspx">XML-based book library draft</a> (and release), below is a draft layout for keeping track of my CDs.
</p>
<p>
Here&#39;s what I currently track:
</p>
<ul>
	<li>Artist</li>
	<li>
	<div>
	CD Name
	</div>
	</li>
	<li>
	<div>
	Date bought
	</div>
	</li>
	<li>
	<div>
	Place bought
	</div>
	</li>
	<li>
	<div>
	Bought price
	</div>
	</li>
	<li>
	<div>
	Number of songs
	</div>
	</li>
	<li>
	<div>
	Time (which I don&#39;t fill in very often)
	</div>
	</li>
	<li>
	<div>
	Misc info/notes
	</div>
	</li>
</ul>
<p>
Following the iTunes standard, each CD has a main artist. Songs, which could be listed (and which I listed back when I had this in Access, I did so), could have their own artists.
</p>
<p>
It would be nice to be able to tie this in with an iTunes library&#39;s XML export, but I&#39;m not quite sure how that would be done.
</p>
<p>
I also feel it important to have this XML since it stores purchase information (but the songs and time could easily drop).
</p>
<p>
Based on this, draft layout is as follows.
</p>
<ul>
	<li>
	<div>
	albums
	</div>
	<ul>
		<li>
		<div>
		album id=&quot;&quot;
		</div>
		<ul>
			<li>
			<div>
			title
			</div>
			</li>
			<li>
			<div>
			artist
			</div>
			</li>
			<li>
			<div>
			purchase
			</div>
			<ul>
				<li>
				<div>
				<em>date</em>
				</div>
				</li>
				<li>
				<div>
				<em>place</em>
				</div>
				</li>
				<li>
				<div>
				<em>price</em>
				</div>
				</li>
			</ul>
			</li>
			<li>
			<div>
			notes
			</div>
			</li>
		</ul>
		</li>
	</ul>
	</li>
</ul>
<p>
Artist could become artists with children of artist, and a format element could be added rather easily. However, since I&#39;m not sure that tracking artists is the primary purpose ... I&#39;m going to leave it as it is.
</p>
<p>
As before, items in italics are optional.
</p>
<p>
Once the schema has been created, I&#39;ll post a link.
</p>

