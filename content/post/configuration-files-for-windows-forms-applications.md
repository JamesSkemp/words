+++
title = "Configuration files for Windows Forms Applications"
description = "Using configuration files may be the preferred method, but if it is, why is it so difficult to find resources on how to do so? Here's what I did."
draft = false
comments = true
date = "2009-03-05T22:10:00-06:00"
modified = "2009-03-05T22:24:44-06:00"
slug = "Configuration-files-for-Windows-Forms-Applications"
blogengine = "86687a30-ef34-4b1a-be51-ddfddf549c71"
categories = ["article", "software"]
tags = ["c#", ".net"]
+++

<p>
Since I know I&#39;ll run across this again ... 
</p>
<p>
In my <a href="http://jamesrskemp.com/apps/iTunesPlaylists2Xml/">iTunes Playlists to Xml</a> application I wanted to allow users the ability to persist their name across sessions. The supported method seems to be using application configuration files; in my case, something like iTunesApplication.exe.config. However, try as I could, I just couldn&#39;t find anything solid on how to create the configuration file. 
</p>
<p>
First, I had to add a reference to &quot;System.configuration&quot; (in References). I&#39;m still baffled on why you sometimes need to add a reference, and other times you can just add it to the top of the code-behind file. 
</p>
<p>
Once that was done <strong>using System.Configuration;</strong> worked and I was able to use <strong>Configuration config = ConfigurationManager.OpenExeConfiguration(ConfigurationUserLevel.None);</strong>. 
</p>
<p>
Next an &quot;Application Configuration File&quot; needed to be added, called app.config, and an appSettings element added within. Adding add elements with key and value attributes was the final step. 
</p>
<p>
Now building the application resulted in an iTunesApplication.exe.config file being created, and my config checks working as expected. 
</p>

