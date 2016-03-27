+++
title = "Music application idea"
description = "A music application idea, that I'll be working on implementing."
draft = false
comments = true
date = "2010-05-25T22:23:00-05:00"
modified = "2010-05-25T22:37:52-05:00"
slug = "Music-application-idea"
blogengine = "e5a436f2-db22-41d5-95d1-d9160a4834a2"
categories = ["software", "StrivingLife"]
tags = ["music"]
+++

<p>Surprisingly, it was way back in September of last year that I realized <a href="http://strivinglife.com/words/post/Music-Recommendations-Please!-045-beta-released.aspx">Music Recommendations Please!</a>, which I hoped would help me discover new music (and perhaps help others as well).</p>
<p>Since then&nbsp;I haven't used it as much as I would have hoped, but that's mostly because I'm not happy with how easy it is to get more than one artist in at a time, and generate helpful 'reports' from data returned for multiple artists.</p>
<p>Thanks to <a href="http://strivinglife.com/words/post/iTunes-Playlists-to-Xml-version-16-released.aspx">iTunes Playlists to Xml</a> I'm able to generate very nice XML files which I can then parse with LINQPad, but again, outside of the couple statements I save (and which I seemingly haven't been sharing), there's no real reporting functionality.</p>
<p>Ideally, the best of both worlds would be to point to one of these generated XML files, get a listing of artists that are enjoyed, and then return a listing of artists that may also be enjoyed, with appropriate weighting applied, since artists showing up multiple times would necessarily have their rating increased. Similarly, if an artist was purchased, but not enjoyed, that too would impact the results.</p>
<p>Now if it was&nbsp;a Web site I wouldn't necessarily want to allow users to upload XML files (mine is almost at 3.25 MB, with all data pulled), but it would offer much more flexibility. Perhaps a hybrid would be the best solution.</p>
<p>For the desktop application, either point to an XML file (from iTunes Playlists to Xml) or allow one or more artists to be manually entered. The Web would only allow the latter. Once a button is pressed either Last.fm or Yahoo! would be called and similar artists would be returned, sorted by number of times they show up and 'rating.'</p>
<p>Returned results could then be filtered and/or removed, as well as dug into even further. The listing would need to be exportable, but having links to purchase from Amazon would also be more than okay.</p>
<p>Seeing as how I've already done the work, albeit in pieces, it seems it just needs to be put together now.</p>
