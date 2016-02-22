+++
title = "Example batch file to dump Subversion repositories"
summary = "Sample batch file to easily dump all Subversion repositories in a single directory."
draft = false
comments = true
date = "2009-11-19T21:52:00-06:00"
modified = "2009-11-19T22:03:00-06:00"
slug = "Example-batch-file-to-dump-Subversion-repositories"
blogengine = "f15793a8-e37f-4860-a9a7-8deb62eee256"
categories = ["tutorials / guides"]
tags = ["subversion", "windows"]
+++

<p>I have a large collection of repositories, and until now ran a single batch file that had to be updated each time I created a new repository, to add the new directory.</p>
<p>To combat that, I did some research and created a new batch file that does all the heavy lifting for me.</p>
<p>To save others time, I present it below.</p>
<pre class="code"><code class="powershell">SET timeVar=%date:~10,4%%date:~4,2%%date:~7,2%
SET repoDumpDir=..\repos_dump
FOR /D %%G IN (*) DO svnadmin dump %%G &gt; %repoDumpDir%%%G%timeVar%.dump

PAUSE</code></pre>
<p>The key items are the repoDumpDir variable, which you'll want to set accordingly. (Save and run this batch file in the directory you store your repositories.)</p>
<p>For each directory it finds, it assumes it's a repository and attempts to do an <a rel="external" href="http://svnbook.red-bean.com/nightly/en/svn.ref.svnadmin.c.dump.html">svnadmin dump</a>, so we can restore if needed. It&nbsp;adds today's date (YYYYMMDD) to the end of the repository (directory) name.</p>
