+++
title = "Playing around with Subversion with a test repository"
summary = "In this article I'll be working through creating a test repository in Subversion, and creating two working directories, to see how multiple developers works."
draft = false
comments = true
date = "2008-07-12T18:00:00-05:00"
modified = "2009-10-31T19:07:39-05:00"
slug = "Playing-around-with-Subversion-with-a-test-repository"
blogengine = "54b965f7-e4cc-4ada-9851-b10de68ace68"
categories = ["general programming", "software", "tutorials / guides"]
tags = ["subversion", "svn"]
+++

<p>I've flirted with source/version/revision control since September 2006 (with <a href="/words/?tag=/subversion">Subversion</a>), but have never really dug in to actually do anthing with it. But now, that changes.</p>
<div class="note">
<p>The following guide was created using Subversion 1.4.6 and TortoiseSVN 1.4.8. However, this should still be applicable. Also, because of the number and size of the images, I've limited the images shown directly in the guide. All links to these images should open in a new window.</p>
</div>
<h3>The basics of Subversion</h3>
<p>The basics are that you have a <strong>repository</strong> to store files within. Files in the repository are not directly modified. Instead, you can <strong>check out</strong> a working copy of the files to work on. You can then <strong>check in</strong> (aka <strong>commit</strong>) your working files, at any time, so that they become a part of the repository. When you do this, a new <strong>revision</strong> is created. If multiple people are working on the same repository, you'll also need to <strong>update</strong> your working files and handle any <strong>conflicts</strong>.</p>
<h3>Getting started with Subversion</h3>
<p>I've already covered this in previous posts, for Windows installations.</p>
<ul>
<li>
<div><a href="/words/post/Installing-Subversion-to-Windows-Vista.aspx">Subversion</a></div>
</li>
<li>
<div><a href="/words/post/Installing-TortoiseSVN-to-Windows-Vista.aspx">TortoiseSVN</a></div>
</li>
</ul>
<p>These both cover Windows Vista installations, but <a href="/words/post/Installing-Subversion-and-TortoiseSVN-to-a-Windows-XP-Home-Edition-SP2-local-machine-with-Dreamweaver-8.aspx">an older guide</a> exists for Windows XP.</p>
<p>TortoiseSVN isn't required, but I highly recommend it, and it's how I'll be working through this.</p>
<div class="note">
<p>Personally, I'm a GUI&nbsp;guy, for the most part. If I can have a GUI, I'll use it. Now if&nbsp;I need to use the command line, or the command line will give me additional functionality, I'll use it (when I need to).</p>
</div>
<h3>Creating a test repository&nbsp;</h3>
<p>The first thing to try is a 100% test repository. Again, this will be what keeps track of file versions.</p>
<p>Determine where you'll store your repositories. I have a second hard drive that I'll be using, so my repositories will be stored in B:\repos\ . Substitute your directory structure whenever you see this.</p>
<p>Next, create a new directory under B:\repos\, called repoTest.</p>
<p>Right click on the directory and select TortoiseSVN &gt; Create repository here... (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_01.jpg" target="_blank">See this</a>.)</p>
<p>When prompted, select Native filesystem (FSFS) for the repository type. (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_02.jpg" target="_blank">See this</a>.)</p>
<div class="note">
<p>From what I've read, there doesn't seem to be any reason to choose Berkeley database (BDB) as the type, as it's perk is that it's been around for a while, and is therefore more stable, but it will definitely corrupt if you use it for a network share.</p>
</div>
<p>With that, the repository is created.</p>
<div class="warning">
<p>Again, the repository is not updated directly. You can browse the repoTest directory to see what Subversion (SVN) has created, but don't mess with any of the files.</p>
</div>
<p>Now that you've got a repository, it's time to check out a version you can work with.</p>
<h3>Creating a working directory</h3>
<p>Right-click on the repoTest directory and select SVN Checkout... (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_04.jpg" target="_blank">See this</a>.)</p>
<p>You'll be prompted for the URL of the repository (which should be correct - in this case, <strong>file:///B:/repos/repotest</strong>) and a Checkout directory. This directory is where you'll store your working copy. I created a new directory B:\projects\repoTest\.</p>
<p><img title="Checking out from a repository" src="http://media.jamesrskemp.com/graphics/repotest/repotest_05.jpg" alt="Checking out from a repository" width="466" height="324" /></p>
<p>Leave all other options as they are and press OK to continue.</p>
<p>With that done, you should be shown a window stating that the checkout has finished.</p>
<p>If you now browse to your checkout directory (in my case, B:\projects\) you'll notice that the repoTest directory has a new icon - a green circle with a check.</p>
<h3>Adding files to the working directory</h3>
<p>Let's now create a text file called 'file number 1.txt' in the working directory. For now, leave the file blank.</p>
<p>Now go back up to the B:\projects\ directory and right-click on the repoTest folder. Select SVN Commit... (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_07.jpg" target="_blank">See this</a>.)</p>
<p>Our new file is displayed in the lower half of the window that appears. Check the box next to the file name. Next, enter a meaningful message in the first text box. For example, "First check-in."&nbsp; (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_08.jpg" target="_blank">See this</a>.)</p>
<p>Press OK to continue.</p>
<p>A new window will appear showing that our file has been added and sent. We're also given a revision number, in this case, 1. (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_09.jpg" target="_blank">See this.</a>)</p>
<h3>Checking out another copy&nbsp;</h3>
<p>Now let's go back to our repository and checkout another copy.</p>
<p>This simulates another user working on our repository.</p>
<p>Once again, we can browse to B:\repos\ ,&nbsp;right-click on our repoTest directory, and select SVN Checkout... Or, we can also select TortoiseSVN &gt; Repo-browser . This browser enables you to see all the files in the repository, as well as additional details, like revision. (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_11.jpg" target="_blank">See this.</a>)</p>
<p>If you right-click on the repository, you can select Checkout...</p>
<p>Either way you checkout the repository, do so to a new folder, such as B:\projects\repoTest2\ . (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_12.jpg" target="_blank">See this.</a>)&nbsp;Press OK.</p>
<p>This checks out all files currently committed to the repository. So, when we browse to our new working directory, we'll see&nbsp;'file number 1.txt' .</p>
<h3>Where we're at&nbsp;</h3>
<p>Right now we've&nbsp;got&nbsp;a single repository and two working directories. This is similar to what one might see if two individuals are working on a project.</p>
<p>So,&nbsp;Lisa is B:\projects\repoTest\ and Trish is B:\projects\repoTest2\</p>
<p>Let's treat these imaginary users as human beings, and call them by there names from here on out.</p>
<h3>Lisa&nbsp;adds new files</h3>
<p>Switch to Lisa's repository at B:\projects\repoTest\ . Let's&nbsp;say she creates two new files, called "file number 2.txt" and "file number 3.txt"&nbsp;in this directory.</p>
<p>She also adds some text to file number 1, such as "Lisa has made a modification to this file."</p>
<p>When&nbsp;she modifies file number 1, note that it now has a different icon, as the file has changed.</p>
<p>Now we assume that she wants these to be a part of the repository, so in order to get them in there, she'd have to commit these changes.</p>
<p>Select&nbsp;both of the new files&nbsp;and select TortoiseSVN &gt; Add...</p>
<p>In the prompt that appears, verify both checkboxes next to the file names are selected, and press OK. You'll then be told that both files are added.</p>
<div class="note">
<p>If you still have the repository browser open, if you refresh the repository you'll note that the files haven't been added to the repository. Remember, additions still need to be committed.</p>
</div>
<p>You may have to refresh Explorer, but when you do so, you'll notice that the two new files have new icons - little blue plus signs.</p>
<p>Right-click in the repoTest directory, or on the repoTest folder, and select SVN Commit...</p>
<p>This time you'll see that you've modified one file and added two others. Make sure you put in a message, such as "Lisa updated file 1 and created files 2 and 3." You may note that when you type file, you've got the option to auto-complete with the file names. Pretty nice, eh? (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_19.jpg" target="_blank">See this.</a>)</p>
<p>Go ahead and press OK, verify it completes, and press OK again. (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_20.jpg" target="_blank">See this.</a>)</p>
<h3>What about Trish?</h3>
<p>Now Lisa is up to date with the repository, since she's the only one making changes. But what about Trish?</p>
<p>Let's switch to Trish's directory, B:\projects\repoTest2\ . She still just has file number 1.txt and it's still empty.</p>
<p>Let's go ahead and open her version of file number 1.txt and make a change. For example, add "Trish modified this file."</p>
<p>Right-click on the repoTest2 directory, or within it, and select SVN Commit... Make sure you enter a message!</p>
<p>If you try to commit, the commit will fail. Unfortunately, Trish's version is out of date (it says so). (<a href="http://media.jamesrskemp.com/graphics/repotest/repotest_22.jpg" target="_blank">See this.</a>)</p>
<h3>Getting Trish up-to-date</h3>
<p>We have a couple of options for getting&nbsp;Trish up-to-date. The first is to right-click on&nbsp;'file number 1.txt' and select TortoiseSVN &gt; Check for modifications. We'll see that&nbsp;Trish's version has been modified, and by&nbsp;double-clicking,&nbsp;can see what&nbsp;modifications took place.</p>
<p>However, that's what was modified from the version she checked out.</p>
<p>Press the Check repository button and you'll see an even newer version, the version Lisa checked out.</p>
<div class="note">
<p>In&nbsp;this case, since I'm/we're using the same machine, the User will be the same. However, if we were on different machines, or using different user accounts, the name would be different, and it would be easier to see who made the changes.</p>
</div>
<p>If we now double-click on the file we'll see Lisa's changes compared with our changes.</p>
<p>So now that we've got a conflict, what do we do?</p>
<p>Let's&nbsp;get an updated version of this file by right-clicking on the file and selecting&nbsp;SVN Update.</p>
<p>When we do so, we'll be told that a conflict exists, and will have a couple of&nbsp;files created in our working directory - 'file number 1.txt.mine,' 'file number 1.txt.r1,' and 'file number 1.txt.r2.'&nbsp;In addition, 'file number 1.txt' wll have a small warning icon.</p>
<p>Right-click on this file and select TortoiseSVN &gt; Edit conflicts.</p>
<p>From within TortoiseMerge, we can right click on either of the differences and select a couple of options.</p>
<ol>
<li>
<div>Use a specific text block from one file or another.</div>
</li>
<li>
<div>Use the whole file from one or another.</div>
</li>
<li>
<div>Put our text before/after their text.</div>
</li>
</ol>
<p>The merged/final version will display in the bottom half of the window.</p>
<p>For now, let's go ahead and put Lisa's text before Trish's text.</p>
<p>Right click on the changed block from 'mine'&nbsp;and select 'Use text block from "theirs" before "mine."</p>
<p><img title="Merging changes" src="http://media.jamesrskemp.com/graphics/repotest/repotest_25.jpg" alt="Merging changes" width="446" height="153" /></p>
<p>In the merged version, you'll see Lisa's text before Trish's. Close out of TortoiseMerge and save your changes when prompted, or press the save icon, or select File &gt; Save.</p>
<p>Trish's working copy has now been modified with the updated text, however the file still is in conflict.</p>
<p>Right-click on the file again and select TortoiseSVN &gt; Resolved... Verify that 'file number 1.txt' is checked, and press OK.</p>
<div class="warning">
<p>Make sure the file really has been resolved. If you haven't created a merged version, the code SVN adds to the file will still remain. Because of this, it may be better to press the appropriate button in TortoiseMerge, after saving the document.</p>
</div>
<p>Once you've done so, the extra files are removed from the directory. You'll now need to commit the file back into the repository. Now that the base copy is the same revision, the commit will complete.</p>
<h3>What Trish should have done</h3>
<p>However, there's still an issue with Trish's copy of the repository. She has no file 2 or 3.</p>
<p>What Trish really needs to do is update her copy. She can do so by selecting SVN Update, after right-clicking on/in the repoTest2 folder.</p>
<p>This will allow her to get all the updates that have happened since she first grabbed a copy.</p>
<p>She can also, from this window, see a log (by pressing "Show log...") of revisions, with messages.</p>
<h3>Workflow with&nbsp;more than one&nbsp;developer</h3>
<p>Therefore, based upon this, it's a very good idea to make sure you're pulling updates from the repository on a regular basis.</p>
<p>While there may indeed be times when you don't want to do this, this will allow you to see what other developers have been working on.</p>
<p>She can also use a number of menu items to check on the repository without making commits. The log (Show log), repository browser (Repo-browser), and&nbsp;modifications (Check for modifications) can all be accessed at the directory or file level.</p>
<p>In the case shown below, Lisa has made two additional revisions since Trish last checked files out, including adding two new files and modifying two that Trish already has.</p>
<p><img title="Checking for changes" src="http://media.jamesrskemp.com/graphics/repotest/repotest_38.jpg" alt="Checking for changes" width="685" height="411" /></p>
<p>If Trish hasn't made any changes, it's easy enough to SVN Update and get everything she needs. If she didn't modify any files that have changed, then she won't have to handle any merging of changes. If she has, then she'll just have to handle the conflict, which can involve just ignoring it by using her version (Mine), if she's actually got the version that should be used.</p>
<h3>Deleting our working directories</h3>
<p>At this point we've covered what we need to cover for working with Subversion, using a test repository, and two working directories.</p>
<p>We can clean-up by deleting the B:\projects\repoTest\ and B:\projects\repoTest2\ directories.</p>
<p>Since our repository still exists, we can still get a working copy of the repository. However, if we delete the repository directory, B:\repos\repoTest\, our repository is gone.</p>
<p>Since we don't need it anymore, go ahead and delete this directory.</p>
<h3>To conclude ...</h3>
<p>Probably the best way to start with Subversion is to actually work on a dummy repository, as I've done above.</p>
<h3>Next time</h3>
<p>Next time I'll move an existing Web project into Subversion, since it's definitely time.</p>
<p>Questions, comments, concerns, definitely appreciated.</p>
