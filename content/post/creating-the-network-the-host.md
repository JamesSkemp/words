+++
title = "Creating the network - the host"
description = ""
draft = false
comments = true
date = "2005-10-06T18:58:00-05:00"
slug = "Creating-the-network-the-host"
blogengine = "10e70a48-6879-49d6-8875-5c38e51cd2b5"
categories = ["software", "tutorials / guides"]
tags = []
+++

<p>
While in my last post I said host-singular, really there&#39;s two major &#39;hosts&#39;, in a manner of speaking. Usually, this will be the case. JamesRSkemp.net, for example, was one host. So, let&#39;s look at JamesRSkemp.net when it was one host.<!--more--><!--adsense-->
</p>
<p>
JamesRSkemp.net, as I said previously, was hosted with Tripod.Lycos. This means that both the files that were being served to users (hence, the server) as well as the domain name (the unique identifier that tells the servers where to pull the files) were hosted, or &#39;controlled&#39;, by one entity. In this case, Tripod.Lycos.
</p>
<p>
So, I paid Tripod.Lycos and got both space to store my files, software on the server that held the files, as well as the rights to a domain name for a particular amount of time (more about the specifics at some point in the future).
</p>
<p>
When I moved from this host (Tripod.Lycos, called a host since they are storing/hosting my files/content) I went to iPowerWeb, or sometimes simply iPower. I&#39;ll get into more about why I did, but we&#39;ll stick with the server space and domain name thread for the moment.
</p>
<p>
Like Tripod.Lycos, I was able to get both server space as well as a domain name - StrivingLife.net. However, since I also wanted another domain for Gavin&#39;s files - jamesrskemp.net/gavin, I bought another domain name through iPowerWeb - FramingBusiness.net. With this domain I pointed to a particular folder on my site (strivinglife.net/gavin/) that would be called up.
</p>
<p>
Again, the specifics can wait. The point is, we&#39;ve got server space and two domain names. In other words, two domain names can point to the same server space. This leads me to the other domain names. Instead of using iPowerWeb to register the other domain names I wanted, I used GoDaddy. GoDaddy was able to get me cheaper domain names. However, I did not have to purchase any kind of server space while I was purchasing the domain names.
</p>
<p>
To understand domain names, for those that don&#39;t really understand them, all you have to do is think of telephone numbers, such as for a business. A business can have a regular, local, number, as well as a toll-free number. While the numbers are different, they&#39;ll get you to the same company. So, technically, I didn&#39;t need to purchase the two domains with iPowerWeb. However, often times you&#39;ll get a free domain name as a perk.
</p>
<p>
Since iPowerWeb and GoDaddy are both providing services that allow users to read my content online, I consider both a part of the &#39;hosts&#39; issue.
</p>
<p>
But, iPowerWeb is providing server space. What exactly does that mean? Server&#39;s are basically computers, although built to server content, instead of run word processing software, and browse the Internet. With a more specific purpose, they are built much more powerfully, and able to handle many more connections at once.
</p>
<p>
But, servers don&#39;t just host files that are going to be served. They also require software that will serve the files. IIS and Apache are just two of the many core Web servers (here meant in the software, not the hardware sense). Server software requires an operating system, just like computers. Then, additional programs can be used to provide additional services.
</p>
<p>
For an example, let&#39;s take a look at what iPowerWeb is providing StrivingLife.net.
</p>
<p>
The hardware doesn&#39;t really concern me as much as it probably should. However, a quick glance at their product pages tells me that they use HP servers, and that&#39;s about it. Typically, an email to support or sales is all it takes to get this kind of information. Again, since I personally don&#39;t care all that much, I won&#39;t dig deeper.
</p>
<p>
What I&#39;m really concerned about is the software that they run. The software run on the server allows me, or does not allow me, to serve particular types of files. While every server can serve HTML files, not every server than serve PHP or ASP files. If these files are mumbo-jumbo, don&#39;t worry about it. To bring it closer to home, if you don&#39;t have Adobe Acrobat Reader, or a similar program, you can&#39;t open/read PDF files. If you don&#39;t have Microsoft Access, you can&#39;t open/read Access databases.
</p>
<p>
Looking at what iPowerWeb provides, under Software and scripts, it looks like they provide
</p>
<ul>
	<li><strong>CGI-BIN</strong></li>
	<li><strong>Perl</strong> Support</li>
	<li><strong>MySQL</strong></li>
	<li><strong>PHP</strong> Support</li>
	<li><strong>Server Sides Includes</strong></li>
	<li>Frontpage 2000/2002 Extension</li>
	<li>Web Site Statistics</li>
	<li>Web Site Backup Software</li>
	<li>Web Hosting Control Panel</li>
</ul>
<p>
I&#39;ve emphasized certain items. Basically, these programs allow more files to be served, in addition to HTML files.
</p>
<p>
If you continue looking, you&#39;ll see that they use Apache as a Web server. Again, something important to know. Why? Because setup of software is different, depending upon what you use. For example, installing programs on a Mac is going to give you different file locations than on a Windows machine, or a Linux machine.
</p>
<p>
With my particular host, since I&#39;m with them, I can tell you the following (and it&#39;s quite alright if none of this makes sense);
</p>
<ul>
	<li>the operating system they use is FreeBSD 4.11 Stable</li>
	<li>they run the Apache 1.3.31 (Unix) Web server</li>
	<li>they are running PHP 4.3.10</li>
	<li>they are running MySQL 3.23.49</li>
	<li>finally, they&#39;ve got perl, v5.8.3</li>
</ul>
<p>
These are really the core pieces of software. Tied onto that we have things like AWStats 6.4 (build 1.814) - which requires Perl. phpMyAdmin 2.6.3 is used for MySQL (again, the former requires the latter).
</p>
<p>
Then we have things that I can add to the server, as scripts. Briefly, scripts allow certain things to happen automatically, or when the script is used/run.
</p>
<p>
Things like WordPress 1.5.2, PunBB 1.2.7, BBClone 0.4.8a, and Gallery 1.5, are all installed by me, on the server, for use. Each installation requires that certain things be true. For example, all of these require PHP. Because I wanted to run PHP files, I needed a host that would allow me to do this.
</p>
<p>
But, that&#39;s a discussion for a latter time.
</p>
<p>
Speaking of which, I&#39;ve mentioned a number of times that things wouldn&#39;t be discussed here. Since I&#39;m only giving the background, expect that I&#39;ll be going into greater length about these things as time goes by. While my first concern will be discussing things that I&#39;m doing, as an admin to a number of sites, that doesn&#39;t mean I won&#39;t go off on tangents in posts or comments. So, comment away.
</p>
<p>
~Jk
</p>

