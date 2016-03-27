+++
title = "The WordPress calendar is a table"
description = "The default calendar in WordPress is missing a valuable summary attribute - and it needs one soon!"
draft = false
comments = true
date = "2007-01-15T11:19:00-06:00"
modified = "2007-07-23T22:22:30-05:00"
slug = "The-WordPress-calendar-is-a-table"
blogengine = "05c29deb-ecf1-4b2a-b29a-a54dc7721f9b"
categories = ["StrivingLife", "software"]
tags = ["wordpress", "validation"]
+++

<p>
There&#39;s a number of problems with WordPress, as far as accessibility goes.  However, the easiest one to fix is the problem with the calendar, which displays in the default theme, as well as many custom ones (I&#39;m sure).  It lacks a summary tag.<!--more-->
</p>
<p>
Basically, by defining a summary for a table, you provide a way for text-to-speech browsers to explain what a table consists of.  After all, if you&#39;re using a table in your markup, you&#39;re doing so not for layout purposes, but rather for informational purposes.  <span>Id est</span>, a tabulated listing of data.
</p>
<p>
Since WordPress lacks a basic summary for the calendar&#39;s table, this is something of a problem.
</p>
<p>
<a href="http://diveintoaccessibility.org/day_20_providing_a_summary_for_tables.html">Dive Into Accessibility</a> offers a suggestion for a summary of a table, and I recommend WordPress also incorporate this same language.
</p>
<p>
On line 460 of /wp-includes/template-functions-general.php, the following line.
</p>
<blockquote>
	echo &#39;&lt;table id=&quot;wp-calendar&quot;&gt;
</blockquote>
<p>
Should be changed to the following.
</p>
<blockquote>
	echo &#39;&lt;table id=&quot;wp-calendar&quot; summary=&quot;Monthly calendar with links to each day\&#39;s posts&quot;&gt;
</blockquote>
<p>
Now then, who can either point me in the right direction to suggest this change, or who wants to make the change for me?
</p>

