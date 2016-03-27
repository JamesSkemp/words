+++
title = "BlogEngine.NET 1.6 released"
description = "BlogEngine.NET 1.6 is available for download. Too bad the memory footprint increased again."
draft = false
comments = true
date = "2010-02-10T08:32:00-06:00"
modified = "2010-02-10T08:39:51-06:00"
slug = "BlogEngineNET-16-released"
blogengine = "9c1097b4-99ee-41b2-95fb-3391a651eaea"
categories = ["software"]
tags = ["blogengine.net"]
+++

<p>Promising a real comment moderation system, BE.NET 1.6 was released a few days ago.</p>
<p>Having just upgraded from 1.5.0.7, I wasn't without my issues, but overall the memory footprint doesn't seem too horrible (it's increased a bit again, but ...)</p>
<p>Actually, the memory footprint isn't a minor issue. I have 805 posts with 688 comments, and get between 9 to 10 thousand visits a month. BlogEngine.NET starts at around 150 MB of RAM and jumps up to 210 MB. It's not horrid, but I remember the days when it was nice and lean.</p>
<p>At one point Mads suggested he was going to switch over to IIS 7; maybe we'll see .NET 3.5 functionality first, which might tighten things up. Otherwise it may just mean I need to do a custom build ... or scrap it altogether for a lean system. I don't want to, but ...</p>
