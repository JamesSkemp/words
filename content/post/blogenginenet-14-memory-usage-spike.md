+++
title = "BlogEngine.NET 1.4 - Memory usage spike?"
description = "Is BlogEngine.NET starting to suffer from feature creep?"
draft = false
comments = true
date = "2008-07-06T15:25:00-05:00"
modified = "2008-07-09T20:29:07-05:00"
slug = "BlogEngineNET-14-Memory-usage-spike"
blogengine = "19797beb-05d1-408e-a6cb-087bd02a7577"
categories = ["review", "software"]
tags = ["blogengine.net"]
+++

<div class="note">
<p>
Update,&nbsp;July 9, 2008:&nbsp;This update is a little late, but ... Mads was able to determine what the issue was and has provided a fix. I&#39;ll be trying&nbsp;another update this week. 
</p>
</div>
<p>
I recently upgraded to BlogEngine.NET 1.4, from 1.3. 
</p>
<p>
While it was, overall, a smooth enough process, while trying to dig into the large memory usage spike, I ran into a number of issues. 
</p>
<p>
I&#39;ve written about <a href="/words/?tag=/blogengine.net">BlogEngine.NET</a> in the past, and overall I&#39;ve been very happy with it. 
</p>
<p>
However, upon startup, it seems 1.4 uses&nbsp;4 times the memory 1.3 did (that&#39;s around 130 MB total - with only one visitor). 
</p>
<p>
Huh? That&#39;s pretty scary. 
</p>
<p>
I&#39;m afraid that BlogEngine.NET has started to suffer from feature creep. I&#39;ve got my backup of 1.3.x, so if nothing else I can switch back to that if my application pool keeps restarting (which I&#39;m afraid I&#39;ll have to do). 
</p>
<p>
Granted, there&#39;s some really nice enhancements, but if I can expect such a large memory commitment, I&#39;ll have to downgrade, which means I&#39;ll have to think about switching ... 
</p>
<p>
And that&#39;s a really scary idea, because of incoming links ... 
</p>

