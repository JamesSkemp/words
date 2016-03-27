+++
title = "Eclipse SDK 3.2.2 to Ubuntu 7.04"
description = "Installing Eclipse 3.2.2 to Ubuntu 7.04."
draft = false
comments = true
date = "2007-06-12T07:30:00-05:00"
modified = "2007-07-15T22:17:43-05:00"
slug = "Eclipse-SDK-322-to-Ubuntu-704"
blogengine = "b74a5b53-d9ce-413a-b994-ad92759b8757"
categories = ["StrivingLife", "software", "tutorials / guides", "general programming"]
tags = ["eclipse", "ubuntu"]
+++

<p>
Having already <a href="http://strivinglife.net/wordpress/2007/06/11/366/installing-suns-java-development-kit-50-update-12-on-ubuntu-704/">installed JDK 5.0 on Ubuntu</a>, it&#39;s time to install what I really wanted in the first place - Eclipse.<!--more-->
</p>
<p>
The first thing to do is download the current version from http://www.eclipse.org/downloads/. Again, this is something we could grab from a repo, but if I&#39;m using Linux, I may as well have control.
</p>
<p>
Why Eclipse? No Dreamweaver for Ubuntu.
</p>
<p>
After saving it to the Desktop, and after it&#39;s download, I opened up a Terminal.
</p>
<p>
cd ~/Desktop
</p>
<p>
sudo mv eclipse /usr/lib (to move the Eclipse directory).
</p>
<p>
sudo update-alternatives --install /usr/bin/eclipse /usr/lib/eclipse/eclipse 300
</p>
<p>
sudo ln -s /usr/lib/eclipse/startup.jar /usr/bin
</p>
<p>
Adding it to the menu involves right clicking on the Applications item in the menu, and selecting Edit Menus.
</p>
<p>
Add a New Item under whatever menu (for example, Programming). Browse for an icon (/usr/lib/eclipse/icon.xpm), enter <strong>eclipse</strong> into Command, and whatever makes the most sense for Name and Comment.
</p>
<p>
We still have to install Apache, at least, and because I am who I am, ColdFusion as well.
</p>

