+++
title = "Backing up a computer to an HP Pocket Media Drive"
summary = "Steps I've taken to ensure that my important files are backed up."
draft = false
comments = true
date = "2009-10-04T19:11:00-05:00"
modified = "2009-10-04T19:13:18-05:00"
slug = "Backing-up-a-computer-to-an-HP-Pocket-Media-Drive"
blogengine = "b9c52793-f2f4-4b38-9049-2165060170d3"
categories = ["article"]
tags = ["hp pocket media drive", "backup"]
+++

<p>Recently I purchased another <a rel="external" href="http://www.amazon.com/gp/product/B002C220YI?tag=strivinglifen-20">HP Pocket Media Drive</a>, with 500 GB of space (instead of the 160 GB drives I had purchased before).</p>
<p>Since I'd like to plan out my backup strategy, and need to backup for my upcoming Windows 7 install (which since I have Vista Ultimate, will require a deal of work), I decided to write this post.</p>
<h3>My computer's setup</h3>
<p>Currently I have a primary 450 GB hard drive (advertised as 500 GB) and a 700 GB secondary drive that I put in (advertised as 750 GB).</p>
<p>The second drive was put in shortly after I purchased/recieved the system, so a good deal of data was placed on the primary drive initially. It calculates out to ~230 GB of used space on the primary drive, and only 30 GB used on the secondary.</p>
<h3>The secondary drive</h3>
<p>I started by putting projects that I was currently working on (Web or applications) and the Subversion repositories&nbsp;on my secondary drive ('B' from now on) instead of my primary ('C') drive. Projects are stored in a projects directory, while SVN repositories are stored in a repos directory, with a repos_dump folder for backup dumps.</p>
<p>External log files from my Web server were also downloaded and stored onto this B drive.</p>
<p>Later I moved over all downloads from C to B, and created directories within a downloads folder with the name of the base&nbsp;application, or in some cases the company name. For example, 7-Zip, Apache HTTP Server, FileZilla, etcetera.</p>
<p>I've experimented with other structures, such as by technology or always by company name, but this seems to break down after a while, or become too confusing.</p>
<h3>The primary drive</h3>
<p>The primary drive contains all installer-installed applications, and their related configuration files, photos that I have taken, and music that I have purchased/ripped.</p>
<p>For some applications, that didn't require source control, I saved the files locally to the C drive.</p>
<h3>First steps</h3>
<p>The first thing to do was to copy all of my photos over to my secondary drive. My intent will be to store everything that I want backed up on my secondary drive, allowing me to easily confirm that files are backed up as they should be.</p>
<p>This also means going through the applications that I use and doing a thorough investigation of what files I have created with those, and whether I wish them to be saved.</p>
<p>It's highly likely that some files I will be unable to copy to my second drive, without causing issues with the applications that use the files, so I'll need to make note of them.</p>
<h3>What I found</h3>
<p>Probably the largest issue was with my iTunes music library, with 34.6 GB of data. Moving this would require consolidating the library to a new location, but may result in the best experience. For now, I've decided to hold off on this, since this only requires copying two directories to my external drive for backups.</p>
<p>VirtualBox also stored virtual machines in a directory in my user folder, by default. Microsoft Virtual PC files were the same.</p>
<p>Programs store configuration settings on the primary drive, like Visual Studio 2008 and the FileZilla FTP client, but both offer manual ways to back these settings up.</p>
<p>Favorites from browsers (Internet Explorer on my machine) also need to be backed up.</p>
<h3>Directory structure on the secondary drive</h3>
<p>To start with, I had a file structure like the following on my second drive:</p>
<ul>
<li>/downloads/</li>
<li>/LogFiles/</li>
<li>/photos/</li>
<li>/projects/</li>
<li>/repos/</li>
<li>/repos_dump/</li>
</ul>
<p>So that I wasn't storing working files on my primary drive, I also created a working directory, and moved a number of folders/files from my Desktop to it. These won't be backed up, or will be backed up on an irregular basis.</p>
<h3>Directory structure on the backup drive</h3>
<p>By default the HP Pocket Media Drive that I purchased came with two directories and an installer in the root directory:</p>
<ul>
<li>Documentation</li>
<li>HP SureStore Application</li>
<li>HPSureStore.exe</li>
</ul>
<p>I have need for none of this, but instead of deleting, I decided to zip these files up into a 'zCameWithDrive.zip' archive.</p>
<p>The next step is to determine what directory structure to use on the backup drive. For ease, I've opted to just keep the same structure on the backup as I have on my secondary drive.</p>
<p>And then begins the copying process, from the secondary drive to the backup.</p>
<h3>Next steps</h3>
<p>I still have to deal with my music files (which I handle now by creating a music directory on the backup, and copying files from the primary drive), program configuration files, favorties, and more, but I've got a good start, and hopefully you do as well.</p>
