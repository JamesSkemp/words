+++
title = "iTunes Playlists to Xml - version 0.2b released"
summary = "Version 0.2b of iTunes Playlists to Xml is now available for download."
draft = false
comments = false
date = "2009-02-26T08:05:00-06:00"
modified = "2009-10-30T23:22:57-05:00"
slug = "iTunes-Playlists-to-Xml-version-02b-released"
blogengine = "ff521bfb-4f27-4731-bec8-771a9510e2ee"
categories = ["software", "StrivingLife"]
tags = ["ipod", "xml"]
+++

<div class="warning">
<p>This application has since been updated. <a href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">Read about the current version of iTunes Playlists to Xml.</a></p>
</div>
<p>Previously <a href="/words/post/Parsing-iTunes-data-with-C.aspx">I discussed an iTunes application that I was working on</a>, in C#. That application has been fixed up a bit, and is now available for download.</p>
<p><a href="http://jamesrskemp.com/applications/iTunesPlaylistsToXml_0.2b.zip">Download iTunes Playlists to Xml - version 0.2b</a>.</p>
<p>To run the application extract the contents of the zip to a directory. Then open iTunesApplication.exe. If iTunes is not running, it will start before this application does.</p>
<p>Once it's started you'll see a listing of available sources (computer and iPod only), as well as a listing of all playlists for the selected source.</p>
<p>Clicking on a playlist will generate Xml output, for use elsewhere.</p>
<h3>Known issues</h3>
<p>If you start this application and then plug in an iPod, that new source (the iPod) won't be available until the application restarts.</p>
<p>There's no progress indicator when you select a playlist.</p>
<p>Generating the Xml output can be a bit slow (but I'm not sure that this is something I can resolve).</p>
<p>'Foreign' characters are not escaped correctly.</p>
<h3>Future features</h3>
<p>The ability to select what items you want in the Xml output.</p>
<p>A schema by which to validate the Xml contents.</p>
<p>A stylesheet that can be used for basic styling of Xml output.</p>
