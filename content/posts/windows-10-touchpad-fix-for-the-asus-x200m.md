+++
title = "Windows 10 touchpad fix for the ASUS X200M"
summary = "One possible way to fix an unresponsive touchpad on the ASUS X200M after a Windows 10 install."
draft = false
comments = true
date = "2015-08-07T22:21:19-05:00"
modified = "2015-08-25T19:16:52-05:00"
slug = "Windows-10-touchpad-fix-for-the-Asus-X200M"
blogengine = ""
categories = ["technology"]
tags = ["asus", "windows 10"]
+++

<p>I recently decided to upgrade my ASUS X200M, after successfully upgrading my mom's. Unfortunately, after upgrading my machine I ran into an issue where the touchpad was completely unresponsive, and I was forced to either use the touchscreen or a USB mouse.</p>

<p>After a bit of looking around I found <a href="http://www.cnet.com/forums/post/48428cdd-d8a9-4ef4-8bed-c70357f55fec/">a post on CNET's forums</a> that detailed a way to fix unresponsive touchpads in Windows 10. While the original question was about an Asus Transformer T100, this also worked for the X200M.</p>

<p>The steps are replicated below, since I trust my site to be up longer than CNET's forums.</p>

<blockquote>
  <p>Go to</p>

  <ol>
  <li>Start (Windows Button)</li>
  <li>Settings</li>
  <li>Devices</li>
  <li>Mouse &amp; Touchpad</li>
  <li>Scroll down to Related Settings and click "Additional mouse options"</li>
  <li>When the mouse properties window pops up, click on the ELAN tab</li>
  <li>Click your device and click "Enable".</li>
  </ol>
</blockquote>

<p>With these steps done my touchpad was once again responsive.</p>

<p>If you can't click, you may have to <a href="http://support.asus.com/Download.aspx?SLanguage=en&m=Smart+Gesture">download Smart Gesture for Windows 10</a> from the ASUS web site.</p>

<p>It appears that because I had an external mouse plugged into a USB port it was determining that it didn't need the touchpad to be on. While this sounds nice, I generally find myself keeping the USB receiver always plugged in, so in practice it's not ideal.</p>
