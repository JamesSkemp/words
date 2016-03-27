+++
title = "Windows 7 Home Premium changes for IIS 7.5 access of Users directories"
description = "Tweaks to allow IIS on Windows 7 Home Premium access to content within the Users directories."
draft = false
comments = true
date = "2010-08-28T23:07:00-05:00"
modified = "2010-08-28T23:23:16-05:00"
slug = "Windows-7-Home-Premium-changes-for-IIS-75-access-of-Users-directories"
blogengine = "a347df5a-de76-4753-9ded-62e3763a4204"
categories = ["tutorials / guides"]
tags = ["windows 7", "iis"]
+++

<p>Not feeling much like debugging it too much, I made a couple of modifications to my IIS installation to allow access to files contained within my user directory.</p>
<h3>Background</h3>
<p>I turned the Internet Information Services feature on on my Windows 7 Home Premium machine before using the Web Platform Installer to add additional functionality. However, I kept running into a permissions issue, as the sites I setup were located in my Users directory (C:\Users\James).</p>
<h3>Possible options</h3>
<p>A couple of possible options exist, including giving the user that the application pool runs as full access to the appropriate directory. However, to some extent this circumvents security on my laptop.</p>
<p>Another option is to use Windows authentication. To this end it needs to be enabled by checking the feature of Internet Information Services &gt; World Wide Web Services &gt; Security &gt; Basic Authentication.</p>
<h3>Additional setup and result</h3>
<p>Additionally default rights must be given to the local IIS_IUSRS group, so that it can access the Web.config file.</p>
<p>Now when I browse to the site I'm prompted for credentials, which is the same information I use to login to my machine.</p>
<p>Putting the content into a directory with the appropriate permissions (%SystemDrive%\inetpub\wwwroot)&nbsp;may be better, but this works just fine for the limited testing I need to perform.</p>
