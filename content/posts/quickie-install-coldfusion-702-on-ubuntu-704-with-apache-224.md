+++
title = "Quickie: Install ColdFusion 7.02 on Ubuntu 7.04 with Apache 2.2.4"
summary = "Quick notes on installing ColdFusion MX 7 (Developer Edition) to Ubuntu 7.04."
draft = false
comments = true
date = "2007-06-15T20:51:00-05:00"
modified = "2009-12-20T18:16:18-06:00"
slug = "Quickie-Install-ColdFusion-702-on-Ubuntu-704-with-Apache-224"
blogengine = "d526b94c-5f39-43cc-a808-8bbc4c86e23c"
categories = ["article", "tutorials / guides"]
tags = ["ubuntu", "apache", "coldfusion"]
+++

<p>Once again, may not be the best, but installing ColdFusion 7.02 on Ubuntu 7.04 (Apache 2.2.4 already installed).<!--more--></p>
<p><a rel="nofollow" href="http://wulfshayde.blogspot.com/2006/11/ubuntu-610edgy-eft-apache2-php5-mysql.html" target="_blank"><em>Ubuntu 6.10(Edgy Eft) Apache2, PHP5, MySQL &amp; Coldfusion Install Howto</em></a> provided some inspiration, with changes made as necessary (per my <a href="/words/post/Quickie-Install-Apache-224-on-Ubuntu.aspx">Apache 2.2.4 installation</a>).</p>
<p>Downloaded 7.02 Developer Edition from Adobe (coldfusion-702-lin.bin) to src directory.<!--adsense--></p>
<p><span class="code_terminal">cp coldfusion-702-lin.bin coldfusion.bak<br />cat coldfusion.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" &gt; coldfusion-702-lin.bin</span></p>
<p><span class="code_terminal">sudo sh coldfusion-702-lin.bin</span></p>
<p>Server Configuration. Choose a server configuration. Choose Apache.</p>
<p>httpd.conf directory = /usr/local/apache2/conf</p>
<p>Program binary = /usr/local/apache2/bin/httpd (default)</p>
<p>Control file = /usr/local/apache2/bin/apachectl (default)</p>
<p>Continue with installation.</p>
<p>Administrator = /usr/local/apache2/htdocs (default)</p>
<p>User = apache</p>
<p>Password = *****</p>
<p>Don't enable RDS.</p>
<p>Installation finished.</p>
<p>Downloaded 6/16/06 zip file from http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_17883&amp;sliceId=2, with wsconfig (wsconfig.zip) and saved to src directory. Extracted to the same.</p>
<p><span class="code_terminal">sudo mv /opt/coldfusionmx7/runtime/lib/wsconfig.jar /opt/coldfusionmx7/runtime/lib/wsconfig.bak</span></p>
<p>cd src</p>
<p><span class="code_terminal">sudo mv wsconfig.jar /opt/coldfusionmx7/runtime/lib</span></p>
<p><span class="code_terminal">sudo /opt/coldfusionmx7/bin/coldfusion start</span></p>
<p><span class="code_terminal">sudo /opt/coldfusionmx7/runtime/bin/wsconfig</span></p>
<p>In the window that pops up, choose 'Add...'</p>
<p>Configuration Directory: /usr/local/apache2/conf</p>
<p>Check 'Configure' box.</p>
<p>Advanced.</p>
<p>Binary: /usr/local/apache2/bin/httpd</p>
<p>Control script: /usr/local/apache2/bin/apachectl</p>
<p>OK.</p>
<p>OK.</p>
<p>Restart.</p>
<p>Exit window.</p>
<p><span class="code_terminal">sudo nano /usr/local/apache2/conf/httpd.conf</span></p>
<p>Ctrl + W for directoryindex, which should have index.cfm already added (your call if you want to add anything else at this point).</p>
<p><span class="code_terminal">sudo /usr/local/apache2/bin/apachectl restart</span></p>
<p>http://localhost/ should still work, and http://localhost/CFIDE/administrator/ will put you at the Administrator login to finish up there (the server should configure itself, and you should be able to click on a link to continue to the administrator).</p>
<p>Creating a quick file ...</p>
<p><span class="code_terminal">cd /usr/local/apache2/htdocs</span></p>
<p><span class="code_terminal">sudo nano test.cfm</span></p>
<pre class="code"><code class="coldfusion">&lt;cfset testvariable = "Testing." /&gt;
&lt;cfoutput&gt;#testvariable#&lt;/cfoutput&gt;</code></pre>
<p>Save.</p>
<p>http://localhost/test.cfm</p>
