+++
title = "iTunes Music to SQLite - version 0.1 beta released"
description = "iTunes Music to SQLite imports all 'Music' playlists in iTunes into a SQLite database."
draft = false
comments = true
date = "2009-09-24T12:13:00-05:00"
modified = "2009-09-24T12:27:51-05:00"
slug = "iTunes-Music-to-SQLite-version-01-beta-released"
blogengine = "930ca3b4-beb1-49fe-b082-d06c775d8075"
categories = ["software", "StrivingLife"]
tags = ["music", "itunes", ".net", "sqlite"]
+++

<p>While it was at the same stage as it is now back on the 19th, I'm finally releasing the beta version of iTunes Music to SQLite.</p>
<p>This console application finds all Music playlists in iTunes and imports them into a SQLite database (called iTunesMusic.s3db).</p>
<p>You can change this by passing the database and source names as parameters.</p>
<p>For example:</p>
<pre class="code"><code class="powershell">iTunesMusicToSQLite.exe "datum.db" "James Skemp's 80 gig"</code></pre>
<p>You can run the executable and it will prompt for a key press before exiting, in case you want to view any messages.</p>
<p>This is a beta version, and was done more as a proof of concept than anything else, so this may be the only version released.</p>
<p><a rel="download" href="http://jamesrskemp.com/applications/iTunesMusicToSQLite_0.1.zip">Download iTunes Music to SQLite 0.1</a>.</p>
<p>.NET Framework 3.5 is recommended, and may be required (<a rel="external" href="http://smallestdotnet.com/">check your version of .NET Framework</a>).</p>
