+++
title = "iTunes Playlists to Xml - version 1.5.1 released"
description = "Version 1.5.1 of iTunes Playlists to Xml has been released."
draft = false
comments = false
date = "2009-11-14T16:55:00-06:00"
modified = "2010-05-08T15:01:56-05:00"
slug = "iTunes-Playlist-to-Xml-version-151-released"
blogengine = "f3a75081-3e0a-477a-87b3-f8f311221ea8"
categories = ["software", "StrivingLife"]
tags = ["itunes playlists to xml", "itunes", "ipod", "xml", ".net"]
+++

<div class="warning">
<p>This application has since been updated. <a href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">Read about the current version of iTunes Playlists to Xml.</a></p>
</div>
<div class="note">
<p><a rel="external download" href="http://jamesrskemp.com/applications/iTunesPlaylistsToXml_1.5.2.1.zip">Version 1.5.2.1</a> is available for download, which fixes an issue with version 1.5.2. Thanks to Pierre for bringing this to my attention.</p>
</div>
<div class="note">
<p><a rel="external download" href="http://jamesrskemp.com/applications/iTunesPlaylistsToXml_1.5.2.zip">Version 1.5.2</a> is available for download, which adds the -output argument.</p>
</div>
<p>Version 1.5.1 of iTunes Playlists to Xml is now available for download.</p>
<p>Download <a rel="external download" href="http://jamesrskemp.com/applications/iTunesPlaylistsToXml_1.5.1.zip">iTunes Playlists to Xml 1.5.1</a>.</p>
<h3>Installing and more information</h3>
<p>If you're new to iTunes Playlists to Xml, I've created a 'product page' for <a rel="external" href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">iTunes Playlists to Xml</a> with all the information needed to get started.</p>
<h3>Upgrading</h3>
<p>To upgrade from <strong>any version of 1.4 or 1.5</strong>&nbsp;you simply need to replace the <strong>iTunesPlaylistsToXml.exe</strong> file with the one in the above archive. You should not need to update your configuration.</p>
<p>To upgrade from <strong>version 1.3 or earlier</strong>, extract the contents of the zip replacing everything <em>but</em> the iTunesPlaylistsToXml.exe.config file; when you start the application after upgrading the configuration file <em>should</em> be automatically upgraded with all new settings. If you get a configuration error, then replace this file with the new version. Remember to update your name in the Settings.</p>
<h3>Changes from version 1.5</h3>
<p>Version 1.5.1 of iTunes Playlists to Xml adds the ability to use command-line arguments when starting the application. The following arguments can be used:</p>
<ul>
<li>-connect 
<ul>
<li>Will automatically connect to iTunes when the program starts.</li>
</ul>
</li>
<li>-source:x <em>or</em> -source:"x" 
<ul>
<li>Will automatically attempt to select the source with a name of <em>x</em> after connecting to iTunes.</li>
</ul>
</li>
<li>-playlist:x <em>or</em> -playlist:"x" 
<ul>
<li>Will automatically attempt to select the playlist with a name of <em>x</em> after connecting to iTunes.</li>
<li>-source is required if using -playlist.</li>
</ul>
</li>
<li>-output:x <em>or</em> -output:"x" 
<ul>
<li>Will check the defined output items, comma-delimited, by default after startup.</li>
<li>Requires version 1.5.2 or later.</li>
</ul>
</li>
<li>-save 
<ul>
<li>Will automatically save any generated playlist to Xml, once it is generated.</li>
</ul>
</li>
<li>-exit 
<ul>
<li>Will automatically exit the program after saving a playlist.</li>
<li>Both -connect and -save are required when using -exit.</li>
<li>If there is a problem saving the playlist to a file, the program will not automatically exit.</li>
</ul>
</li>
</ul>
<p>For example, running the following from the command line will connect to iTunes immediately, select the <strong>James Skemp's 80 gig</strong> source and <strong>My Top Rated</strong> playlist.</p>
<pre class="code"><code class="powershell">iTunesPlaylistsToXml.exe -connect -source:"James Skemp's 80 gig" -playlist:"My Top Rated"</code></pre>
<p>The following will do the same as above as well as save the playlist and exit immediately.</p>
<pre class="code"><code class="powershell">iTunesPlaylistsToXml.exe -connect -source:"James Skemp's 80 gig" -playlist:"My Top Rated" -save -exit</code></pre>
<h3>Features for&nbsp;future releases</h3>
<p>A future&nbsp;release will allow you to change the elements that are output by default, as well as set these via the command line.</p>
<p>Additionally I'll be adding the ability to change how the output files are named (amount of flexibility to be determined), and where they are saved.</p>
<h3>Suggestions</h3>
<p>As always, comments and suggestions are appreciated.</p>
<p>Special thanks to Pierre for his feedback, which has directly resulted in this new release.</p>
