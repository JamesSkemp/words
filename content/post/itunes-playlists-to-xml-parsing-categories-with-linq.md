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

I recently had the need to determine what types of music I had within my collection of music. Since I&nbsp;created <a rel="external" href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml">iTunes Playlists to Xml</a> so that I could export out my library on my iPod, it was easy enough to run that and then open <a rel="external" href="http://www.linqpad.net/">LINQPad</a> to run the following query.

Obviously, you must export the Genre field in order for the following query to work.

```csharp
// Location to the XML from iTunes Playlists to XML
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

categories.Dump();
```

Note that you can switch the orderby lines depending upon how you want to sort the returned data.

This may be something I eventually build into my application, along with other reporting features. I know that I'd love to have some comparision functionality, either built-in or as another application, so that I can see how my music tastes change, or if I'm consistent.

### Sample output

With some cleanup, sample output is as follows.

- Alternative - 279
- Alternative &amp; Punk - 154
- Alternative Rock - 282
- Blues - 120
- Books &amp; Spoken - 145
- Children's Music - 12
- Classical - 255
- Country - 104
- Dance - 76
- Dance &amp; DJ - 220
- Easy Listening - 20
- Electronic - 278
- Electronica/Dance - 91
- Folk - 319
- French Pop - 90
- Gospel &amp; Religious - 18
- Hard Rock &amp; Metal - 6
- Hip Hop/Rap - 88
- Holiday - 18
- House - 4
- Industrial - 107
- Industrial Metal - 17
- Jazz - 30
- J-Pop - 48
- J-Rock - 23
- Lo-Fi - 35
- Metal - 82
- New Age - 270
- Pop - 1225
- Pop/Rock - 26
- R&amp;B - 105
- R&amp;B/Soul - 81
- Reggae - 30
- Rock - 3125
- Soundtrack - 348
- World - 57
