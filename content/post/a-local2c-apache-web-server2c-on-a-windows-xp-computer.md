+++
title = "A local, Apache Web server, on a Windows XP computer"
description = "A listing of tutorials on how to add various functionality to a local, Apache, server."
draft = false
comments = true
date = "2006-02-27T03:23:00-06:00"
modified = "2010-03-12T12:33:23-06:00"
slug = "A-local2c-Apache-Web-server2c-on-a-Windows-XP-computer"
blogengine = "4d03d7d5-e74c-44fb-89f6-40fcf173523e"
categories = ["software", "technology", "tutorials / guides"]
tags = ["apache", "perl", "python", "php", "mysql", "postgresql", "coldfusion"]
+++

<p>My intention is to write a number of guides that will help someone build a functional Web server for testing purposes. Since Windows is fairly popular, I've decided to outline how to install Web server programs on it. Since Apache is both powerful and free, I've opted to use it as the core, instead of IIS, or the like.</p>
<p>I also plan on keeping the various technologies up-to-date, yet continuing to provide the instructions for past versions used, just in case. I do have copies of the versions I've installed below, and would be happy to provide those copies that no longer exist elsewhere; just ask.</p>
<h3>Our local Web server uses the following technology.</h3>
<ul>
<li><strong>Apache</strong> 
<ul>
<li>Apache 2.2.4 
<ul>
<li><a href="http://strivinglife.com/words/post/Installing-Apache-224-to-a-Windows-based-computer-locally-Part-1.aspx">Part 1: Setting up Apache 2.2.4</a></li>
</ul>
</li>
<li>Apache 2.0.59 
<ul>
<li><a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-1.aspx">Part 1: Apache 2.0.59, Perl, mod_perl</a></li>
<li><a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-2.aspx">Part 2: ColdFusion MX 6.1 and ColdFusion MX 7.0</a></li>
<li><a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-3.aspx">Part 3: PHP 4.4.2 and PHP 5.1.4, with MySQL and PostgreSQL support</a></li>
<li><a href="/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-4.aspx">Part 4: Using batch files to switch between versions of our local server</a></li>
</ul>
</li>
<li><em>was</em>: <a href="/words/post/Installing-Apache-to-a-Windows-based-computer2c-locally.aspx">Apache 1.3.34</a></li>
<li>.htaccess file 
<ul>
<li><a href="/words/post/Error-handling-on-a-local-Windows-based%2c-Apache2c-server.aspx">Error Handling</a></li>
</ul>
</li>
</ul>
</li>
<li><strong>Perl</strong> 
<ul>
<li><a href="/words/post/Upgrading-(our-local-install-of)-ActivePerl.aspx">ActivePerl 5.8.8.819</a> 
<ul>
<li><em>was</em>: <a href="http://strivinglife.com/words/post/Installing-Perl-on-a-local-Windows-based-Apache-server.aspx">ActivePerl 5.8.7.815</a>, ActivePerl 5.8.8.817</li>
</ul>
</li>
<li><a href="http://strivinglife.com/words/post/Installing-mod_perl-on-a-local-Windows-based-Apache-server.aspx">mod_perl 1.0: version 1.29</a></li>
<li><a href="http://strivinglife.com/words/post/Installing-Apache-2059-to-a-Windows-based-computer2c-locally-Part-1.aspx">mod_perl 2.0</a></li>
</ul>
</li>
<li><strong>Python</strong> 
<ul>
<li><a href="http://strivinglife.com/words/post/Installing-Python-on-a-local-Windows-based-Apache-server.aspx">ActivePython 2.4.3.12</a></li>
</ul>
</li>
<li><strong>PHP</strong> 
<ul>
<li><a href="http://strivinglife.com/words/post/Upgrading-PHP-(442-to-444-and-514-to-520).aspx">Upgrading PHP 4.x and/or PHP 5.x</a> (4.4.2 to 4.4.4 and 5.1.4 to 5.2.0)</li>
<li><a href="/words/post/Installing-PHP-on-a-local-Windows-based%2c-Apache%2c-server.aspx">PHP 4.4.2</a> and <a href="/words/post/Dual-installing-PHP-Running-PHP-5-and-4-on-the-same-local-Windows-based-Apache-server.aspx">PHP 5.1.4</a> (with the ability to run one or the other) 
<ul>
<li><a href="http://strivinglife.com/words/post/Installing-Python-on-a-local-Windows-based-Apache-server.aspx">Changing our PHP directory name/location</a></li>
</ul>
</li>
<li><a href="http://strivinglife.com/words/post/Upgrading-to-Zend-Optimizer-301-on-a-local-Windows-based-Apache-server.aspx">Zend Optimizer 3.0.1</a> 
<ul>
<li><em>was</em>: <a href="http://strivinglife.com/words/post/Installing-Zend-Optimizer-on-a-local-Windows-based2c-Apache2c-server.aspx">Zend Optimizer 2.6.2</a></li>
</ul>
</li>
</ul>
</li>
<li><strong>MySQL</strong> 
<ul>
<li>MySQL 4.1.18: <a href="http://strivinglife.com/words/post/Installing-MySQL-and-phpMyAdmin-on-a-local-Windows-based-Apache-server.aspx">with PHP 4.4.2</a>, <a href="http://strivinglife.com/words/post/Dual-installing-PHP-Running-PHP-5-and-4-on-the-same-local-Windows-based-Apache-server.aspx">with PHP 5.1.4</a>, <a href="http://strivinglife.net/wordpress/?p=69">with ColdFusion MX 6.1</a></li>
<li><a href="http://strivinglife.net/wordpress/2006/06/20/154/upgrading-phpmyadmin-270-pl2-to-281-on-a-local-windows-based-apache-server/">phpMyAdmin 2.8.1</a> 
<ul>
<li><em>was</em>: <a href="/words/post/Installing-MySQL-and-phpMyAdmin-on-a-local-Windows-based%2c-Apache%2c-server.aspx">phpMyAdmin 2.7.0-pl2</a></li>
</ul>
</li>
<li><a href="http://strivinglife.com/words/post/Installing-MySQL-Administrator-on-a-local-Windows-based-Apache-server.aspx">MySQL Administrator 1.1.9</a></li>
<li><a href="http://strivinglife.com/words/post/Installing-MySQL-Query-Browser-1120-on-a-local-Windows-based-Apache-server.aspx">MySQL Query Browser 1.1.20</a></li>
</ul>
</li>
<li><strong>PostgreSQL</strong> 
<ul>
<li>PostgreSQL 8.1.3 or PostgreSQL 8.2.3 and pgAdmin 1.4.1 or pgAdmin 1.6.2: <a href="/words/post/Installing-PostgreSQL-on-a-local-Windows-based%2c-Apache%2c-server.aspx">with PHP 4.4.2</a>, <a href="http://strivinglife.com/words/post/Dual-installing-PHP-Running-PHP-5-and-4-on-the-same-local-Windows-based-Apache-server.aspx">with PHP 5.1.4</a>, <a href="/words/post/Adding-PostgreSQL-connectivity-to-ColdFusion-MX-on-a-local-Windows-based%2c-Apache%2c-server.aspx">with ColdFusion MX 6.1</a></li>
</ul>
</li>
<li><strong>ColdFusion</strong> 
<ul>
<li><a href="/words/post/Installing-ColdFusion-on-a-local-Windows-based%2c-Apache%2c-server.aspx">ColdFusion MX 6.1 Developer Edition</a></li>
<li><a href="/words/post/Upgrading-our-installation-of-ColdFusion-MX-701-on-a-local-Windows-based%2c-Apache%2c-server.aspx">ColdFusion MX 7.0.2 Developer Edition</a> 
<ul>
<li><em>was</em>: <a href="/words/post/Installing-ColdFusion-MX-701-on-a-local-Windows-based%2c-Apache%2c-server.aspx">ColdFusion MX 7.0.1 Developer Edition</a> (upgrade, but with the ability to swap to 6.1)</li>
</ul>
</li>
</ul>
</li>
<li><a href="/words/post/Upgrading-(our-local-install-of)-WordPress.aspx">WordPress 2.0.5</a> 
<ul>
<li><em>was</em>: <a href="/words/post/Setting-up-WordPress-on-a-local-Web-server.aspx">WordPress 2.0.1</a>, 2.0.2, 2.0.4</li>
</ul>
</li>
<li><a href="/words/post/Log-file-analysis-of-our-Windows-based%2c-Apache%2c-Web-sites.aspx">Analog 6.0</a> 
<ul>
<li><em>Other software to try: <a href="/words/post/Log-file-analysis-of-our-Windows-based%2c-Apache%2c-Web-sites.aspx">WebLog Expert Lite 3.6</a></em></li>
</ul>
</li>
<li><a href="/words/post/Creating-a-Microsoft-Management-Console-for-our-local-Windows-based%2c-Apache-server.aspx">Microsoft Management Console setup</a></li>
<li><a href="/words/post/Installing-Eclipse-32-to-a-Windows-XP-SP2-machine.aspx">Eclipse 3.2</a></li>
<li><strong>Versioning control</strong> 
<ul>
<li><a href="http://strivinglife.com/words/post/Installing-Subversion-and-TortoiseSVN-to-a-Windows-XP-Home-Edition-SP2-local-machine-with-Dreamweaver-8.aspx">Subversion, TortoiseSVN and Dreamweaver 8</a></li>
</ul>
</li>
<li><a href="/words/post/PHP-Forum-Software-Showdown.aspx">Forums</a> 
<ul>
<li><a href="/words/post/PHP-Forum-Software-Showdown-Part-1-bbPress.aspx">bbPress 0.73</a></li>
<li><a href="/words/post/PHP-Forum-Software-Showdown-Part-4-MyBB.aspx">MyBB 1.2.1</a></li>
<li><a href="/words/post/PHP-Forum-Software-Showdown-Part-6-phpBB.aspx">phpBB 2.0.21</a></li>
<li><a href="/words/post/PHP-Forum-Software-Showdown-Part-5-PunBB.aspx">PunBB 1.2.14</a></li>
<li><a href="/words/post/PHP-Forum-Software-Showdown-Part-3-Simple-Machines.aspx">Simple Machines 1.0.9</a></li>
<li><a href="/words/post/PHP-Forum-Software-Showdown-Part-2-Vanilla.aspx">Vanilla 1.0.1</a></li>
</ul>
</li>
</ul>
<h3>The following upgrades are planned for addition (in no particular order):</h3>
<ul>
<li>MySQL 4.1.21</li>
<li>phpMyAdmin 2.9.1.1</li>
<li>PostgreSQL 8.1.5 
<ul>
<li>pgAdmin III 1.6.0</li>
</ul>
</li>
</ul>
<h3>The following information is planned for expanding the tutorials, in no particular order:</h3>
<ul>
<li>World's simplest, but professionally functional, Web page</li>
<li>MagpieRSS</li>
<li>how to restore WordPress/MySQL using phpMyAdmin</li>
<li>how to setup a CMS (Joomla and possibly Mambo)</li>
<li>AWStats</li>
<li>FusionReactor</li>
<li>sending mail</li>
<li>FTP?</li>
</ul>
<p>As new pages are added, I will add additional links and items to the above. If you would like me to cover a particular program, please let me know - any possible additions to this list would be appreciated.</p>
