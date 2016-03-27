+++
title = "Upgrading to .NET 4 on an IIS site supporting a .NET 2.0 child application"
description = "Today I experienced some downtime as I tried updating one of my sites to .NET 4, while needing to keep the child application as .NET 2.0. Here's what I could have done in moments, instead of 30 minutes."
draft = false
comments = true
date = "2012-08-05T14:51:00-05:00"
modified = "2012-08-05T15:18:16-05:00"
slug = "Upgrading-to-NET-4-on-an-IIS-site-supporting-a-NET-20-child-application"
blogengine = "f35cc7d5-404f-4e4c-b6cf-8d9a0d823989"
categories = ["StrivingLife"]
tags = ["windows server 2008 r2"]
+++

<p>Today I decided to finally make progress on a couple pending applications. As part of that process I needed to upgrade one of my sites to .NET 4. Unfortunately it has a child application that needs to say as .NET 2.0/3.5. After approximately 30 minutes of downtime, I finally got things configured correctly (seemingly). Here's what I ended up having to do.</p>
<p>This assumes IIS 7.5.</p>
<ol>
<li>Wrap the system.web and system.webServer elements in the parent Web.config with the following:<br />
<pre class="code"><code class="xml">&lt;location path="." inheritInChildApplications="false" allowOverride="true"&gt;
...
&lt;/location&gt;</code></pre>
</li>
<li>If you have the following set in system.webServer, you'll want to <em>move</em> that outside of the location wrapper you added in step 1. Otherwise the site doesn't appear to capture that, and you'll 500.<br />
<pre class="code"><code class="xml">&lt;validation validateIntegratedModeConfiguration="false"/&gt;</code></pre>
</li>
<li>Change the application pool settings on the parent application to .NET Framework 4.0 and push the above change.</li>
</ol>
<p>That was the only change it appears I needed to make. Instead I made a number of minor changes, all over the place, which resulted in the downtime.</p>
<p>In my particular case I also had both the parent and child applications running on the same application pool. I ended up creating a new application pool for the child application, switched it over to that<span style="text-decoration: line-through;">, but neglected to set the identity as NETWORK SERVICE, which resulted in a few moments of questioning</span>. Actually, I correctly set this to the application pool identity, but had actually neglected to give the correct directories the new permissions (since I changed the applicaton pool).</p>
<p>Needless to say, I'll be very happy when I re-write the child application over to .NET 4.</p>
