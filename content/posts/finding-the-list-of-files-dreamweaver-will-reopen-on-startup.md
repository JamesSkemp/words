+++
title = "Finding the list of files Dreamweaver will reopen on startup"
summary = "Want to make note of the files you had open in Dreamweaver? The listing of files is stored in the registry, depending upon your version."
draft = false
comments = true
date = "2009-08-19T20:00:00-05:00"
modified = "2009-08-26T22:05:35-05:00"
slug = "Finding-the-list-of-files-Dreamweaver-will-reopen-on-startup"
blogengine = "c608ab81-af7b-4951-a1ec-d1236ce36397"
categories = ["software"]
tags = ["dreamweaver"]
+++

<p>As sometimes happens, a network share ended up going down while I was using Dreamweaver. Unfortunately, this can cause fairly major issues with Dreamweaver, if you have files still open, or if you have Dreamweaver closed, but need to open it up.</p>
<p>Since I typically have more than one file open in Dreamweaver, and have set my preferences to remember what I've got open, I wanted to know where Dreamweaver stored the files that it was going to re-open.</p>
<p>This setting isn't stored in the file system, but rather is stored in the registry.</p>
<p>In Dreamweaver 8 the setting is under Edit &gt; Preferences &gt; General &gt; Reopen documents on startup.</p>
<p>The files that were open are stored in HKEY_CURRENT_USER\Software\Macromedia\Dreamweaver 8\Open Files</p>
<p>In Dreamweaver CS4 the registry setting is HKEY_CURRENT_USER\Software\Adobe\Dreamweaver CS4\Open Files</p>
<p>Note that if Dreamweaver crashes, Open Files may not be set. This is also updated when the program closes, not while it's running.</p>
<p>On Dreamweaver 8 Open Files is deleted, until the program closes, while CS4 seems to keep it available for longer.</p>
