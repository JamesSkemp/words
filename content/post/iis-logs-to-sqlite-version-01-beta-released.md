+++
title = "IIS Logs to SQLite - version 0.1 beta released"
summary = "Built on Microsoft Log Parser, IIS Logs to SQLite aims to import IIS logs into SQLite databases."
draft = false
comments = true
date = "2009-09-24T11:46:00-05:00"
modified = "2009-09-24T11:58:29-05:00"
slug = "IIS-Logs-to-SQLite-version-01-beta-released"
blogengine = "f761068f-313a-4b2b-b413-355828af0caf"
categories = ["software", "StrivingLife"]
tags = [".net", "iis", "log parser", "sqlite"]
+++

<p>Unfortunately, Microsoft Log Parser is unable to convert logs into SQLite. To work around this limitation I've created <strong>IIS Logs to SQLite</strong>, which will parse IIS logs and import them into the SQLite database and table of your choice.</p>
<p>The first beta version of this application is now available.</p>
<p><a rel="download" href="http://jamesrskemp.com/applications/IISLogsToSQLite_0.1.zip">Download IIS Logs to SQLite version 0.1</a>.</p>
<p>This application requires the .NET Framework version 3.5 (<a rel="external" href="http://smallestdotnet.com/">check your version of .NET Framework</a>).</p>
<p>Note that for a larger amount of logs, memory usage can spike.</p>
<p>In a future version I may (read: will) allow the columns to be exported to be selected by the user, instead of the 'all' dump that I currently do.</p>
<p>There's some other interface cleanup items as well, and there's at least one known bug (using a custom log file or path that returns no matches).</p>
<p>This might be the direction I end up taking my Log Parser Plus application.</p>
<p>Plug: Read more about Microsoft Log Parser and find example queries at <a rel="external" href="http://logparserplus.com/">Log Parser Plus</a>.</p>
