+++
title = "Windows Server 2008 Standard Edition on Sun VirtualBox 2.2.4 - Notes"
description = "Notes on getting base installs ready of Windows Server 2008 Standard Edition, on VirtualBox 2.2.4."
draft = false
comments = true
date = "2009-06-27T16:21:00-05:00"
modified = "2009-10-24T14:17:40-05:00"
slug = "Windows-Server-2008-Standard-Edition-on-Sun-VirtualBox-224-Notes"
blogengine = "d9b520a5-6f52-484a-97c2-a9ea74fc55aa"
categories = ["technology"]
tags = ["microsoft", "windows server 2008", "virtualbox"]
+++

<p>As part of a test environment, I setup Windows Server 2008 Standard Edition, both the core and full installations,&nbsp;using Sun VirtualBox 2.2.4. Here are a couple of notes on the base installs.</p>
<p>With the core install, it's not immediately obvious, but you need to select Other User once the system is installed, and enter Administrator for the username, with no password. As soon as you log in, you'll be prompted to add&nbsp;a password.</p>
<p>This is different than the full install, which will immediately bring you to the password change screen, with Administrator already selected.</p>
<p>To shutdown the machine at the prompt, enter the following at the command line:</p>
<pre class="code"><code>Shutdown -s -t 0</code></pre>
<p>This shuts the machine down after 0 seconds. Enter -r instead of -s to do a reboot.</p>
<p>I haven't played with the core install beyond this.</p>
<p>The full install will immediately tell you, much like Server 2003, what you should do after installing. Run updates, select your timezone, etcetera.</p>
<p>No features or roles will be enabled, unless you update the .NET Framework (which will be recommended) and then you'll have .NET enabled afterwards.</p>
<p>Since I wanted to setup base installs, I decided to have Windows "Check for updates but let me choose whether to download and install them."</p>
<p>Additions installed fine on full install, but I didn't try on the core installation.</p>
