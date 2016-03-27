+++
title = "Cassini 3.5.0.2 - built and ready to go"
description = "Want to run ASP.NET Web applications on your computer, without IIS? Here's a compiled version of Cassini to get you on your way."
draft = false
comments = true
date = "2010-01-03T18:10:00-06:00"
modified = "2010-01-03T18:13:39-06:00"
slug = "Cassini-3502-built-and-ready-to-go"
blogengine = "293d47c4-b9e8-4b42-94d0-bdab8472ebce"
categories = ["software"]
tags = ["cassini", "iis"]
+++

<p>Cassini is the product of Dimitry Robsman, and allows ASP.NET applications to be run without&nbsp;a full-fledged instance of IIS.</p>
<p>While Cassini should not be used in production environments, it's more than enough to run for minor development, or even minor projects.</p>
<p>The last official version of Cassini at the time of this writing&nbsp;is <a rel="external" href="http://blogs.msdn.com/dmitryr/archive/2009/04/23/cassini-support-for-friendly-urls-routing.aspx">3.5.0.2</a>. Since he's released the source, you can build your own, but what if you just want to download a pre-built version? Well now you can.</p>
<p><a rel="external download" href="http://jamesrskemp.com/applications/Cassini_3.5.0.2.zip">Download Cassini 3.5.0.2</a>.</p>
<p>While tempted, I've made no modifications. I have included a simple batch file (_startCassini.bat) however that allows you to copy this and the Cassini executable to a directory, and start Cassini from that directory. This also allows you to distribute your projects to others to run in a test environment. (I believe ELMAH uses something like this, but I kept, and keep,&nbsp;neglecting to look at how he implemented it.)</p>
<p>The batch file is simply the following:</p>
<pre class="code"><code class="powershell">Cassini-v35.exe "%cd%"</code></pre>
<p>Cassini does support additional arguments, which is documented in the ReadMe.txt. The MS-PL license is also included in the zip.</p>
<p>You may also be interested in <a rel="external" href="http://cassinipp.codeplex.com/">Cassini++</a> (I haven't looked into this project) and you'll want to have the current version of the <a rel="external" href="http://smallestdotnet.com/">.NET Framework</a> installed.</p>
