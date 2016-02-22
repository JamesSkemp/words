+++
title = "Git/posh-git commands"
summary = "After frustration with GitHub for Windows, thanks to Google+ I've completely switched to posh-git. Here are the commands I end up using."
draft = false
comments = true
date = "2013-09-25T20:58:10-05:00"
modified = "2013-10-06T20:43:47-05:00"
slug = "Git-posh-git-commands"
blogengine = ""
categories = ["general programming"]
tags = ["git", "github"]
+++

<p>This is a rough list, in no particular order (yet), but here's the commands I've found useful after being converted to posh-git after <a href="https://plus.google.com/110143205597803895575/posts/Qk4Cfs5Yi9P">my Google+ post</a>.</p>

<pre><code>git add -u
    Add all changes (including deletions)

git rm &lt;file&gt;
    Stage file deletion.

git commit -m "Message"
    Commit with Message.

git push
    Push to GitHub

git status
    See what has changed/etcetera

git pull
    Pull from GitHub

git add &lt;tab&gt; &lt;tab&gt;
    Add multiple files, space delimited

git diff &lt;file&gt;
    Difference. Use Shift + Q to quit.

git reset HEAD &lt;file&gt;
    Unstage change.

git config -l
    List all configuration settings for the current repository.

</code></pre>
