+++
title = "Importing an existing Web site into Subversion"
summary = "In this article I move one of my smaller sites into Subversion, and work through making a change."
draft = false
comments = true
date = "2008-07-13T11:30:00-05:00"
modified = "2009-07-22T21:51:10-05:00"
slug = "Importing-an-existing-Web-site-into-Subversion"
blogengine = "b5a7aa23-d441-41e1-b5ff-9bc0bc2e9fa7"
categories = ["general programming", "tutorials / guides"]
tags = ["subversion", "svn"]
+++

<p>Last time, <a href="/words/post/Playing-around-with-Subversion-with-a-test-repository.aspx">I played around with Subversion</a> in order to determine just how Subversion worked.</p>
<p>This time I'm actually going to create a repository for a site to store the current version, and work through making a couple of updates.</p>
<h3>Existing site structure</h3>
<p>The site that I'll be working with is <a href="http://donotdenymyunicorn.com/" target="_blank">DoNotDenyMyUnicorn.com</a>. It's a small, stable, site, that has just a few files. It's also relatively clean, with no previous versions floating about.</p>
<p>The directory for the site currently exists on another box, at C:\inetpub\wwwroot\donotdenymyunicorn\ and consists of 8 files in that directory.</p>
<ol>
<li>
<div>index.html</div>
</li>
<li>
<div>main234x60.gif</div>
</li>
<li>
<div>print.css</div>
</li>
<li>
<div>robots.txt</div>
</li>
<li>
<div>screen.css</div>
</li>
<li>
<div>sitemap.xml</div>
</li>
<li>
<div>StrivingLifeGmail.png</div>
</li>
<li>
<div>(a Google-related file)</div>
</li>
</ol>
<h3>The new development structure</h3>
<p>I won't be changing the structure of the site, but since I'll be moving the files to my Vista box, I'll have a slightly different structure.</p>
<p>First, I'll be storing the repository at B:\repos\DoNotDenyMyUnicorn\</p>
<div class="note">
<p>You'll note that I'm using seperate repositories for each of my sites. However, I could create one repository for all my sites if I wanted to.</p>
</div>
<p>The development files will be stored at B:\projects\DoNotDenyMyUnicorn\</p>
<h3>My workflow</h3>
<p>Since I'm the only one working on my sites, I'll be keeping things simple. I'll do all my development work in B:\projects\ and push files once they've been tested and commited to the repository.</p>
<p>Depending upon what issues I run into, this may change, but this is what I'm planning for now.</p>
<h3>Creating the repository</h3>
<p>The first thing to do is create the repository we'll be using. The location of the repository will be B:\repos\DoNotDenyMyUnicorn\ , so the first thing to do is make sure that the directory exists. In my case, I need to create the DoNotDenyMyUnicorn folder.</p>
<p>With that done, I can right-click on the DoNotDenyMyUnicorn folder and select TortoiseSVN &gt; Create repository here... (type of Native filesystem, of course).</p>
<h3>Creating the working/development directory</h3>
<p>Now that I've got the repository created, it's time to put data into it.</p>
<p>As I said before, the development directory will be at B:\projects\DoNotDenyMyUnicorn\ .</p>
<p>Now I have a couple of options. I can either import my existing content into Subversion, or I can create a working copy, add my data, and commit it.</p>
<p>In this case I'm going to create a working copy, since that makes more sense to me.</p>
<p>So, I right-click on the DoNotDenyMyUnicorn directory in B:\repos\ and select SVN Checkout...</p>
<p>I'll confirm that the URL is correct (file:///B:/repos/DoNotDenyMyUnicorn) and browse to the Checkout directory of B:\projects\DoNotDenyMyUnicorn .</p>
<p><img title="Checking out a working copy" src="http://media.strivinglife.com/graphics/svn_web/RepoCheckout_DNDMU.jpg" alt="Checking out a working copy" width="400" height="278" /></p>
<p>Pressing OK, I've now got revision 0 in my projects directory.</p>
<p>Next I'll grab the eight files from my XP machine, and copy them into B:\projects\DoNotDenyMyUnicorn\ .</p>
<p>I can now either 'Add...' each of the files I want under version control, or just right-click in/on the DoNotDenyMyUnicorn directory to select SVN Commit...</p>
<p>Depending upon whether I already added the files, I may need to select the files I want added, but since I want them all, a simple check of "Select / deselect all" selects the eight files.</p>
<p>I'll type a meaningful message ("Initial check-in.") and press OK.</p>
<p>This should add the 8 files, and create revision 1.</p>
<div class="tip">
<p>If&nbsp;you don't see any TortoiseSVN status icons on the file icons, you may try refreshing Explorer with F5.</p>
</div>
<h3>Making changes</h3>
<p>Now there's just a few minor things that I want to change about the existing DoNotDenyMyUnicorn. I used Visual Studio 2008, but the editor doesn't really matter.</p>
<p>Once I've made my changes, I'll need to commit them to the repository.</p>
<div class="tip">
<p>Remember that if you have multiple developers, it's a good&nbsp;idea&nbsp;to see if any other updates have taken place since your last update.&nbsp;</p>
</div>
<p>This is as simple as either committing the changes by selecting, or by committing the entire project directory (DoNotDenyMyUnicorn, in B:\projects\) and letting SVN take care of the rest.</p>
<p>In my case I just had the one change.</p>
<p>Once I committed, I pushed the changed files up to my remote Windows server.</p>
<p>While doing so, I noticed that I had a favicon, that I didn't have on my devel site. Whoops.</p>
<p>It was easy enough to download that into my project directory, and add/commit that to the repository.</p>
<h3>Conclusions</h3>
<p>While this doesn't handle trunks, branches, tags, or any of that other fun stuff, for a simple Web site, as <a href="http://donotdenymyunicorn.com/" target="_blank">DoNotDenyMyUnicorn.com</a> is, it's easy enough to move files into version control - much easier than I originally thought.</p>
<p>However, while we didn't talk about it, it's a very good idea to make sure that you have clean directories, without temp files, previous versions, and 'correct' directories. You can always exclude these from versioning, but a clean directory is a developer's favorite directory.</p>
<h3>Next steps</h3>
<p>My next steps are to move more of my sites into version control. Your next step should be to move one of your smaller sites, or <a href="/words/post/Playing-around-with-Subversion-with-a-test-repository.aspx">test Subversion out</a>.</p>
