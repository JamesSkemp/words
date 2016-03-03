+++
title = "Enabling ADB on a Lenovo A7600-F TAB A10"
summary = "How to enable ADB on a Lenovo A7600-F TAB A10, even though they haven't released official drivers yet."
draft = false
comments = false
date = "2014-11-06T12:59:46-06:00"
slug = "Enabling-ADB-on-a-Lenovo-A7600-F-TAB-A10"
blogengine = ""
categories = ["tutorials / guides"]
tags = ["android", "lenovo a7600-f tab a10", "adb"]
+++

<p>As of this post, Lenovo does not have an ADB Interface Driver for their Lenovo A7600-F TAB A10. However, since I'd like to develop on it, I had to find a solution.</p>

<p>An initial forum post pointed me to the older <a href="http://support.lenovo.com/us/en/downloads/ds022366" rel="external">ADB Interface Driver for their ThinkPad Tablet</a>. However, trying to update the android_winusb.inf with the necessary information was throwing a signature error when I tried to install it on Windows 8.1.</p>

<p>Luckily StackOverflow had <a href="http://stackoverflow.com/a/15609366/11912" rel="external">an answer to the question "Google Android USB Driver and ADB"</a> that stepped through how to make this work.</p>

<p>The specific steps I followed for the Lenovo A7600-F TAB A10 were:</p>

<ol>
<li>Downloaded the <a href="http://support.lenovo.com/us/en/downloads/ds022366" rel="external">ThinkPad Tablet ADB Interface Driver</a>.</li>
<li>Extract the contents of the zip to a new directory.</li>
<li>Update the <code>android_winusb.inf</code> file with the code below, which is also available as a <a href="https://gist.github.com/JamesSkemp/a1da366d597664ea3c91" rel="external">Gist</a>. This was added above the <code>;NVIDIA Tegra</code> line.</li>
<li>This may not be necessary, but I also updated the file at <code>C:\Program Files (x86)\Android\sdk\extras\google\usb_driver\android_winusb.inf</code> with the same code. I added it above the <code>;Project Tango (generic)</code> line.</li>
<li>Run <code>cmd</code> and then use <code>shutdown -o -r -t 0</code> to reboot. I unfortunately didn't keep track of the exact steps, but it's close to what the SO answer had, so something like "Click ‘Troubleshoot’. Click ‘Advanced Options’ Click ‘Windows Startup Settings’ Click Restart."</li>
<li>When you have the option, "Disable driver signature enforcement," which I believe was option 7 in the menu.</li>
<li>Once you've logged back into your machine you should be able to go into Device Manager, find the Lenovo tablet, and choose to update the device drivers. Point to the extracted zip directory. You might get a security warning, but you'll be able to install it.</li>
<li>Run <code>cmd</code> and navigate over to where adb is installed. In my particular case I'm using Android Studio, and upgraded to 0.8.14, so mine is in <code>C:\Program Files (x86)\Android\sdk\platform-tools</code>.</li>
<li><a href="https://gist.github.com/JamesSkemp/a56534e22e4c25a3ef0d" rel="external">Restart ADB</a> and then check the devices. This is done by running <code>adb kill-server</code> and <code>adb start-server</code> to restart ADB, and then <code>adb devices</code> to get a device listing.</li>
<li>I found that I had to unplug the USB cable from my computer first. You'll also have to accept the connection from the tablet.</li>
<li>Checking Device Manager should display "Lenovo ThinkPad Tablet ADB Interface" under Android Phone, and "A7600-F" under Portable Devices. You should also be able to run Android applications on the Lenovo A7600-F.</li>
</ol>

<script src="https://gist.github.com/JamesSkemp/a1da366d597664ea3c91.js"></script>

<script src="https://gist.github.com/JamesSkemp/a56534e22e4c25a3ef0d.js"></script>
