+++
title = "WP-ShortStat SQL queries"
summary = "SQL queries to update records from older versions of wp-shortstats."
draft = false
comments = true
date = "2006-04-04T20:13:00-05:00"
slug = "WP-ShortStat-SQL-queries"
blogengine = "e30a1139-f67a-4a2a-a7db-d3f132da6071"
categories = ["software"]
tags = ["wordpress", "mysql"]
+++

<p>
The <a href="http://blog.happyarts.de/wp-shortstat/">wp-shortstat plugin</a>, modified for WordPress 2.x use by Markus Kaemmerer, is a great little plugin.  I&#39;ve been using it since March 17, and since Markus has been doing a deal of updating (additional functionality, as well as bug fixes), I&#39;ve been checking it on a regular basis (and have looked through the code more than once).
</p>
<p>
However, since I started out by using 1.3, I&#39;ve got a problem with old records skewing my stats.  To remedy that, I&#39;ve written a couple of SQL queries, for use in phpMyAdmin, for example.  Before I release them to the wild, I wanted to see if I can get a smaller audience to try them out.  I&#39;ve tried them out on my own stats, but ...
</p>
<p>
If someone wants to create a PHP page that does these, certainly go for it - just share the souce code.  There&#39;s also a way to update more than one row at a time, but, I&#39;d much rather do things one row at a time, just in case.
</p>
<p>
If you run these queries, please backup your database, or this table, before you run these queries.  Note that the &#39;standard&#39; table name is wp_ss_stats.  If your&#39;s is named differently, you may have to change these queries accordingly.
</p>
<blockquote>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET version = &#39;2.1&#39; WHERE user_agent = &#39;Googlebot/2.1 (+http://www.google.com/bot.html)&#39; AND version = &#39;Indeterminable&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET version = &#39;2.1&#39; WHERE user_agent = &#39;Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)&#39; AND version = &#39;Indeterminable&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET version = &#39;0.9&#39; WHERE user_agent = &#39;msnbot/0.9 (+http://search.msn.com/msnbot.htm)&#39; AND version = &#39;Indeterminable&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET browser = &#39;msnbot&#39; WHERE user_agent = &#39;msnbot/0.9 (+http://search.msn.com/msnbot.htm)&#39; AND browser = &#39;Crawler/Search Engine&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET version = &#39;1.0&#39; WHERE user_agent = &#39;msnbot/1.0 (+http://search.msn.com/msnbot.htm)&#39; AND version = &#39;Indeterminable&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET browser = &#39;msnbot&#39; WHERE user_agent = &#39;msnbot/1.0 (+http://search.msn.com/msnbot.htm)&#39; AND browser = &#39;Crawler/Search Engine&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET version = &#39;2.1&#39; WHERE user_agent = &#39;Mediapartners-Google/2.1&#39; AND version = &#39;Indeterminable&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET browser = &#39;Feedfetcher-Google&#39; WHERE user_agent = &#39;Feedfetcher-Google; (+http://www.google.com/feedfetcher.html)&#39; AND browser = &#39;Indeterminable&#39;
	</p>
	<p>
	UPDATE &#39;wp_ss_stats&#39; SET browser = &#39;Feedfetcher-Google&#39; WHERE user_agent = &#39;Feedfetcher-Google; (+http://www.google.com/feedfetcher.html)&#39; AND browser = &#39;Crawler/Search Engine&#39;
	</p>
	<p>
	UPDATE wp_ss_stats SET browser = &#39;Yahoo-Blogs&#39; WHERE version = &#39;5.5&#39; AND user_agent = &#39;Yahoo-Blogs/v3.9 (compatible; Mozilla 4.0; MSIE 5.5; http://help.yahoo.com/help/us/ysearch/crawling/crawling-02.html )&#39;
	</p>
	<p>
	UPDATE wp_ss_stats SET version = &#39;3.9&#39; WHERE version = &#39;5.5&#39; AND user_agent = &#39;Yahoo-Blogs/v3.9 (compatible; Mozilla 4.0; MSIE 5.5; http://help.yahoo.com/help/us/ysearch/crawling/crawling-02.html )&#39;
	</p>
</blockquote>
<div class="downloads">
<p>
Download these queries in txt format: <a href="/files/2006/04/mysql%20sql%20queries%20for%20wp_ss_stats.txt">WP-ShortStat SQL queries</a>
</p>
</div>
<p>
Want more added?  Let me know.  I&#39;d like to do Googlebot and Yahoo! Slurp, among others, but I&#39;m waiting for Markus to support them in his plugin.  I figure once he thinks I&#39;m done pestering him, I&#39;ll send him the code and a request ;)
</p>
<p>
Remember, running a SELECT query first is your best bet if you&#39;re unsure of what you may be updating.
</p>
<blockquote>
	SELECT * FROM wp_ss_stats WHERE version = &#39;2.1&#39; AND browser = &#39;Crawler/Search Engine&#39;
</blockquote>

