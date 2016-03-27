+++
title = "Windows Phone 7: Taking and restoring a SQL database"
description = "As I develop my first Windows Phone 7 application, My Video Game Tracker, I want to make sure that the many games I've added won't accidentally be lost (as I'm deploying test versions to my physical phone)."
draft = false
comments = true
date = "2012-04-22T16:08:00-05:00"
modified = "2012-04-22T16:35:23-05:00"
slug = "Windows-Phone-7-Taking-and-restoring-a-SQL-database"
blogengine = "e6d5c53d-9aeb-4d10-9ba8-e7c398216630"
categories = ["technology", "tutorials / guides"]
tags = ["windows phone 7"]
+++

<p>As I develop my first Windows Phone 7 application, <a rel="external" href="http://jamesrskemp.com/Projects/MyVideoGameTracker">My Video Game Tracker</a>, I want to make sure that the many games I've added won't accidentally be lost (as I'm deploying test versions to my physical phone).</p>
<div class="note">
<p>The below assumes you're using Windows PowerShell, but they should run on the standard command line.</p>
</div>
<h3>Taking screenshots of the application's data</h3>
<p>When you install the Windows Phone SDK the Isolated Storage Explorer Tool is also installed. This tooll allows you to easily explore isolated storage on both emulated devices and any plugged in devices.</p>
<p>First you'll want to go to the directory where the tool is installed.</p>
<pre class="code"><code class="powershell">cd "C:\Program Files (x86)\Microsoft SDKs\Windows Phone\v7.1\Tools\IsolatedStorageExplorerTool"</code></pre>
<p>You can now enumerate devices if you want, but there's two parameters that you can tend to rely upon.</p>
<pre class="code"><code class="powershell">.\isetool.exe enumeratedevices</code></pre>
<p>To continue, you'll need to have the guid of the application, which can be found in the WMAppManifest.xml file, and it's the ProductID attribute in the App element.</p>
<p>First, make sure that the application has been started, and any necessary data items have been setup.</p>
<p>Next get a directory listing, so you have an idea of what it looks like.</p>
<pre class="code"><code class="powershell">.\isetool.exe dir xd 00000000-0000-0000-0000-000000000000</code></pre>
<p>This would return something like the following.</p>
<pre class="code"><code class="powershell">       131,072 AppData.sdf
</code><code class="powershell">&lt;DIR&gt;          Shared</code></pre>
<p>Now you can take a screenshot to any directory you like. For example, to grab it from your phone (de = physical device):</p>
<pre class="code"><code class="powershell">.\isetool.exe ts de 00000000-0000-0000-0000-000000000000 D:\projects\JamesRSkemp\WindowsPhone\isolatedstorage</code></pre>
<p>When you run this command you'll have a directory created in the above called IsolatedStore. This will mimic what the dir command above returns.</p>
<p>To take a screenshot of the default emulated device (512 MB emulator), run the above except with xd instead of de.</p>
<pre class="code"><code class="powershell">.\isetool.exe ts xd 00000000-0000-0000-0000-000000000000 D:\projects\JamesRSkemp\WindowsPhone\isolatedstorage</code></pre>
<h3>Restoring screenshots of the application's data</h3>
<p>Now if you want to restore the screenshot you want to make sure you append IsolatedStorage to the end of the directory path.</p>
<pre class="code"><code class="powershell">.\isetool.exe rs xd 00000000-0000-0000-0000-000000000000 D:\projects\JamesRSkemp\WindowsPhone\isolatedstorage\IsolatedStore</code></pre>
<p>Depending upon what you're storing, if you want to move data from one device to another, you can take a screenshot, replace the necessary file(s), and then restore the modified screenshot/directory.</p>
<h3>Possible errors</h3>
<p>As I've been developing I've run into two errors. The message and resolution are below.</p>
<h4>Error: The process cannot access the file because it is being used by another process.</h4>
<p>To resolve this error you need to close the application (back button from the home screen).</p>
<h4>Error: Failed to connect to the device. Ensure that the device is completely booted and is connected to the PC.</h4>
<p>To resolve this error you need to make sure Zune is running and the device is connected, and unlocked.</p>
