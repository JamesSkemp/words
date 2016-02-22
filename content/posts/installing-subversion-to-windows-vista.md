+++
title = "Installing Subversion to Windows Vista"
summary = "In this article I'll be installing Subversion 1.4.6 to a Windows machine, running Vista Ultimate. [slnet0514:e9b1aa65-ad7c-4484-a26d-6e5696aec003]"
draft = false
comments = true
date = "2008-06-07T15:00:00-05:00"
modified = "2009-10-31T19:04:24-05:00"
slug = "Installing-Subversion-to-Windows-Vista"
blogengine = "e9b1aa65-ad7c-4484-a26d-6e5696aec003"
categories = ["software", "tutorials / guides"]
tags = ["subversion", "windows", "vista", "svn"]
+++

<p>In a previous article, I <a href="/words/post/Installing-Subversion-and-TortoiseSVN-to-a-Windows-XP-Home-Edition-SP2-local-machine-with-Dreamweaver-8.aspx">installed Subversion and TortoiseSVN to a Windows XP Home Edition machine</a>. Later, I <a href="/words/post/Upgrading-Subversion-and-TortoiseSVN-on-Windows-(140-to-142).aspx">upgraded the installation</a>. This time I'll be installing Subversion on a Windows Vista Ultimate SP1 machine.</p>
<h3>The setup</h3>
<p>The system I'm using is a HP Pavilion a6360t, with 4GB install RAM, 2.20 GHz, with two cores, running Windows Vista Ultimate SP1, 32-bit.</p>
<p>I'm already running IIS 7, so I won't be installing Apache to run Subversion.</p>
<h3>Downloading Subversion</h3>
<p>On the <a rel="external" href="http://subversion.tigris.org/">official Subversion site</a>, downloads can be found under Getting&nbsp;Subversion &gt; Downloads. I went for the "friendly Installer program" link, and downloaded the file svn-1.4.6-setup.exe.</p>
<h3>Installing Subversion</h3>
<p>Unless you've turned it off, trying to run the installer will prompt you if you want to allow access to your computer. You do.</p>
<p>Continue through the installer screens, setting up Subversion as you'd like.</p>
<p>I opted to install in the default directory of C:\Program Files\Subversion\ but without the desktop or quick launch icons.</p>
<h4>Install screens</h4>
<p>Below are the screens from the installer for Subversion 1.4.6.</p>
<p><img style="width: 398px; height: 169px;" title="Subversion Setup Screen 1" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_01.jpg" alt="Subversion Setup Screen 1" width="398" height="169" /> <img style="width: 513px; height: 396px;" title="Subversion Setup Screen 2" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_02.jpg" alt="Subversion Setup Screen 2" width="513" height="396" /> <img style="width: 513px; height: 396px;" title="Subversion Setup Screen 3" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_03.jpg" alt="Subversion Setup Screen 3" width="513" height="396" /> <img style="width: 513px; height: 396px;" title="Subversion Setup Screen 4" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_04.jpg" alt="Subversion Setup Screen 4" width="513" height="396" /> <img style="width: 513px; height: 396px;" title="Subversion Setup Screen 5" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_05.jpg" alt="Subversion Setup Screen 5" width="513" height="396" /> <img title="Subversion Setup Screen 6" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_06.jpg" alt="Subversion Setup Screen 6" width="513" height="396" /> <img src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_07.jpg" alt="" width="513" height="396" /> <img title="Subversion Setup Screen 8" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_08.jpg" alt="Subversion Setup Screen 8" width="513" height="396" /> <img title="Subversion Setup Screen 9" src="http://media.jamesrskemp.com/graphics/subversion/subversion_1.4.6_install_09.jpg" alt="Subversion Setup Screen 9" width="513" height="396" /></p>
<h3>Post-Installation</h3>
<p>If you run the following command at a prompt, you can&nbsp;verify that your installation is complete. To run a command, select the Run command from the Start menu, or use the Start Search&nbsp;and type <strong>cmd</strong>.</p>
<pre class="code"><code class="powershell">svnadmin ?</code></pre>
<p>Assuming you see a listing of available subcommands, you should be set.</p>
<p>At this point, I've covered what I need to for installing Subversion to Windows Vista.</p>
<p>Next time I'll be covering TortoiseSVN, which will allow direct integration with Windows Explorer.</p>
