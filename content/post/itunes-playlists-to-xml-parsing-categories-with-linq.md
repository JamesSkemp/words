+++
title = "iTunes Playlists to Xml: Parsing categories with LINQ"
description = "LINQ to parse the XML export from iTunes Playlists to Xml for musical genres/categories."
draft = false
comments = true
date = "2010-10-20T08:35:00-05:00"
modified = "2010-10-28T07:54:42-05:00"
slug = "iTunes-Playlists-to-Xml-Parsing-categories-with-LINQ"
blogengine = "97c45ece-420e-47e6-992d-c73dbf23cdf8"
categories = ["StrivingLife", "tutorials / guides"]
tags = ["linq to xml", "itunes playlists to xml", "music", "resume"]
+++

<p>I recently had the need to determine what types of music I had within my collection of music. Since I&nbsp;created <a rel="external" href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml">iTunes Playlists to Xml</a> so that I could export out my library on my iPod, it was easy enough to run that and then open <a rel="external" href="http://www.linqpad.net/">LINQPad</a> to run the following query.</p>
<p>Obviously, you must export the Genre field in order for the following query to work.</p>
<pre class="code"><code class="csharp">// Location to the XML from iTunes Playlists to XML
String playlistXml = @"C:\Users\James\Projects\services\WcfRestService\App_Data\playlistXml.xml";

XDocument xml = XDocument.Load(playlistXml);

var categories = from track in xml.Descendants("track")
	group track by track.Element("genre").Value into t
	orderby t.Key
	//orderby t.Count() descending
	select new {
		Category = t.Key,
		Count = t.Count()
	};
				
categories.Dump();</code></pre>
<p>Note that you can switch the orderby lines depending upon how you want to sort the returned data.</p>
<p>This may be something I eventually build into my application, along with other reporting features. I know that I'd love to have some comparision functionality, either built-in or as another application, so that I can see how my music tastes change, or if I'm consistent.</p>
<h3>Sample output</h3>
<p>With some cleanup, sample output is as follows.</p>
<ul>
<li>Alternative - 279</li>
<li>Alternative &amp; Punk - 154</li>
<li>Alternative Rock - 282</li>
<li>Blues - 120</li>
<li>Books &amp; Spoken - 145</li>
<li>Children's Music - 12</li>
<li>Classical - 255</li>
<li>Country - 104</li>
<li>Dance - 76</li>
<li>Dance &amp; DJ - 220</li>
<li>Easy Listening - 20</li>
<li>Electronic - 278</li>
<li>Electronica/Dance - 91</li>
<li>Folk - 319</li>
<li>French Pop - 90</li>
<li>Gospel &amp; Religious - 18</li>
<li>Hard Rock &amp; Metal - 6</li>
<li>Hip Hop/Rap - 88</li>
<li>Holiday - 18</li>
<li>House - 4</li>
<li>Industrial - 107</li>
<li>Industrial Metal - 17</li>
<li>Jazz - 30</li>
<li>J-Pop - 48</li>
<li>J-Rock - 23</li>
<li>Lo-Fi - 35</li>
<li>Metal - 82</li>
<li>New Age - 270</li>
<li>Pop - 1225</li>
<li>Pop/Rock - 26</li>
<li>R&amp;B - 105</li>
<li>R&amp;B/Soul - 81</li>
<li>Reggae - 30</li>
<li>Rock - 3125</li>
<li>Soundtrack - 348</li>
<li>World - 57</li>
</ul>
