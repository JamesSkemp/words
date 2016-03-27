+++
title = "Subversion and TortoiseSVN: Moving a repository"
description = "How to rename an existing Subversion repository."
draft = false
comments = true
date = "2008-09-12T20:18:00-05:00"
modified = "2009-07-22T21:50:33-05:00"
slug = "Subversion-and-TortoiseSVN-Moving-a-repository"
blogengine = "f12b6fdf-5519-4cba-92ed-f17a902df284"
categories = ["software", "tutorials / guides"]
tags = ["subversion", "tortoisesvn", "svn"]
+++

<p>This evening I had to rename a project folder, since I was creating a site with the same name.</p>
<p>Since I had the project (application) under Subversion, I also needed to move the repository.</p>
<p>Here's what I did:</p>
<blockquote>
<p>svnadmin create b:\repos\_newName_</p>
<p>svnadmin dump b:\repos\_oldName_ &gt; b:\repos_dump\_oldName_.dump</p>
<p>svnadmin load b:\repos\_newName_ &lt; b:\repos_dump\_oldName_.dump</p>
</blockquote>
<p>At this point I could either checkout the repository, or change where the checked out directory points to.</p>
<p>I choose to relocate my working copy by right-clicking on my working directory and selecting Relocate from the TortoiseSVN menu. Point it to the new directory, and rename your working directories name, and you're set.</p>
