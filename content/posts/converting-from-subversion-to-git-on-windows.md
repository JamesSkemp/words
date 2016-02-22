+++
title = "Converting from Subversion to Git on Windows"
summary = "Windows Git support sucks. Here's what I ended up doing over the course of a couple hours."
draft = false
comments = true
date = "2013-02-09T10:21:00-06:00"
modified = "2013-02-09T11:48:59-06:00"
slug = "Converting-from-Subversion-to-Git-on-Windows"
blogengine = "a3abbe50-f0ff-40bf-a490-fb5a41a4b1d4"
categories = ["software", "tutorials / guides"]
tags = ["git", "subversion"]
+++

<p>With the news that Visual Studio 2012 will support Git out-of-the-box, and me deciding to stop storing my repositories locally, I decided to switch to Git this weekend.</p>
<p>They say the best way to do this is via <a rel="external" href="https://github.com/nirvdrum/svn2git">svn2git</a>, which unfortunately uses Ruby. Since I'm on Windows, and haven't done Ruby development, I needed to download Ruby using <a rel="external" href="http://rubyinstaller.org/">RubyInstaller for Windows</a>.</p>
<p>Next I needed to have RubyGems support, which meant <a rel="external" href="http://rubyforge.org/projects/rubygems/">downloading from RubyForge</a>.</p>
<p>Unfortunately I had issues installing RubyGems. When I first installed Ruby I decided not to put it in my PATH. However, I couldn't install RubyGems.</p>
<pre class="code">c:\Ruby193\bin&gt;ruby.exe ..\rubygems-1.8.25\setup.rb</pre>
<p>What I ended up having to do was call Ruby slightly differently.</p>
<pre class="code">c:\Ruby193\rubygems-1.8.25&gt;..\bin\ruby.exe setup.rb</pre>
<p>However, it seems as though this step may not have even been necessary, since supposedly 1.9+ includes Gem support by default?</p>
<p>Then I got stuck (user credentials/user migration) and decided to search around, which caused me to find that TortoiseGit supported grabbing from SVN, but that requires msysgit. So I <a rel="external nofollow" href="http://code.google.com/p/msysgit/downloads/list?can=2&amp;q=%22Full+installer+for+official+Git+for+Windows%22">download msysgit</a> and install it, unchecking a bunch of options since I don't intend on using TortoiseGit/msysgit after I get everything ported over.</p>
<p>Now I can download and install <a rel="external nofollow" href="http://code.google.com/p/tortoisegit/wiki/Download?tm=2">TortoiseGit</a>.</p>
<p>At this point I'm wondering if I screw having old commit logs. I've already been thinking for a while how poor Windows support with Git is.</p>
<p>...</p>
<p>...</p>
<p>And I ended up just deciding to start fresh.</p>
