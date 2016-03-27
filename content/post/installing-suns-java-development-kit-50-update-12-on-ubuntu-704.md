+++
title = "Installing Sun's Java Development Kit 5.0 Update 12 on Ubuntu 7.04"
description = "My experience in installing Sun's JDK 5.0 (Update 12) to Ubuntu 7.04."
draft = false
comments = true
date = "2007-06-11T19:21:00-05:00"
slug = "Installing-Suns-Java-Development-Kit-50-Update-12-on-Ubuntu-704"
blogengine = "87ac104a-643b-4d34-a555-63edc761f80f"
categories = ["software", "tutorials / guides"]
tags = ["ubuntu", "firefox", "java"]
+++

<p>
I don&#39;t have much desire to update from the repositories all the time, for whatever reason. Supposedly, if you run Eclipse from the download manager on Ubuntu, you can expect one slow experience.  So ... time to start by installing Sun&#39;s Java.<!--more--><!--adsense-->
</p>
<p>
I read varying ways on how to do this, but this is what worked for me, using Ubuntu 7.04, fully up-to-date, as of June 11, 2007, 7:00 PM, CST.
</p>
<p>
First, I downloaded the current version of JDK 5.0 from http://java.sun.com/javase/downloads/index_jdk5.jsp, for Linux (jdk-1_5_0_12-linux-i586.bin), saving it to the desktop.
</p>
<p>
I then right clicked on the bin file, and under Permissions allowed execute rights.  Elsewhere I saw that this should be made into a deb file, but another said bin was fine, so ...
</p>
<p>
Once spacebar, spacebar, spacebar-ing through the agreement, I agreed and it extracted to /home/strivinglife/
</p>
<p>
In Terminal, I cd /home/strivinglife, followed by sudo mv jdk1.5.0_12 /usr/lib (which moved the entire directory).
</p>
<p>
sudo update-alternatives --install /usr/bin/java java /usr/lib/jdk1.5.0_12/bin/java 300
</p>
<p>
sudo update-alternatives --config java, and then selected the jdk I just installed.
</p>
<p>
I also did <span class="code">sudo ln -s /usr/lib/Java6u1/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins</span> since http://www.java.com/en/download/help/testvm.xml was bombing.
</p>

