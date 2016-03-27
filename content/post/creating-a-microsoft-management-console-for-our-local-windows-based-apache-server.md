+++
title = "Creating a Microsoft Management Console for our local Windows-based, Apache server"
description = "In a previous tutorials, we discussed how to access the Services control panel from Windows. In this tutorial, we'll be setting up a custom console that will provide us an easy way to access both our Services control panel, an Event Viewer, as well as other management tools."
draft = false
comments = true
date = "2006-06-03T07:23:00-05:00"
modified = "2007-07-22T17:00:37-05:00"
slug = "Creating-a-Microsoft-Management-Console-for-our-local-Windows-based-Apache-server"
blogengine = "879c8cf0-35ff-42ec-818d-6b6bc1352466"
categories = ["software", "tutorials / guides"]
tags = ["microsoft management console"]
+++

<p>
In a previous tutorials, we discussed how to access the Services control panel from Windows. In this tutorial, we&#39;ll be setting up a custom console that will provide us an easy way to access both our Services control panel, an Event Viewer, as well as other management tools.
</p>
<!--more-->
<p>
First, we&#39;ll need to go to &quot;Start&quot; &gt; &quot;Run...&quot;, or press Windows + R on our keyboards. This will bring up a Run window. Type &#39;mmc&#39;, without the quotes, and press enter or OK.<!--adsense-->
</p>
<h4>Adding the Services control panel</h4>
<p>
You&#39;ll now be presented with an empty console. We&#39;ll now be adding a quick way to access the Services menu. Under File, select &quot;Add/Remove Snap-in&quot;, or press Ctrl + M.
</p>
<p>
We&#39;ll now be presented with a window where we can choose either the Standalone or Extensions tab; stay on the Standalone tab and select &quot;Add...&quot;.
</p>
<p>
You&#39;ll see a number of snap-ins that can be added. For now, scroll down and select &quot;Services&quot;. Double-click on it or press Add. Once you do so, you can choose a couple of options, but at the moment we&#39;ll leave the default of managing the local computer. Once you Finish, you&#39;ll be able to add additional items. For now, press Close, then OK on the remaining pop-up window.
</p>
<p>
You can now access the Services of your local computer. However, other than the left-side column, this is no different that using a/our Services shortcut. However, once we add another snap-in, we&#39;ve got a real benefit.
</p>
<h4>Adding the Event Viewer</h4>
<p>
Sometimes Apache may not start when we Start or Restart it. For that, we need to take a look at the Event Viewer. But, instead of having to open yet another window, we can simply add this to our new console.
</p>
<p>
As we did for the Services control panel, under File, select &quot;Add/Remove Snap-in&quot;, or press Ctrl + M. Again, &quot;Add...&quot; a new standalone snap-in. Select Event Viewer this time, but you&#39;ll still want to just manage the local computer.
</p>
<p>
Finish and Close, and then press OK. You&#39;ll now notice that you&#39;ve got both the Services and Event Viewer added under the Console Root folder. At this point, we&#39;ve setup a console with the two items that we may need to regularly check. So, let&#39;s save our console.
</p>
<p>
To do so, first go to File &gt; Options... We&#39;ll want to give our console a good name, like &quot;Web services&quot;. Next, select File &gt; Save As. Either save this file to your Desktop, or to your default Web folder (like c:\home\) where you store your other shortcuts and files.
</p>
<p>
If you now close out completely, you can open this file to see the console that you&#39;ve created.
</p>
<p>
Now that you&#39;ve setup your own console, you can add additional items to it as the need arises. You can also remove the shortcuts you may have created to the various controls now at your reach within one shortcut.
</p>
<p>
<a href="http://strivinglife.net/wordpress/a-local-apache-web-server-on-a-windows-xp-computer/">View all of the steps to creating a local Web server, for development.</a>
</p>
<div class="note">
<p>
Update 08/31/2006: Note that by changing to User mode will mean that you can no longer make changes to the console.
</p>
<p>
However, there is still a way to switch out of this limited mode. If you open the msc file in Notepad, you can make a change to the ProgramMode value. If this is equal to &ldquo;Author&rdquo;, you can again make changes.
</p>
</div>

