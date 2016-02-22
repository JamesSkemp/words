+++
title = "Ubuntu 7.04 - Server Edition installed"
summary = "Notes, mostly to myself, on installing Ubuntu 7.04 Server Edition."
draft = false
comments = true
date = "2007-06-26T19:13:00-05:00"
modified = "2007-07-22T18:05:36-05:00"
slug = "Ubuntu-704-Server-Edition-installed"
blogengine = "42749f31-e804-4168-9a85-3c4741c0c974"
categories = ["software", "tutorials / guides"]
tags = ["ubuntu"]
+++

<p>
Just about finished ...  Quite the process, but things seem to be running okay - now I just have to determine whether it was worth it ...<!--more-->
</p>
<p>
I&#39;m using a computer with a 40 GB hard drive and 512 MB of RAM.  So ...
</p>
<p>
#1 - primary - 1.2 GB - swap - swap<br />
#3 - primary - 22.3 GB - ext3 - /home<br />
#5 - logical - 15.0 GB - ext3 - /<br />
#6 - logical - 1.5 GB - fat32 - /mnt/shared
</p>
<p>
This was based upon my previous install, where I had the following:
</p>
<p>
/ = 6.7 GB, 59% was used<br />
/home = 9.3 GB, 5% used<br />
(swap was 1.2 GB?)
</p>
<p>
The other 20 GB was the Windows XP installation.<!--adsense-->
</p>
<p>
Getting it partitioned just right took a bit of time ...
</p>
<p>
Once the server installation was done, I decided to install ubuntu-desktop (yikes, that was almost an hour). What I should have done was install Lynx (see a little further below) so I could have at least browsed a bit while I was waiting ... but I had my Windows machine up, so I was able to get some work done while I was waiting.
</p>
<p>
sudo apt-get install ubuntu-desktop
</p>
<p>
Once that finally stopped, a reboot.
</p>
<p>
sudo reboot
</p>
<p>
Unfortunately, now the GUI is starting automatically.  After some research online ...
</p>
<p>
sudo apt-get sysv-rc-conf
</p>
<p>
sudo sysv-rc-conf
</p>
<p>
I unchecked the level 2 boxes for bluetooth and gdm.
</p>
<p>
Restart.
</p>
<p>
Now you&#39;ll have to login, but AMP will automatically be started (tested by checking another machine on my network).
</p>
<p>
sudo apt-get install lynx
</p>
<p>
sudo gdm start
</p>
<p>
... or ...
</p>
<p>
sudo /etc/init.d/gdm start
</p>
<div class="note">
<p>
And if you want to stop gdm (Ubuntu&#39;s default GUI) use this at a terminal:
</p>
<p class="code">
sudo /etc/init.d/gdm stop
</p>
<p>
If you do sudo gdm stop, then it keeps trying to restart, and it&#39;s dang annoying &hellip; (because it never stops in the first place)
</p>
</div>
<p>
Another login required ...
</p>
<p>
Then it&#39;s uninstalling the Games and installing <strong>gkrellm</strong>.
</p>
<p>
If I do this again, I&#39;ll definitely need to take a look at the minimal version of ubuntu-desktop ...
</p>
<p>
Now I&#39;ve got to reconfigure Firefox, <a href="http://strivinglife.net/wordpress/2007/06/18/374/configuring-apache-for-per-user-pages/">reconfigure Apache</a>, and <a href="http://strivinglife.net/wordpress/2007/06/15/373/quickie-install-coldfusion-702-on-ubuntu-704-with-apache-224/">reinstall ColdFusion</a>. I&#39;m debating PostgreSQL ...
</p>

