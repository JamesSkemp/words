+++
title = "Windows Server 2008 R2 Enterprise Edition - setup for sharing files"
summary = "With the File Server role in Windows Server 2008, it's relatively easy to share files with multiple machines."
draft = false
comments = true
date = "2010-06-06T10:00:00-05:00"
modified = "2010-06-06T10:11:13-05:00"
slug = "Windows-Server-2008-R2-Enterprise-Edition-setup-for-sharing-files"
blogengine = "7b34b8f0-5c06-4503-ba14-6b979604dabd"
categories = ["software", "tutorials / guides"]
tags = ["windows server 2008", "windows server 2008 r2"]
+++

<p>When I first started downloading files, almost a decade and a half ago, I would just download everything to one directory, using whatever name the file originally had when I was downloading it.</p>
<p>In the last couple of years I've been trying (despite Chrome's default method trying to push be back)&nbsp;to be much better about saving files, by creating a directory with the full name of the application - "Microsoft Web Platform Installer" - and then saving the file(s) into that directory.</p>
<p>However, I do lose track of how many previous versions I have of particular applications (I try to only have the current and one version back) and how much total I'm storing.</p>
<p>Since my server is setup for the Web and Subversion, it was time to look at the next step, which is storing files to it, so that I can access with my other machines.</p>
<p>Luckily Windows Server 2008 has a File Services role which allows the setup of shared folders over a network. The File Server role service is necessary, and based on what it seems to provide (not having worked with it before), File Server Resource Manager (FSRM) seemed to be a good bet as well.</p>
<p>Storage Monitoring gives another screen that allows for a volume to be monitored, and reports to be generated, but since at this point I want to monitor directories instead of volumes, I opted to skip past that by just pressing Next.</p>
<p>With that done I'm left with the question, especially (I think) since I'll probably put in a second hard drive in the next couple of months, whether I should create a Virtual Hard Drive (VHD) with the downloads stored to it. At this point I'm at about 40 GB of files, though, and I'm not sure it would really be a benefit. So while more research is needed into the benefits of VHD, I opted to just create a new directory in the root of C called downloads.</p>
<p>Now I want my PCs and laptop to be able to access this directory, as well as save files to it. I create a new user (Server Manager &gt; Configuration &gt; Local Users and Groups &gt; Users) that the three will all use to access the machine (and I'm okay with one account being shared over the three machines). Users cannot change the password <span style="text-decoration: line-through;">and it'll never expire</span>. With the account setup I share C:\downloads\ with the new account, giving it Read/Write permissions.</p>
<p>Since it was initially setup as being on a public network (just by default), I'm prompted on whether I want to turn on network discovery and file sharing for public networks, of if I'm connected to a private network (home/workplace). In my case it's definitely the latter. Even though network discovery continued to be turned off, I was still able to access the share using the user account I had setup (so long as I didn't try adding the domain to the end).</p>
<p>With that done I opened File Server Resource Manager and added a quota to C:\downloads\. The built-in templates didn't work for me, so I created one with a 50 GB soft limit, that generates an event log entry if the quota is reached, and generates&nbsp;reports for large files and least recently accessed files, when usage reaches the default of 85%.</p>
<p>And now it's just a matter of move files to the server.</p>
