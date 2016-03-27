+++
title = "Is it really that simple - redirecting a single file on IIS"
description = "Redirecting a single file on IIS really isn't that difficult. [slnet0514:0a81d74a-197a-47cd-8cba-d6d9b8a7392b]"
draft = false
comments = true
date = "2007-09-02T09:47:00-05:00"
modified = "2009-09-12T21:10:43-05:00"
slug = "Is-it-really-that-simple-redirecting-a-single-file-on-IIS"
blogengine = "0a81d74a-197a-47cd-8cba-d6d9b8a7392b"
categories = ["software", "tutorials / guides"]
tags = ["iis"]
+++

<p>For various reasons, I've been working towards migrating from an Apache server to an IIS one for my sites. For Gavin's site, I couldn't get away with it, but I don't have any problem making things more difficult for myself :D</p>
<p>However, this means that old URLs may not be working as they should.</p>
<p>My experience with IIS is a working knowledge of it, and therefore I know what I need to know, picking up what I can. One thing that I've had a hard time with is figuring out how to do 301 redirects for individual files.</p>
<p>For folders, it's easy enough. So, if the file names have stay the same, but the folder structure has changed, it's easy to setup a redirect.</p>
<p>For domains, it's also easy enough. So, if the domain has changed, but the folder structure and file names have stayed the same, it's easy to setup a redirect.</p>
<p>For individual files, I know now that it's easy enough to enable 301 redirects as well. Well, not quite as easy as Apache, but ...</p>
<p>I've got a file at http://domain/foldername/filename.ext but that should now go to some other file at http://newurl</p>
<p>For Apache, you can add the following to your .htaccess file, in the domain's root folder:</p>
<blockquote>
<p>redirect 301 /foldername/filename.ext http://newurl</p>
</blockquote>
<p>Unfortunately, IIS doesn't have a way to change these via a file (at least, not built-in to IIS 6). But, you can create that file using the old structure, if it doesn't already exist.</p>
<p>Next, open IIS Manager and navigate to the file.</p>
<p>Now right click on the file, select Properties, and change the first option in the File tab from "The designated file" to "A redirection to a URL" and enter the new, full, url into the "Redirect to" field.</p>
<p>"The exact URL entered above" and "A permanent redirection for this resource" should also be selected, as necessary.</p>
<p>I just wish I would have known about this some time ago.&nbsp;</p>
