+++
title = "Installing Subversion binaries for Apache 2.2.x"
description = "In this article we'll be covering the installation of Subversion to work with Apache 2.2.x."
draft = false
comments = true
date = "2008-08-19T21:30:00-05:00"
modified = "2009-08-09T18:38:43-05:00"
slug = "Installing-Subversion-binaries-for-Apache-22x"
blogengine = "f5d7386a-6b9e-455d-bb5e-642045634133"
categories = ["software", "tutorials / guides"]
tags = ["subversion", "apache", "vista", "tortoisesvn", "svn"]
+++

<p>Recently I went ahead and <a href="/words/post/Install-Apache-229-to-Windows-Vista-Ultimate.aspx">installed Apache 2.2.9 to my Windows Vista Ultimate</a> machine. The purpose of doing that was to move towards <a href="/words/post/Playing-around-with-Subversion-with-a-test-repository.aspx">a Subversion install</a> running on Apache.</p>
<p>In this article, I'll be covering that installation.</p>
<h3>Getting Subversion</h3>
<p>Obviously, the first thing to do is to <a href="http://subversion.tigris.org/" target="_blank">get Subversion</a>.</p>
<p>We're looking for the Windows Apache 2.2.x binaries, in particular. At the time of this writing, that's svn-win32-1.5.1.zip.</p>
<div class="note">
<p>In <a href="/words/post/Playing-around-with-Subversion-with-a-test-repository.aspx">a previous guide</a>, which you may have followed,&nbsp;I installed the Windows installer with the basic win32 binaries. If you did this, you'll want to uninstall Subversion first.</p>
</div>
<p>Once you've downloaded the zip, extract the contents.</p>
<h3>Installing the binaries</h3>
<p>The&nbsp;README included in the zip&nbsp;basically covers what you need to do.</p>
<p>Determine where you want&nbsp;to install Subversion. I decided to keep it in the Program Files directory, so I created a new Subversion folder&nbsp;at C:\Program Files\Subversion.</p>
<p>Next, move the four directories and file, from the zip,&nbsp;to this directory.</p>
<p>Now go to Start and right click on Computer, selecting Properties. Go to the Advanced tab and press the Environment Variables... button. At the end of the Path system variable, add the location of the Subversion bin directory. For example, C:\Program Files\Subversion\bin . Press OK all the way out.</p>
<div class="note">
<p>You should be able to open a command line and type <strong>svnadmin -?</strong> and get a meaningful bunch of commands.</p>
</div>
<p>In a new instance of Windows Explorer, navigate to the <strong>modules</strong> directory in the Apache install directory. For example, c:\Program Files\Apache Software Foundation\Apache2.2\modules.</p>
<p>Copy <strong>mod_authz_svn.so</strong> and <strong>mod_dav_svn.so</strong> from your Subversion install's <strong>bin</strong> directory into the Apache <strong>modules</strong> directory.</p>
<p>Still in the Subversion&nbsp;<strong>bin</strong> directory, copy the <strong>intl3_svn.dll</strong> and <strong>libsvn_fs-1.dll</strong> files into the Apache <strong>bin</strong> directory.</p>
<div class="note">
<p>If you want to use Berkeley DB, grab the libdb44.dll (or <strong>libdb*.dll</strong>)&nbsp;instead of the latter.</p>
</div>
<p>Next open the httpd.conf file (we <a href="/words/post/Install-Apache-229-to-Windows-Vista-Ultimate.aspx">covered how to do this</a> before) and uncomment the following two lines (remove the #):</p>
<blockquote>
<p>#LoadModule dav_module modules/mod_dav.so<br />#LoadModule dav_fs_module modules/mod_dav_fs.so</p>
</blockquote>
<p>Now add these two after the existing LoadModule lines (you may want to add a comment noting why&nbsp;you've added these):</p>
<blockquote>
<p>LoadModule authz_svn_module modules/mod_authz_svn.so<br />LoadModule dav_svn_module modules/mod_dav_svn.so</p>
</blockquote>
<p>Now go to the bottom of the httpd.conf file and add the following information:</p>
<p>&lt;Location /svn/repos&gt;<br />&nbsp;&nbsp;&nbsp;&nbsp; DAV svn<br />&nbsp;&nbsp;&nbsp;&nbsp; SVNListParentPath on<br />&nbsp;&nbsp;&nbsp;&nbsp; SVNParentPath Drive:\path\to\repos<br />&lt;/Location&gt;&nbsp;</p>
<p>For example:</p>
<p>&lt;Location /svn/repos&gt;<br />&nbsp;&nbsp;&nbsp;&nbsp; DAV svn<br />&nbsp;&nbsp;&nbsp;&nbsp; SVNListParentPath on<br />&nbsp;&nbsp;&nbsp;&nbsp; SVNParentPath B:\repos<br />&lt;/Location&gt;</p>
<p>Restart Apache via the Apache Service Monitor.</p>
<div class="tip">
<p>If you get any errors, check your error logs (<strong>logs</strong> directory in the Apache install directory).</p>
<p>Windows event logs (Administrative Tools &gt; Event Viewer or <strong>eventvwr</strong> from the command line) may also have relevant error information.</p>
</div>
<p>Once Apache starts, browse to <a href="http://localhost:8080/svn/repos/">http://localhost:8080/svn/repos/</a> (assuming you used that port and directory), and you should see a listing of your repositories.</p>
<p>You can now browse the current versions of the files under Subversion.</p>
<h3>TortoiseSVN</h3>
<p>While you're at it, you may want to install or update <a href="http://tortoisesvn.net" target="_blank">TortoiseSVN</a>.</p>
<p>I already covered <a href="/words/post/Installing-TortoiseSVN-to-Windows-Vista.aspx">how to install Subversion on Vista</a>, and the steps still apply.</p>
<h3>Upgrading existing repositories</h3>
<p>If you've already installed Subversion, and have been working with it, you may need to upgrade your existing repositories.</p>
<p>You can do this via the command line by running <strong>svnadmin upgrade \path\to\repository</strong> , however, you should ensure that you have a backup before you do this. Also, you'll be unable to use tools that cannot access the 1.5 repos.</p>
