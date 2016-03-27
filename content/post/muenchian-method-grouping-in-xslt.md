+++
title = "Muenchian Method grouping in XSLT"
description = "My investigations on how the Muenchian Method of grouping in XSLT 1.0 works."
draft = false
comments = true
date = "2009-07-01T22:09:00-05:00"
modified = "2009-07-01T22:46:41-05:00"
slug = "Muenchian-Method-grouping-in-XSLT"
blogengine = "4c43cf08-e413-4d17-843b-ab5d5d006938"
categories = ["article", "tutorials / guides"]
tags = ["xml", "xslt"]
+++

<p>I owe a deal of thanks for figuring out the Muenchian Method of grouping in XSLT (1.0) to Jeni's article <a href="http://jenitennison.com/xslt/grouping/muenchian.xml">Grouping Using the Muenchian Method</a>. It took, however, a while for me to get my mind around the method completely, and some experimentation, which I'm sharing below.</p>
<p>Specifically I was looking to get a listing of tracks, from my <a href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">iTunes Playlists to Xml</a> application's output, and group them by album.</p>
<p>For this, all I really need is the track's album and name, which gives a basic layout of the following.</p>
<pre class="code"><code class="xml">&lt;playlist&gt;
	&lt;track&gt;&lt;name&gt;Smile&lt;/name&gt;&lt;album&gt;Alright, Still&lt;/album&gt;&lt;/track&gt;
	&lt;track&gt;&lt;name&gt;Knock &amp;apos;Em Out&lt;/name&gt;&lt;album&gt;Alright, Still&lt;/album&gt;&lt;/track&gt;
	&lt;!-- Additional tracks removed. --&gt;
&lt;/playlist&gt;</code></pre>
<p>&nbsp;Now the first thing you'll need is a key, that you'll be using to group things by. In this case, since I want to group by album, that will be my key. Immediately before any &lt;xsl:template/&gt; elements I added the following key.</p>
<pre class="code"><code class="xml">&lt;xsl:key name="tracks-by-album"
	match="track"
	use="album"/&gt;</code></pre>
<p>Here we're grouping the tracks, by the album value.</p>
<p>Now that we have a key, we can, for example, grab just those tracks that are from a certain album.</p>
<pre class="code"><code class="xml">&lt;xsl:template match="/"&gt;
	&lt;ul&gt;
		&lt;xsl:for-each select="key('tracks-by-album', '1492: Conquest of Paradise')"&gt;
			&lt;li&gt;&lt;xsl:value-of select="name"&gt;&lt;/xsl:value-of&gt;&lt;/li&gt;
		&lt;/xsl:for-each&gt;
	&lt;/ul&gt;
&lt;/xsl:template&gt;</code></pre>
<p>This will only output those tracks from the album Vangelis' <span style="text-decoration: underline;">1492: Conquest of Paradise</span>.</p>
<p>Stepping back, if I just wanted to grab the first track's album, I could do the following.</p>
<pre class="code"><code class="xml">&lt;xsl:template match="/"&gt;
	&lt;ul&gt;
		&lt;xsl:for-each select="/playlist/track[1]"&gt;
			&lt;li&gt;&lt;xsl:value-of select="album"/&gt;&lt;/li&gt;
		&lt;/xsl:for-each&gt;
	&lt;/ul&gt;
&lt;/xsl:template&gt;</code></pre>
<p>That suggests that this code is doing, which will go through every album, and display the first track.</p>
<pre class="code"><code class="xml">&lt;xsl:template match="/"&gt;
	&lt;ul&gt;
		&lt;xsl:for-each select="/playlist/track[count(. | key('tracks-by-album', album)[1]) = 1]"&gt;
			&lt;xsl:sort select="album"/&gt;
			&lt;li&gt;&lt;xsl:value-of select="album"/&gt;
				&lt;ul&gt;
					&lt;li&gt;&lt;xsl:value-of select="name"/&gt;&lt;/li&gt;
				&lt;/ul&gt;
			&lt;/li&gt;
		&lt;/xsl:for-each&gt;
	&lt;/ul&gt;
&lt;/xsl:template&gt;</code></pre>
<p>And with a slight tweak, you can loop through and display all the song names from each album.</p>
<pre class="code"><code class="xml">&lt;xsl:template match="/"&gt;
	&lt;ul&gt;
		&lt;xsl:for-each select="/playlist/track[count(. | key('tracks-by-album', album)[1]) = 1]"&gt;
			&lt;xsl:sort select="album"/&gt;
			&lt;li&gt;
				&lt;xsl:value-of select="album"/&gt;
				&lt;ul&gt;
					&lt;xsl:for-each select="key('tracks-by-album', album)"&gt;
						&lt;li&gt;&lt;xsl:value-of select="name"/&gt;&lt;/li&gt;
					&lt;/xsl:for-each&gt;
				&lt;/ul&gt;
			&lt;/li&gt;
		&lt;/xsl:for-each&gt;
	&lt;/ul&gt;
&lt;/xsl:template&gt;</code></pre>
<p>And after all that discovery, I have exactly what I want; a listing of tracks, grouped by albums. With only slight modification, the grouping can be changed to artist, or any one of any other number of items.</p>
<p>Now if only IE 7+ supported for-each-group, available in&nbsp;XSLT 2.0, this wouldn't be necessary.</p>
