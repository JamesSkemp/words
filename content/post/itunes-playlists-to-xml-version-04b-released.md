+++
title = "iTunes Playlists to Xml - version 0.4b released"
description = "iTunes Playlists to Xml, which creates an Xml file based upon iTunes playlists, has been updated to version 0.4b."
draft = false
comments = false
date = "2009-03-02T23:11:00-06:00"
modified = "2009-10-30T23:23:05-05:00"
slug = "iTunes-Playlists-to-Xml-version-04b-released"
blogengine = "4ceb39a3-8b46-4d45-9706-47205f084b18"
categories = ["software", "StrivingLife"]
tags = ["ipod", "xml", ".net"]
+++

<div class="warning">
<p>This application has since been updated. <a href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">Read about the current version of iTunes Playlists to Xml.</a></p>
</div>
<p>Having just released version 0.3b of iTunes Playlists to Xml, I've got yet <em>another</em> release.</p>
<p>This release includes menus, the ability to select what data you want in the Xml, and a schema for validation.</p>
<p>Unfortunately, I've discovered one bug (that would have existed before) with playlists getting updated in iTunes, between the refresh in this application, and the time it was clicked on. The application ignores the request for the playlist's tracks.&nbsp;My guess (which just&nbsp;came to me)&nbsp;is that it's because I'm using the name and track count to check against the playlist in iTunes.</p>
<p>I did not update the XSLT, but am instead going to leave it as is, as a working point for others (and may write a tutorial on doing so, to serve another purpose).</p>
<p>I got to do some new stuff with the XSD creation, but that should be set, no matter what is selected in the application.</p>
<p>Otherwise, I'm pretty happy with how it's turning out.</p>
<p>Next time I hope to have 'Save' functionality implemented, so that the Xml file can be saved with the click of a button. I'll also be attempting to create or find an icon for the application. After some thought, I'm torn about using an installer; it's two files, so ... ?</p>
<p><a href="http://jamesrskemp.com/applications/iTunesPlaylistsToXml_0.4b.zip">Download iTunes Playlists to Xml - version 0.4b</a>.</p>
<p>As before, comments/suggestions appreciated. As it is, I believe I'm pretty close to version 1.0 (final).</p>
