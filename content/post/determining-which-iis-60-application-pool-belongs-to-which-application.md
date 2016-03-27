+++
title = "Determining which IIS 6.0 Application Pool belongs to which application"
description = "How to match an Application Pool to a process in Windows Server 2003 and IIS 6.0."
draft = false
comments = true
date = "2007-10-06T22:07:00-05:00"
modified = "2007-10-06T22:28:30-05:00"
slug = "Determining-which-IIS-60-Application-Pool-belongs-to-which-application"
blogengine = "840351af-5e33-48b1-8498-86f2ebff81f9"
categories = ["article", "software", "tutorials / guides"]
tags = ["iis", "windows"]
+++

<p>
In IIS 6.0, you can setup Application Pools for each of your sites. My knowledge of the exact benefits of this is somewhat lacking, but what I do understand is that these help applications (Web sites) stay within their own bounds, and prevent them from having a bad effect upon each other. 
</p>
<p>
For example, if one application is preforming poorly, as long as it&#39;s not a server-wide issue, the other sites on the server will be impacted minimally. 
</p>
<h3>Matching an Application Pool to a process</h3>
<p>
If you check the Windows Task Manager, and verify that you&#39;re looking showing processes from all users, you&#39;ll see&nbsp;one w3wp.exe for each running process, along with Memory Usage.&nbsp; PID (Process ID) isn&#39;t shown by default, but once you add that, you&#39;re on your way to discovering which process belongs to which Application Pool. 
</p>
<p>
Select Start &gt; Run ... and enter <strong>cmd</strong>. From the command line, if you&#39;re not in the <em>systemroot</em>\system32 directory, cd to it. For example, <strong>cd c:\windows\system32</strong>. 
</p>
<p>
Now, either enter iisapp.vbs or cscript iisapp.vbs to display the running Application Pools, along with a Process ID and the ID of the Pool. 
</p>
<h3>Next steps</h3>
<p>
Once you can match an Application Pool with a process, you can see just how much memory is being used. If you find that an application is using a deal of memory, then that may mean that you need to Recyle the Pool more regularly. You may also need to look at the code you&#39;re running to see if you have instances of leaks.
</p>
<p>
From my, albeit limited, experience, w3wp.exe starts with about 8 MB of memory usage, after a Recycle. However, how fast it climbs is up to the individual usage of the Application Pool.
</p>
<p>
Remember to check into your Performance logs, or enable logging for a set amount of time, to see if memory usage is getting too high too fast. For most business applications, there is generally a slow period, or two, where you can have the Application Pool Recycle. Of course, there&#39;s no real reason to Recycle too often, if you don&#39;t need it. 
</p>
<p>
There&#39;s an article on TechRepublic from Brien M. Posey (MCSE) with more information about Application Pools: <em><a rel="nofollow" href="http://articles.techrepublic.com.com/5100-6345_11-5170149.html" target="_blank">SolutionBase: Stabilize Web servers by using application pools</a></em>. 
</p>

