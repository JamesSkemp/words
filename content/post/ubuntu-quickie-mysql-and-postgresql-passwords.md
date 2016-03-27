+++
title = "Ubuntu Quickie: MySQL and PostgreSQL passwords"
description = "Quickie on changing the passwords for MySQL and PostgreSQL, after installing from the repos."
draft = false
comments = true
date = "2007-06-23T08:50:00-05:00"
modified = "2009-12-21T08:04:28-06:00"
slug = "Ubuntu-Quickie-MySQL-and-PostgreSQL-passwords"
blogengine = "6ba5c55e-759b-4d3c-bed7-37c11add2399"
categories = ["article", "tutorials / guides"]
tags = ["ubuntu", "mysql", "postgresql"]
+++

<p>Another Ubuntu Quickie, this time on the default passwords for MySQL and PostgreSQL.</p>
<h3>MySQL</h3>
<pre class="code"><code class="powershell">mysql -u root
UPDATE mysql.user SET Password = OLD_PASSWORD('***password***') WHERE User = 'root';
FLUSH PRIVILEGES;
\q</code></pre>
<h3>PostgreSQL</h3>
<pre class="code"><code class="powershell">
sudo -u postgres psql template1
ALTER USER postgres WITH PASSWORD '***password***';
\q</code></pre>
