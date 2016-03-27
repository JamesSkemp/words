+++
title = "Windows Server 2008 R2 Enterprise Edition - setup for Web development"
description = "Steps taken to setup a fresh copy of Windows Server 2008 R2 Enterprise Edition to serve Web content via IIS."
draft = false
comments = true
date = "2010-06-05T20:20:00-05:00"
modified = "2010-06-05T21:24:56-05:00"
slug = "Windows-Server-2008-R2-Enterprise-Edition-setup-for-Web-development"
blogengine = "c2a76358-d90d-4697-84f9-a3900fb78bc0"
categories = ["software", "tutorials / guides"]
tags = ["windows server 2008", "windows server 2008 r2", "iis", "subversion"]
+++

<p>This afternoon I setup a machine for the following purposes:</p>
<ol>
<li>to serve as a test bed for Web development</li>
<li>to serve as an always-available Subversion repository server</li>
<li>to serve as a repository for shared downloads, across all my machines</li>
</ol>
<p>As time goes by the scope of the server may also change. But for now, this will work just fine.</p>
<h3>Choosing an edition</h3>
<p>The first step was to install Windows Server 2008 R2. Being able to choose between any of the editions, it was between Enterprise, Standard, and Web. While I began to lean towards Web based upon the <a rel="external" href="http://www.microsoft.com/windowsserver2008/en/us/r2-compare-specs.aspx">edition comparison by technical specification</a>, when I looked at <a rel="external" href="http://www.microsoft.com/windowsserver2008/en/us/r2-compare-roles.aspx">edition comparison by server role</a>, Web&nbsp;dropped out of the race. Since my external host provides an Enterprise edition server, Enterprise is what I finally chose.</p>
<h3>Initial setup before&nbsp;disconnecting the (physical) monitor</h3>
<p>After a short time, Windows Server 2008 R2 Enterprise edition was installed and ready for configuration, after entering an Administrator password.</p>
<p>The first thing I did was activate Windows, correct the time zone, and change the computer name to something a bit more manageable, which required a restart.</p>
<p>The&nbsp;next step was to configure (checking for updates,&nbsp;but not installing them automatically)&nbsp;and&nbsp;install updates, of which there were 30.</p>
<p>Since&nbsp;I want to ultimately remove the monitor from this change, I enabled remote desktop. Since I've only got the one network connection, I didn't need to tweak it any further.</p>
<p>While I was in System Properties and switched over to the Advanced tab and hit the Settings... button under Performance. I don't care about how it looks, so I switched from "Let Windows choose what's best for my computer" to "Adjust for best performance," which just unchecked all the checkboxes. I now tested connecting in from my Windows 7 Home Premium machine, and sure enough I was able to&nbsp;bump my other machine and remote in.</p>
<p>With that tested, it was time to shut off the machine, unplug the monitor and USB keyboard and mouse, and see if I could remote in.</p>
<h3>Success means shutting off services</h3>
<p>With the machine correctly booting up, even though it had no monitor, keyboard, nor mouse hooked up, it was time to start optimizing the server by shutting off services.</p>
<p>Print Spooler was the first to be stopped and disabled. And that was about it. At only 470 MB used, that's not too shabby.</p>
<h3>Adding server roles - Web server</h3>
<p>With Print Spooler disabled it was time to start setting up server roles. I want to start simple, I first selected Web Server (IIS). While I've run through this before, this time I actually read the notes and saw an item about Windows System Resource Manager (WSRM) that "can help ensure equitable servicing of Web server traffice, especially when there are multiple roles on this computer." That sounds like what I'll eventually be doing, so I've made a note to look into this later.</p>
<p>By default a number of role services are selected, and since I know I want to do ASP.NET development, I added that (and the&nbsp;items it requires)&nbsp;and HTTP Redirection, since it's come up before. I end up with the following.</p>
<ul>
<li><strong>Web Server (IIS)</strong> 
<ul>
<li><strong>Web Server</strong> 
<ul>
<li>Common HTTP Features 
<ul>
<li>Static Content</li>
<li>Default Document</li>
<li>Directory Browsing</li>
<li>HTTP Errors</li>
<li>HTTP Redirection</li>
</ul>
</li>
<li>Application Development 
<ul>
<li>ASP.NET</li>
<li>.NET Extensibility</li>
<li>ISAPI Extensions</li>
<li>ISAPI Filters</li>
</ul>
</li>
<li>Health and Diagnostics 
<ul>
<li>HTTP Logging</li>
<li>Request Monitor</li>
</ul>
</li>
<li>Security 
<ul>
<li>Request Filtering</li>
</ul>
</li>
<li>Performance 
<ul>
<li>Static Content Compression</li>
</ul>
</li>
</ul>
</li>
<li><strong>Management Tools</strong> 
<ul>
<li>IIS Management Console</li>
</ul>
</li>
</ul>
</li>
</ul>
<p>Once the installation was finished successfully (without the need of a reboot), I was successfully able to browse to the site on my Windows 7 machine.</p>
<h3>The 'easy button'</h3>
<p>With that done, it was time to install <a rel="external" href="http://www.microsoft.com/web/downloads/platform.aspx">Microsoft Web Platform Installer</a>&nbsp;(WPI), also know as <a href="http://strivinglife.com/words/post/Microsoft-Web-Platform-Installer-is-the-easy-button.aspx">the easy button</a>. Since Internet Explorer runs in a high-security mode in Server 2008, I had to download a copy on my Windows 7 machine and copy and paste it over to the Server, via Remote Desktop.</p>
<p>Since Server 2008 R2 doesn't come with .NET Frameworks&nbsp;3.5 SP 1 or 4 installed, I started with 3.5 SP1. For whatever reason Logging Tools was also selected, but seemingly no download was required.</p>
<p>Surprisingly I didn't have to reboot after installing .NET 3.5 SP1, so I went on to version 4. For whatever reason, this install took a good deal of time (in the&nbsp;double-digits), and since I didn't keep my attention solely on it, missed the restart prompt in the bottom right corner. But, after the restart that was too was finished.</p>
<p>URL Rewrite 2.0, ASP.NET MVC 2, and PHP 5.2.13 were all next (which ended up requiring CGI to be installed as well).</p>
<p>While tempted to install SQL Server Express, I opted to hold off, since I can install something&nbsp;a bit higher-end, depending upon how they compare for what I need.</p>
<h3>CollabNet Subversion Server</h3>
<p>As I've been doing more and more, I opted to use CollabNet Subversion Server to install Apache and Subversion, which means another copy and paste through Remote Desktop.</p>
<p>The installation steps haven't changed, so I used <a href="http://strivinglife.com/words/post/Installing-CollabNet-Subversion-Sever-163-and-TortoiseSVN-163-on-Windows-Server-2003.aspx">an older installation guide I had written</a>, turned off update notifications, and restart the server.</p>
<p>As I've grown to expect, once the server was restarted I was able to access port 8080 locally, but not on my own machine, due to firewall settings. After allowing C:\Program Files (x86)\CollabNet\Subversion Server\httpd\bin\httpd.exe (Apache HTTP Server) to communicate through Windows Firewall, that was now working.</p>
<p>Since I install PHP in a previous step I could go ahead and allow Apache to use it, but for now I'm going to keep moving forward and setup my existing (used) repositories.</p>
<h3>Subversion security and repositories</h3>
<p>Since I've only got one hard drive (at the moment) on the server, in the C drive root I created a new svn_resources directory. Opening cmd and moving to C:\Program Files (x86)\CollabNet\Subversion Server\httpd\bin\ we can access the htpasswd.exe executable. Using the 'official' book as the standard, I entered the following to create an account for my main development machine (an HP Pavilion a6360t).</p>
<pre class="code"><code class="powershell">htpasswd.exe -cm c:\svn_resources\svn-auth-file james-a6360t</code></pre>
<p>After entering my password twice, I now had an authentication file, and I can now add security to my repositories, via updating&nbsp;C:\Program Files (x86)\CollabNet\Subversion Server\httpd\conf\httpd.conf (you may also want to start Apache Monitor and restart the instance).</p>
<pre class="code"><code class="xml">&lt;Location /svn&gt;
	DAV svn
	SVNParentPath C:\svn_repository
	AuthType Basic
	AuthName "Subversion repository"
	AuthUserFile C:\svn_resources\svn-auth-file
	Require valid-user
&lt;/Location&gt;</code></pre>
<p>I setup my laptop with another account, and with that done it's time to start <a href="http://strivinglife.com/words/post/Subversion-and-TortoiseSVN-Moving-a-repository.aspx">moving over the repositories</a>. Since I have so many, I focused on just the handful that I'm actively working on, and holding off on the rest.</p>
<p>Whew.</p>
<h3>Next steps</h3>
<p>In addition to looking into WSRM, I still need to move my downloads over to the server (which possibly means setting this up with a file server role), adding SQL Server, and possibly adding PHP functionality to Apache ... just in case.</p>
