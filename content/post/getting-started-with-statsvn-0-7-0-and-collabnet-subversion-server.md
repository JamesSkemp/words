+++
title = "Getting started with StatSVN (0.7.0) and CollabNet Subversion Server"
description = "While a tool like TortoiseSVN allows limited reporting on Subversion repositories, using a tool like StatSVN generates much more useful reports."
draft = false
comments = true
date = "2010-10-31T10:00:00-05:00"
modified = "2010-10-30T21:23:53-05:00"
slug = "Getting-started-with-StatSVN-0-7-0-and-CollabNet-Subversion-Server"
blogengine = "8c57fc72-c24e-4e1d-be51-a2253617538c"
categories = ["software", "tutorials / guides"]
tags = ["subversion", "statsvn", "apache", "resume"]
+++

<p>This past week I was looking at advanced statistical information about a couple Subversion repositories we use at work.</p>
<p>While TortoiseSVN has some basic reporting, the downside is that, out of the box, users must have access to the repository to access this information.</p>
<p><a rel="external" href="http://www.statsvn.org/">StatSVN</a>, seemingly the most popular solution, works rather well as an alternative to granting this access. The downside (or upside, depending upon your perspective) is that viewers of the report can see what files changed, and how many lines, but not what the actual changes were (outside of the logged message).</p>
<p>At least for our implementation, the lines of code statistic, which seems to be stressed in StatSVN, is also fairly useless for specific commits, which in turn throws off the statistics for the entire repository. (We use third-party code, so being the user that committed that code at a couple of different points, that inflated my numbers.)</p>
<p>Having worked through part of the process at work, refined it at home, and performed a second implementation at work, I present the following steps to implement StatSVN with a CollabNet Subversion Server installation.</p>
<p>Note that these steps, with minor modifications, willl work fine with any Windows and Apache-based installation of Subversion.</p>
<h3>The basic steps</h3>
<ol>
<li>If using authentication, create a user, if one isn't already created, that has access to the repositories and that can be used to checkout the repositories to report on.</li>
<li>If necessary, download and install the Java 4+ requirement for StatSVN.</li>
<li>Download and extract <a rel="external" href="http://www.statsvn.org/">StatSVN</a> to a directory of your choosing. For example, C:\statsvn</li>
<li>Create a directory to store the generated content from StatSVN.</li>
<li>Update Apache to allow access to the reports directory (from step 4).</li>
<li>Checkout or update a working copy of the repository to report on.</li>
<li>Generate the StatSVN reports for the working copy of the repository (from step 6).</li>
</ol>
<p>To make this even easier, I'm including the implementation I've setup at home.</p>
<h3>Example implementation</h3>
<p>StatSVN directory: C:\statsvn</p>
<p>StatSVN outputs directory: C:\statsvn\output</p>
<p>Working copies of repositories are saved to the C:\statsvn directory (C:\statsvn\<em>repositoryName</em>).</p>
<p>From the command line at <strong>C:\Program Files (x86)\CollabNet\Subversion Server\httpd\bin</strong>&nbsp;I ran the following:</p>
<pre class="code"><code class="powershell">htpasswd -m c:\svn_resources\svn-auth-file james-cq5320y</code></pre>
<p>I was then prompted for a password, which I entered twice. This now gives me an account I can use within a batch file to checkout/update repositories, that is specific to the server.</p>
<p>Next the Apache httpd.conf file needed to have the two following additions (where applicable):</p>
<pre class="code"><code class="xml">Alias /stats C:\statsvn\output</code></pre>
<p>That allows http://server1:8080/stats to point to the appropriate directory.</p>
<pre class="code"><code class="xml">&lt;Directory C:/statsvn/output&gt;
	Options Indexes
	allow from all
&lt;/Directory&gt;</code></pre>
<p>And the above allows the directory structure to be returned (the alternative is to manually create an index page, either static or dynamic), that anyone can access. (Since access to this server is only available on my network, this works fine for my situtation.)</p>
<p>Since we've modified the Apache configuration we need to restart the service.</p>
<p>Next we create the batch file that will generate the StatSVN outputs.</p>
<pre class="code"><code class="powershell">set repositoryName=NorthwindExamples
svn checkout http://localhost:8080/svn/%repositoryName% --username james-cq5320y --password PASSWORD
cd %repositoryName%
svn log -v --xml &gt; ..\%repositoryName%.log
cd ..java -jar statsvn.jar -output-dir output\%repositoryName%.Stats %repositoryName%.log %repositoryName%
REM pause</code></pre>
<p>After running this a couple of times I felt satisified that it was working correctly, so you'll see that I commented out the pause.</p>
<p>Of course, that works fine for the initial checkout. Once you have a working copy you can simply update, such as shown in the below batch file contents.</p>
<pre class="code"><code class="powershell">set repositoryName=NorthwindExamples
cd %repositoryName%
svn update
svn log -v --xml &gt; ..\%repositoryName%.log
cd ..java -jar statsvn.jar -output-dir output\%repositoryName%.Stats %repositoryName%.log %repositoryName%
pause</code></pre>
<h3>Optimizations</h3>
<p>Of course, some optimizations could be made, as currently this makes a bit of a mess of the StatSVN directory.</p>
<p>Because of this I'd recommend creating a directory for the working copy and/or logs generated.</p>
