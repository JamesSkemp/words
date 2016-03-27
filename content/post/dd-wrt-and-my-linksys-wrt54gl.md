+++
title = "DD-WRT and my Linksys WRT54GL"
description = "I tried updating my WRT54GL to DD-WRT. Can you guess what happened?"
draft = false
comments = true
date = "2011-04-23T17:24:00-05:00"
modified = "2011-04-23T17:40:44-05:00"
slug = "DD-WRT-and-my-Linksys-WRT54GL"
blogengine = "5846dba9-0435-4c5b-8143-d142ec908efa"
categories = ["software"]
tags = ["cisco", "wrt54gl", "dd-wrt"]
+++

<p>I've been sitting on a <a rel="external" href="http://www.amazon.com/gp/product/B000BTL0OA?tag=strivinglifen-20">Linksys (Cisco) WRT54GL</a> for a long while now. A long, long, while.</p>
<p>Originally I was going to replace my <a rel="external" href="http://www.amazon.com/gp/product/B00007KDVI?tag=strivinglifen-20">WRT54G</a>&nbsp;(don't get me wrong, it still works great) and install DD-WRT for the additional features. However, I just never got around to it.&nbsp;Today I finally dusted off the box (I had opened it) and started getting it setup.</p>
<p>Interestingly, the deeper I dug into DD-WRT the more confused I became. The main Web site contains a database of routers, with information on which firmware to install, but if you dig into the forums you'll find that the database, and the firmware, are out-of-date and buggy.</p>
<p>Luckily, although not too surprisingly, there's <a rel="external" href="http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54GL">a Wiki on the Linksys WRT54GL</a>, which made installation pretty dang simple.</p>
<p>I basically:</p>
<ul>
<li>plugged the router into my laptop via a wired connection,</li>
<li>disconnected from my existing wireless-enabled router,</li>
<li>verified I could access the router with the stock firmware</li>
<li>did a hard reset on the router (30-30-30)</li>
<li>installed the new firmware</li>
<li>had to manually change the password (it didn't prompt me)</li>
<li>was set, since I decided to stick with the 'micro' (called such because of how large it is) install</li>
</ul>
<p>The hardest part was then replicating my existing settings on the new router, although that wasn't terrible since I was able to just connect to both from my laptop and iPad. I didn't put in my custom DNS lookups (I'm not using Charter), so that caused some issues, although even after adding those didn't work, a power cycle of my <a rel="external" href="http://www.amazon.com/gp/product/B00005T6GZ?tag=strivinglifen-20">cable modem</a> did.</p>
<p>All-in-all, it was <em>much</em>&nbsp;easier than I thought it was going to be, and, best of all, I don't have a bricked router.</p>
<p>According to inSSIDer, I already seem to have a better signal, so that's a good sign. I don't see myself investing too much time in additional settings, but ... it's there if I want to play around.</p>
<p>Oh, and if you're gotten this far, it's been a few months more than 2 years since I picked up the WRT54GL. Whoops.</p>
