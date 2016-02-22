+++
title = "Second Web site ported over to ASP.NET MVC 2"
summary = "Thoughts on porting a second Web site over to ASP.NET MVC 2."
draft = false
comments = true
date = "2010-05-23T17:27:00-05:00"
modified = "2010-05-23T17:41:21-05:00"
slug = "Second-Web-site-ported-over-to-ASPNET-MVC-2"
blogengine = "246c7a9e-8bd9-4a08-b23f-8f55ff720131"
categories = ["StrivingLife"]
tags = ["asp.net mvc"]
+++

<p>After <a href="http://strivinglife.com/words/post/First-Web-site-ported-over-to-ASPNET-MVC-2.aspx">converting one Web site over to ASP.NET MVC 2 yesterday</a>, I ported my second one today.</p>
<p>The first Web site was originally just a bunch of static HTML pages, so it was fairly easy to move over. This one, <a rel="external" href="http://logparserplus.com/">LogParserPlus.com</a>, gets all of its data from a collection of XML files. Using LINQ to XML the files are read and parsed out to the page, using a Repeater control.</p>
<p>Unfortunately, when I was creating the site I had run into issues with that Repeater control not acting as I would have liked. Luckily, now that I've moved to ASP.NET MVC those issues have been eliminated.</p>
<p>While the addresses changed for every page save the home page (and the static content), the Web.config was more than able to handle these via some httpRedirect elements.</p>
<pre class="code"><code class="xml">&lt;configuration&gt;
	&lt;location path="LogParserExpressions.aspx"&gt;
		&lt;system.webServer&gt;
			&lt;httpRedirect enabled="true" destination="/Expressions" exactDestination="true" childOnly="true" httpResponseStatus="Permanent"/&gt;
		&lt;/system.webServer&gt;
	&lt;/location&gt;
&lt;/configuration&gt;</code></pre>
<p>Memory usage didn't jump as much as for the static site, but there was still an increase from approximately 14 K (with all pages visited) to a little under 29 K (again with all pages visited).</p>
<p>On the bright side, it's highly likely that I'll now add additional functionality to the site. However, I believe I'll need to tweak the data access classes a bit before I go too far down that path.</p>
<p>Overall, I'm happy to be able to move away from Web Forms for this site.</p>
