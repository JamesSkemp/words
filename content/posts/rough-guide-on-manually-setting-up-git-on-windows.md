+++
title = "Rough guide on manually setting up Git on Windows"
summary = "Rough guide on how to manually install Git on Windows."
draft = false
comments = true
date = "2013-10-06T08:58:25-05:00"
modified = "2014-07-13T12:53:53-05:00"
slug = "Rough-guide-on-manually-setting-up-Git-on-Windows"
blogengine = ""
categories = ["software", "tutorials / guides"]
tags = ["git"]
+++

<p>For both machines I'm doing this on (running Windows 7 and Windows 8) I had already installed Github for Windows. However, since I've been converted to posh-git, I wanted to do an install that would get me away from continuing to use it.</p>

<p>The below is roughly what I did, and may not be completely correct.</p>

<ol>
<li>Install the latest version of <a href="http://msysgit.github.io/" rel="external">msysgit</a> (currently 1.8.4).</li>
<li>Set execution policy (run as administrator).<ul><li><code>Set-ExecutionPolicy RemoteSigned</code></li></ul></li>
<li>Install posh-git<ul><li><code>(new-object Net.WebClient).DownloadString("http://psget.net/GetPsGet.ps1") | iex</code></li></ul></li>
<li>Possibly open the Powershell profile and add the Git path when Powershell runs.<ul>
<li><code>notepad $profile</code></li>
<li>Add to the top of the file:<br /><code>$env:path += ";" + (Get-Item "Env:ProgramFiles(x86)").Value + "\Git\bin"</code></li>
<li>Reload profile:<br /><code>. $profile</code></li>
<li>Thanks to <a href="http://stackoverflow.com/a/17625052/11912" rel="external">G. Lombard</a>.</li>
</ul></li>
<li>Actually install posh-git.
<ul><li><code>install-module posh-git</code></li>
<li>Reload profile:<br /><code>. $profile</code></li></ul></li>
<li>Verify/set global config options (user name and email).<ul>
<li><code>git config --global -l</code></li>
<li><code>git config --global user.name "Your Name Here"</code></li>
<li><code>git config --global user.email "your_email@example.com"</code></li>
</ul>
<li>Update push behavior:<ul><li><code>git config --global push.default simple</code></li><li>See <a href="http://stackoverflow.com/a/13148313/11912">Warning: push.default is unset; its implicit value is changing in Git 2.0</a></li></ul></li>
<li>Since I'm using Powershell 3.0 (ISE), I decided to remove the 'Dark' color versions of the displayed information:<ul>
<li><code>notepad $profile</code></li>
<li>Add the following at the end of the file:<ul>
<li><code class="powershell">$global:GitPromptSettings.BeforeIndexForegroundColor = [ConsoleColor]::Green<br />
$global:GitPromptSettings.IndexForegroundColor       = [ConsoleColor]::Green<br />
$global:GitPromptSettings.WorkingForegroundColor    = [ConsoleColor]::Red<br />
$global:GitPromptSettings.UntrackedForegroundColor  = [ConsoleColor]::Red</code></li>
<li>See also <a href="http://sedodream.com/2012/05/05/GitCustomizingColorsForWindowsIncludingPoshgit.aspx" rel="external">Git customizing colors for Windows including posh-git</a><ul><li>This involved running these two commands:<br /><code>git config --global color.status.changed "magenta normal bold"</code><br /><code>git config --global color.status.untracked "magenta normal bold"</code></li></ul></li>
</ol>

<h3>Todo</h3>

<p>http://deanclatworthy.com/2013/01/how-to-avoid-relying-on-github-mirror-your-repository/</p>

<p>http://www.harecoded.com/migrating-github-repo-to-bitbucket-or-similar-services-2275467</p>
