+++
title = "Ubuntu Quickie: Installing MySQL and PostgreSQL"
description = "Quickie on installing MySQL and PostgreSQL to Ubuntu 7.04."
draft = false
comments = true
date = "2007-06-21T21:05:00-05:00"
modified = "2009-12-21T08:11:14-06:00"
slug = "Ubuntu-Quickie-Installing-MySQL-and-PostgreSQL"
blogengine = "c0de1743-61ee-4670-b7c1-5ce4acad9cc3"
categories = ["article", "tutorials / guides"]
tags = ["ubuntu", "mysql", "postgresql"]
+++

<p>For SQL on Ubuntu Linux, I decided it was easiest to just use the repositories to just install MySQL and PostgreSQL.<!--more--></p>
<p>There was a couple of reasons for this. First, MySQL docs recommend it.<!--adsense--></p>
<p>Second, there's not that much that I really want to configure in SQL.</p>
<p>So ...</p>
<h3>MySQL</h3>
<pre class="code"><code class="powershell">sudo apt-get install mysql-server</code></pre>
<p>At the time of this writing, this will install;</p>
<p>libdbd-mysql-perl<br />libdbi-perl<br />libnet-daemon-perl<br />libplrpc-perl<br />mysql-client-5.0<br />mysql-server<br />mysql-server-5.0</p>
<p>Suggested packages:</p>
<p>dbishell<br />libcompress-zlib-perl<br />tinyca</p>
<p>Recommended packages:</p>
<p>mailx</p>
<p>There's some official GUIs that you can also install:</p>
<pre class="code"><code class="powershell">sudo apt-get install mysql-admin mysql-query-browser</code></pre>
<p>At the time of this writing, this will install;</p>
<p>libcairomm-1.0-1<br />libglibmm-2.4-1c2a<br />libgtkhtml3.8-15<br />libgtkmm-2.4-1c2a<br />mysql-admin<br />mysql-admin-common<br />mysql-query-browser<br />mysql-query-browser-common</p>
<p>Suggested packages:</p>
<p>libgtkhtml3.8-dbg</p>
<h3>PostgreSQL</h3>
<p>For PostgreSQL, it's a bit longer of a string, since there's four packages, but it's still easy enough.</p>
<pre class="code"><code class="powershell">sudo apt-get install postgresql-8.2 postgresql-client-8.2 postgresql-client-common postgresql-common</code></pre>
<p>You may as well also go from pgAdmin III, which "is the most popular and feature rich Open Source administration and development platform for PostgreSQL."</p>
<pre class="code"><code class="powershell">sudo apt-get install pgadmin3</code></pre>
<p>At the time of this writing, this will install:</p>
<p>libpq4<br />libwxbase2.6-0<br />libwxgtk2.6-0<br />pgadmin3<br />pgadmin3-data</p>
<p>Recommended packages:</p>
<p>pgagent (adds functionality to schedule PostgreSQL jobs)</p>
<h3>Next time ...</h3>
<p>Next time we'll <a href="http://strivinglife.com/words/post/Ubuntu-Quickie-MySQL-and-PostgreSQL-passwords.aspx">configure databases</a> for both MySQL and PostgreSQL on Ubuntu.</p>
