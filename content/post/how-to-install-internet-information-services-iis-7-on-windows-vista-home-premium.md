+++
title = "How to install Internet Information Services (IIS) 7 on Windows Vista Home Premium"
description = "In this guide I'll be covering just how easy it is to setup the default installation of IIS 7 in Windows Vista Home Premium. [slnet0514:2040411a-63de-4dd6-a7f6-31af01e13a31]"
draft = false
comments = true
date = "2008-03-21T15:45:00-05:00"
modified = "2009-09-18T20:35:59-05:00"
slug = "How-to-install-Internet-Information-Services-IIS-7-on-Windows-Vista-Home-Premium"
blogengine = "2040411a-63de-4dd6-a7f6-31af01e13a31"
categories = ["Internet", "software", "tutorials / guides"]
tags = ["microsoft", "vista", "iis"]
+++

<div class="note">
<p>
This guide covers Windows Vista Home Premium SP1, and may differ for other versions. 
</p>
<p>
I&#39;ll also only be covering the basic, default, installation. A guide covering the addition of additional features, like .NET capabilities, may be released as well. 
</p>
</div>
<p>
While limited, Windows Vista Home Premium allows Internet Information Services (IIS) 7 to be installed with little fuss, using the Control Panel interface. 
</p>
<p>
First, select <strong>Start</strong> &gt; <strong>Control Panel</strong>. 
</p>
<p>
Next click on the <strong>Programs</strong> item, followed by <strong>Turn Windows features on or off</strong>. 
</p>
<p>
A Windows Features window will come up, which will allow you to change the status of certain applications. Included amongst these is an <strong>Internet Information Services</strong> item, which contains a number of sub-items. 
</p>
<p>
Microsoft recommends you select this item, Internet Information Services, to install IIS. This is the default installation, and contains a minimum set of features. A full listing of items is below. 
</p>
<ul>
	<li>...</li>
	<li>Internet Information Services 
	<ul>
		<li>Web Management Tools 
		<ul>
			<li>IIS 6 Management Compatibility 
			<ul>
				<li>IIS 6 Management Console</li>
				<li>IIS 6 Scripting Tools</li>
				<li>IIS 6 WMI Compatibility</li>
				<li>IIS Metabase and IIS 6 configuration compatiblity </li>
			</ul>
			</li>
			<li>IIS Management Console</li>
			<li>IIS Management Scripts and Tools</li>
			<li>IIS Management Service </li>
		</ul>
		</li>
		<li>World Wide Web Services 
		<ul>
			<li>Application Development Features 
			<ul>
				<li>.NET Extensibility</li>
				<li>ASP</li>
				<li>ASP.NET</li>
				<li>CGI</li>
				<li>ISAPI Extensions</li>
				<li>ISAPI Filters</li>
				<li>Server-Side Includes </li>
			</ul>
			</li>
			<li>Common Http Features 
			<ul>
				<li>Default Document</li>
				<li>Directory Browsing</li>
				<li>HTTP Errors</li>
				<li>HTTP Redirection</li>
				<li>Static Content </li>
			</ul>
			</li>
			<li>Health and Diagnostics 
			<ul>
				<li>Custom Logging</li>
				<li>HTTP Logging</li>
				<li>Logging Tools</li>
				<li>Request Monitor</li>
				<li>Tracing </li>
			</ul>
			</li>
			<li>Performance Features 
			<ul>
				<li>Http Compression Dynamic</li>
				<li>Static Content Compression </li>
			</ul>
			</li>
			<li>Security 
			<ul>
				<li>Basic Authentication</li>
				<li>IP Security</li>
				<li>Request Filtering</li>
				<li>URL Authorization </li>
			</ul>
			</li>
		</ul>
		</li>
	</ul>
	</li>
	<li>...</li>
</ul>
<p>
When you select the <strong>Internet Information Services</strong> item, the following items are automatically selected. 
</p>
<ul>
	<li>Internet Information Services 
	<ul>
		<li>Web Management Tools 
		<ul>
			<li>IIS Management Console</li>
		</ul>
		</li>
		<li>World Wide Web Services 
		<ul>
			<li>Application Development Features</li>
			<li>Common Http Features 
			<ul>
				<li>Default Document</li>
				<li>Directory Browsing</li>
				<li>HTTP Errors</li>
				<li>Static Content</li>
			</ul>
			</li>
			<li>Health and Diagnostics 
			<ul>
				<li>HTTP Logging</li>
				<li>Request Monitor</li>
			</ul>
			</li>
			<li>Performance Features 
			<ul>
				<li>Static Content Compression </li>
			</ul>
			</li>
			<li>Security 
			<ul>
				<li>Request Filtering</li>
			</ul>
			</li>
		</ul>
		</li>
	</ul>
	</li>
</ul>
<p>
By default, then, you&#39;ve got the ability to manage the server through the IIS Management Console. You can also serve, and compress, static content. 
</p>
<p>
If you apply these additions, you&#39;ll be able to browse to http://localhost/ <em>immediately</em> after installation. A w3wp.exe process should also display in Windows Task Manager, running under the NETWORK SERVICE user name, and with the description of IIS Worker Process. 
</p>
<p>
If you don&#39;t already have it, you&#39;ll probably want to add the System administrative tools item to your All Programs/Start menu(s). You can do this by right-clicking on an empty spot in the Start menu, selecting Properties, then Start Menu &gt; Customize... Near the bottom of the list you&#39;ll have an option for System administrative tools, which you can display in a number of places. 
</p>
<div class="note">
<p>
I&#39;ll be assuming you installed it on both the Start menu and All Programs menu. 
</p>
</div>
<p>
Once this has been added you&#39;ll find an IIS Manager option under Administrative Tools. 
</p>
<p>
If you&#39;re used to older versions of IIS, like IIS 6, it may take a bit to get used to the new interface. But, it&#39;s sure to be a rewarding experience. 
</p>
<p>
Comments/corrections/etcetera greatly appreciated. 
</p>

