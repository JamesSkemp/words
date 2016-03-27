+++
title = "Initial thoughts on moving Firefox settings from Windows to Ubuntu"
description = ""
draft = false
comments = true
date = "2007-05-30T17:30:00-05:00"
modified = "2007-07-22T19:31:24-05:00"
slug = "Initial-thoughts-on-moving-Firefox-settings-from-Windows-to-Ubuntu"
blogengine = "fec2f9ce-13e1-4065-87fa-51e5515bd0bc"
categories = ["software"]
tags = ["firefox", "ubuntu"]
+++

<p>
This past Friday, I installed Ubuntu 6.06, upgraded it to 6.10, upgraded it to 7.04. I didn&#39;t have too much time to actually use it this weekend, but I&#39;m beginning to, attempting to move towards using it almost exclusively for day-to-day stuff.<!--more-->
</p>
<p>
The most used software? Firefox, of course.
</p>
<p>
I&#39;ve been using FEBE for a while to backup my profile, so it was time to give it a try actually doing a restore.
</p>
<p>
While I followed the necessary instructions to create a new profile, namely starting the profile manager (cd ~/.mozilla/firefox followed by firefox -ProfileManager) and creating a new profile, the actual restore didn&#39;t work too well.
</p>
<p>
So, I switched back to Windows, backed up everything individually (not the entire profile, as I was doing) and then began restoring my usernames and passwords.
</p>
<p>
Which didn&#39;t work.
</p>
<p>
So, I manually replaced the necessary files. Not wanting to try it again, I did the same for the cookies file.
</p>
<p>
The problem seems to stem from the fact that the directory structure has changed, and a number of my extensions appear to use the directory structure to function.
</p>
<p>
Now I just need to figure out how to remove the extra kernels when I initially boot up (I&#39;ve still got Windows XP Pro installed on a partition).
</p>

