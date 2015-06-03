+++
title = "Using Disk Investigator to Regain Files"
description = "An exercise showing how to regain lost/deleted files using Disk Investigator."
draft = false
comments = true
date = "2003-10-09T01:01:00-05:00"
modified = "2010-04-02T22:56:23-05:00"
slug = "Using-Disk-Investigator-to-Regain-Files"
blogengine = "78011792-e7e2-4595-85d4-a5a927e06764"
categories = ["article", "software", "tutorials / guides"]
tags = ["windows"]
+++

<p>
I&#39;ve already discussed Disk Investigator in some detail (see <em>Overview of Disk Investigator</em>). However, what I really want to have is an example of the great use Disk Investigator is. In order to do this, I&#39;m going to set up an example - an example of a situation that is not too uncommon - in order to show just how powerful it is. I urge you to follow along, with my example, on your own computer. Please note that for this article I am using Disk Investigator v1.3. I am also using Windows 98, Second Edition (but I have tested this program personally on Windows XP Home, SP1).
</p>
<p>
The first thing we are going to do is create a folder directly within the hard drive of your computer. Most computers designate this drive by &#39;C&#39;. On the desktop, click on &#39;My Computer&#39;, then on &#39;C:&#39;. When you are in the &#39;C&#39; folder, right click in a blank area, and select &#39;New&#39;, and then &#39;Folder&#39;. This will create an empty folder on your hard drive. Let&#39;s name the folder something like &#39;diskinvest&#39;, or &#39;empty1&#39;. I&#39;ll be using &#39;empty1&#39; for this exercise, so please just replace &#39;empty1&#39; with the name that you gave this new folder to follow along.
</p>
<p>
Let&#39;s open this folder (&#39;empty1&#39; - &#39;C:\empty1&#39;). Now, let&#39;s create a new text file, by right clicking in an empty area, and selecting &#39;New&#39;, and then &#39;Text Document&#39;. Let&#39;s name this something like &#39;empty2&#39; (&#39;empty2.txt&#39;). Now we have created a file, called &#39;empty2&#39;, residing within a created folder, &#39;empty1&#39;. The full path of this new file is something like &#39;C:\empty1\empty2.txt&#39;. Now, let&#39;s open up the text file and type some gibberish. For my file, I typed &quot;This file is going to be saved by Disk Investigator&quot;. For this exercise, you may want to copy and paste the above (without the quotes) into the text file, so that we get the same results.
</p>
<p>
Let&#39;s open Disk Investigator now, and find our file. Disk Investigator will start by &quot;Reading Disk Information . . .&quot;, which may take a while on larger hard drives. I&#39;ve included an image of where you&#39;ll want to end up below. If you&#39;ve used Windows before, you&#39;ll have no problem getting to where I am at. If you need clarification on this, please send me an email (I&#39;m not sure if people need to know this, so I&#39;m not going to add it in this edition, however, I will if even one person asks).
</p>
<p>
<a href="http://strivinglife.com/files/images/diskinvest01.jpg" onclick="window.open(this.href);return false;"><img style="width: 475px; height: 235px" src="http://strivinglife.com/files/images/diskinvest01t.jpg" alt="Disk Investigator" title="Disk Investigator" /></a>
</p>
<p>
Here we see where our file is located on the computer, it&#39;s DOS name, it&#39;s size, it&#39;s modified date, and it&#39;s creation date. Right now, nothing else really matters.
</p>
<p>
Now, click on one of the other folders, on the right side of Disk Investigator (such as &#39;C&#39; or &#39;Desktop&#39;). Then, flip back to Windows Explorer, or, on the desktop, go &#39;My Computer&#39; -&gt; &#39;C&#39; -&gt; &#39;empty1&#39;. Now, select our created text file (&#39;empty2&#39;) and delete it (with the Delete key for example). Now, either navigate to the &#39;Recycle Bin&#39;, or close the current window (not Disk Investigator) and open the &#39;Recycle Bin&#39;. You&#39;ll notice that &#39;empty2&#39; is located in the bin. Empty the recycle bin, or delete &#39;empty2&#39; again to remove it from your bin, and therefore from your computer (...). Close this window.
</p>
<p>
Now, switch back to Disk Investigator, and go back like we were before (see the above image). This time, you&#39;ll notice that &#39;empty2&#39; is no longer black, but is rather red. In the bottom left hand corner of Disk Investigator we see that red files are deleted files. If we navigate to &#39;empty1&#39; again, we&#39;ll notice that the folder is quite empty.
</p>
<p>
Now, click on &#39;empty2&#39; and press the &#39;View&#39; button. A window will pop up which will have the text files contents contained in it. If you switch back to looking at &#39;empty1&#39;, you&#39;ll still notice that the file is gone. Press &#39;OK&#39; to dismiss the window. Now, making sure that &#39;empty2&#39; is still selected, press &#39;Undelete&#39;. Disk Investigator will now ask you where you want the file restored to. I choose the C drive, even though you may not normally want to do this, because I have nothing to lose :) Disk Investigator will popup a window telling you were it restored the file to (in my case, &#39;C:\Recovered_10_09_03&#39;). If we navigate to this file we&#39;ll see that we have recovered our information.
</p>
<p>
Of course, while the way above will work, I often (if it is a text file, or a document file with text contained in it) just open up the file and copy/paste the information/text that I need. Sometimes, if you have other processes going, you&#39;ll notice that the information may not be restored correctly. This is because your hard drive saves data on it until it is overwritten - just because you delete something doesn&#39;t mean that it&#39;s completely gone. For example, imagine that your computer is like a sheet of carbon copy paper. If you write something on the top sheet, a copy is created on the carbon copy. Now, if you delete/erase the top copies information, that doesn&#39;t mean that the carbon copy information is erased. Rather, you have to write over it to &#39;get rid&#39; of it (by writing over it, in both cases).
</p>
<p>
I hope that this has helped in using Disk Investigator. It should be noted that you can&#39;t recover information within deleted folders, using Disk Investigator, so, please keep that in mind. However, if Word happens to incorrectly save your document, causing corruption, be happy in the fact that you can still go grab an older copy (with luck) :)
</p>
<p>
Please feel free to email me with any questions you may have regarding the topics covered on this page.
</p>
<p>
<strong>Modified:</strong> January 6th 2004; January 25th 2004<br />
<strong>Notes:</strong> See also my paper titled <em>Overview of Disk Investigator</em>.
</p>

