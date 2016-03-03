+++
title = "Compiling BlogEngine.NET source with Microsoft Visual C# 2005 Express Edition"
summary = "How to compile a current build of BlogEngine.NET with Microsoft Visual C# 2005 Express Edition."
draft = false
comments = true
date = "2007-09-05T10:51:00-05:00"
modified = "2007-09-08T11:14:18-05:00"
slug = "Compiling-BlogEngineNET-source-with-Microsoft-Visual-C-2005-Express-Edition"
blogengine = "84d55bef-b2aa-4bd9-8dee-f1999fd30237"
categories = ["software", "tutorials / guides"]
tags = ["blogengine.net", "c#", ".net"]
+++

<p>
The follow covers how to compile BlogEngine.NET from the most recently available source code.
</p>
<p>
This was originally posted to the Codeplex discussions for BlogEngine.NET, and will eventually get moved into the wiki. (Update Sept 8, 2007: Added to the <a href="http://www.dotnetblogengine.net/wiki/CompilingFromSource.ashx" target="_blank">BlogEngine.NET wiki</a>, but not yet linked from other pages. Also made a minor change to step one.)
</p>
<h4>Compiling source with Microsoft Visual C# 2005 Express Edition </h4>
<p>
1) Download the current source code from the <a href="http://www.codeplex.com/blogengine/Release/ProjectReleases.aspx" target="_blank">Releases tab</a> or the <a href="http://www.codeplex.com/blogengine/SourceControl/ListDownloadableCommits.aspx" target="_blank">Source code tab</a> on CodePlex.
</p>
<p>
2) Extract the contents of the zip file to a directory on your computer.
</p>
<p>
3) Browse to BlogEngine.sln and open it with a text editor (Notepad).
</p>
<p>
4) Change the second project (BlogEngine.NET) from<br />
..\..\WebSites\BlogEngine.NET\<br />
to<br />
BlogEngine.NET\<br />
Save your changes.
</p>
<p>
5) Open the BlogEngine.sln file with Visual C# Express 2005.
</p>
<p>
6)
If prompted regarding the source control provider, select either Yes or
No at the prompt. When you&#39;re told to &quot;Make sure the application for
the project type () is installed.&quot; say OK.
</p>
<p>
7) From the top menu, select Build &gt; Configuration Manager and change from Debug to Release.
</p>
<p>
8) From the top menu, select Build &gt; Build Solution, or press F6.
</p>
<p>
9) Assuming the build succeeded, browse to DotNetSlave.BusinessLogic\bin\Release</p>
<p>
Copy the dll and XML file to the BlogEngine.NET\Bin\ directory.
</p>
<p>
10) Move the entire BlogEngine.NET directory to your host, in the correct folder.
</p>
<p>
11) Apply the correct Properties and Permissions, to the correct folders, per the regular install guide. 
</p>
<p>
&nbsp;
</p>

