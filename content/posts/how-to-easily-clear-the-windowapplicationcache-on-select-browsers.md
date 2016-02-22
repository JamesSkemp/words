+++
title = "How to easily clear the window.applicationCache on select browsers"
summary = "How to 'easily' clear application cache (cache manifest) data for Chrome, and Safari on i-devices."
draft = false
comments = true
date = "2011-04-02T19:45:00-05:00"
modified = "2011-04-02T20:01:47-05:00"
slug = "How-to-easily-clear-the-windowapplicationCache-on-select-browsers"
blogengine = "5fb6e436-bb3c-4b3e-9d77-a1c6c69e35a9"
categories = ["software", "tutorials / guides"]
tags = ["html", "safari", "chrome"]
+++

<p>While I was working on tweaking my video game listing, and creating my offline Web application manager, I kept running into issues with the cache manifest holding onto data much longer than I would have liked.</p>
<p>After some research I found that Chrome's interface can easily be found by going to&nbsp;<a rel="external nofollow" href="chrome://appcache-internals/">chrome://appcache-internals/</a>.</p>
<p>On Safari, on the iPod Touch and iPad, you can stop/close Safari (hold down the home button on the home screen, and close the application) and then start it back up to clear the data. This is slightly unfortunate, since it would be nice if this would stick around after the application is closed, but is sufficient. It also isn't very obvious, as I spent a good deal of time trying to figure this out before I tried this as a last-ditch effort.</p>
