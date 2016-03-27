+++
title = "Steps to setting up a Windows Server 2003 Web Server on VirtualBox"
description = "Steps to setup a Windows Server 2003 instance running IIS, on VirtualBox."
draft = false
comments = true
date = "2009-10-24T15:45:00-05:00"
modified = "2009-10-24T15:51:16-05:00"
slug = "Steps-to-setting-up-a-Windows-Server-2003-Web-Server-on-VirtualBox"
blogengine = "5d476ac6-3a9e-40b9-bd36-7862ccf7bfd8"
categories = ["tutorials / guides"]
tags = ["windows server 2003", "microsoft", "windows", "web development"]
+++

<p>The following goes through the steps needed to setup&nbsp;Windows Server 2003, with Web server capabilities (IIS 6 in this instance), on a Sun VirtualBox virtual machine.</p>
<p>Why Windows Server 2003 when Server 2008 is out and available? Because a large number of hosts (mine included) haven't made the switch yet.</p>
<h3>Requirements</h3>
<ol>
<li><a rel="external" href="http://www.virtualbox.org/">Sun VirtualBox</a>. We want this in particular for the great networking functionality, but other apps, like Microsoft Virtual PC, will work fine as well. I used version 3.0.8 r53138 on Windows 7 Home Premium&nbsp;64-bit for this guide.</li>
<li>A copy of Windows Server 2003. In my case, I picked up a copy of <a rel="external" href="http://www.amazon.com/gp/product/B000WM3L3O?tag=strivinglifen-20">Visual Studio 2008 Professional with MSDN Professional</a>, which gives access to a large number of Windows Operating Systems and tools. Microsoft offers a number of <a rel="external" href="http://msdn.microsoft.com/en-us/subscriptions/subscriptionschart.aspx">subscription options</a>.</li>
<li>A computer that with a good amount of RAM and processor. The machine I used for this guide has 4 GB of RAM and a 2.20 GHz processor.</li>
</ol>
<h3>VirtualBox setup</h3>
<ol>
<li>Install VirtualBox, making sure that you install any network adapters VirtualBox may need.</li>
<li>Create a new virtual machine.<ol>
<li>Give the virtual machine a good name, such as <em>Windows Server 2003 - Web Server 1</em>.</li>
<li>Select Microsoft Windows - Windows 2003 as the operating system and version.</li>
<li>Feel free to bump up the base memory size, but if looking to mimic an external server, try to use it's specs. I typically stick to the default of 256 MB.</li>
<li>Create a new hard disk, of the type Dynamically expanding storage; this allows you to create a large disk, but only have it take up the space it needs.</li>
<li>Give the disk a good amount of space; I generally change from the default of 20 GB to 50 GB, since it's not easy to increase this later, but you'll typically never go above 10 GB anyway.</li>
</ol></li>
<li>Change the Network Adapter from the default of NAT to Bridged Adapter. This will allow you to reach both the Internet and your internal network.</li>
<li>With the machine setup, you'll want to verify that your Windows Server 2003 installation media is available. If using MSDN, that means adding your downloaded ISO to the Virtual Media Manager (FIle &gt; Virtual Media Manager)&nbsp;under CD/DVD Images.</li>
<li>Start the machine, attaching the ISO when prompted.<ol>
<li>Generally the defaults are acceptable.</li>
</ol></li>
</ol>
<h3>General Windows Server 2003 setup</h3>
<ol>
<li>Once Windows Server 2003 is installed, install the guest additions (Devices &gt; Install Guest Additions); it'll save you a deal of time.</li>
<li>Update Windows Server 2003 as needed.<ol>
<li>In particular, I like to download the <a rel="external" href="http://smallestdotnet.com/">current version of ASP.NET</a> and install IE 8 (although I do the latter as a separate update; I've had issues otherwise).</li>
</ol></li>
<li>At this point I like to exit out of the machine and clone the hard drive. I'll have activated the license and have a nice hard drive, with the current updates. If I want to create another Window Server 2003 instance, it's easier to just use a base drive and customize as needed. Your decision. (The VirtualBox (VBoxManage) command is clonehd.)</li>
</ol>
<h3>Specific Windows Server 2003 setups</h3>
<p>With a base install ready, we can go in various ways with our installation. By default, almost no services will be up and running.</p>
<p>In this particular instance, we just want to run IIS 6.</p>
<ol>
<li>Make sure you're in the Manage Your Server application. <a rel="external" href="http://media.jamesrskemp.com/graphics/windowsServer2003/server2003Roles_01.jpg">See this</a>.<ol>
<li>By default it will start automatically (a good thing) or you can find it at Start &gt; All Programs &gt; Administrative Tools &gt; Manage Your Server.</li>
</ol></li>
<li>From the options, select <strong>Add or remove a role</strong>.</li>
<li>We want a <strong>Custom configuration</strong>, since we just want a Web server.</li>
<li>For our needs, we want our&nbsp;server to be an&nbsp;<strong>Application server (IIS, ASP.NET)</strong>.</li>
<li>We only want to enable <strong>ASP.NET</strong>, not FrontPage Server Extensions (unless you particularly know you want that).</li>
<li>Our summary reads something like the following. <a rel="external" href="http://media.jamesrskemp.com/graphics/windowsServer2003/server2003Roles_02.jpg">See this</a>.<ol>
<li>Install Internet Information Services (IIS)</li>
<li>Enable COM+ for remote transactions</li>
<li>Enable Microsoft Distrubuted Transaction Coordinator (DTC) for remote access</li>
<li>Enable ASP.NET</li>
</ol></li>
<li>You may be prompted to insert a CD, at which point you'll want to mount CD 1 of the R2 discs, and not CD 2. You can play around with this as needed.</li>
<li>Shortly, you see that "This server is Now an Application server." Included on this page is a link to view additional steps to secure the server. <a rel="external" href="http://media.jamesrskemp.com/graphics/windowsServer2003/server2003Roles_03.jpg">See this</a>.</li>
<li>You should now see that the Application Server role is now available to be managed. <a rel="external" href="http://media.jamesrskemp.com/graphics/windowsServer2003/server2003Roles_04.jpg">See this</a>.</li>
<li>Opening a browser and calling <a rel="nofollow" href="http://localhost/">http://localhost/</a> should now display the standard Under Construction page.</li>
<li>Go to Windows Update and install any needed updates.</li>
<li>Assuming you've setup a Bridged Adapter in Network for the virtual machine, you should now be able to browse to the virtual instance in your host machine. You can use both the IP as well as the server name. For example, <a rel="nofollow" href="http://james-wins03ws1/">http://james-wins03ws1/</a>&nbsp;or <a rel="nofollow" href="http://192.168.1.106/">http://192.168.1.106/</a>.<ol>
<li>This can be found by opening a command prompt (cmd) and running <strong>ipconfig /all</strong> and finding the IP Address.</li>
</ol></li>
</ol>
<h3>Conclusion</h3>
<p>At this point you've successfully setup IIS running on Windows Server 2003, in a virtual machine, and are able to connect to it from your host machine.</p>
<p>You can now mimic a real machine as much as you'd like, for example by setting up FTP (<a rel="external" href="http://filezilla-project.org/">FileZilla Server</a>)&nbsp;to move files between the machines.</p>
<div class="note">
<p>I recommend just using VirtualBox to move files between the two; Devices &gt; Shared Folders will let you setup temporary and permanent folders.</p>
</div>
<p>Questions, comments, and suggestions are appreciated.</p>
