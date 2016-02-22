+++
title = "Collection down after opening - resolution"
summary = "Sometimes Verity collections will show a Collection down after opening (10) error, when attempting to index. Here's a resolution. [slnet0514:e2cfa167-e350-498b-9dea-3927bfe6ec1e]"
draft = false
comments = true
date = "2008-06-16T13:55:00-05:00"
modified = "2009-12-20T18:04:14-06:00"
slug = "Verity-Collection-down-after-opening-resolution"
blogengine = "e2cfa167-e350-498b-9dea-3927bfe6ec1e"
categories = ["article", "software"]
tags = ["coldfusion"]
+++

<p>We've been running into an issue, off and on, with ColdFusion MX 7.0.2 having issues with Verity collections.</p>
<p>During one of our nightly jobs, two Verity collections are purged, through ColdFusion, and then re-built.&nbsp;</p>
<p>Sometimes this will bring the collection down, resulting in a message like the following.</p>
<blockquote>
<p>Collection down after opening (10)</p>
</blockquote>
<p>Using the mdvdk executable, you can get some information about the collection, and even bring it back up.</p>
<p>mdvdk can be found in the \verity\k2\_nti40\bin\ directory, within the ColdFusion root directory.</p>
<p>You can get information about the status of the collection through this:&nbsp;</p>
<pre class="code"><code class="powershell">mkvdk -collection &lt;path to collection&gt; -about</code></pre>
<p>You don't use the online option/switch, but rather the repair one to bring the collection back online.</p>
<pre class="code"><code class="powershell">mkvdk -collection &lt;path to collection&gt; -repair</code></pre>
<p>You should be able to reindex successfully.</p>
<p>I also changed the code to do a refresh, instead of a purge, since the former doesn't take the collection offline.</p>
<p>You can find additional options by using the following:</p>
<pre class="code"><code class="powershell">mkvdk -help</code></pre>
<p>&nbsp;</p>
