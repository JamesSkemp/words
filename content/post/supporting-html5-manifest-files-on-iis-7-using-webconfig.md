+++
title = "Supporting HTML5 manifest files on IIS 7 using Web.config"
description = "While particular to HTML5 .manifest files, this can done for any particular MIME type that needs to be changed."
draft = false
comments = true
date = "2011-02-18T18:24:00-06:00"
modified = "2011-02-18T18:47:34-06:00"
slug = "Supporting-HTML5-manifest-files-on-IIS-7-using-Webconfig"
blogengine = "c4338231-6e71-49e1-8fc2-600f2873008a"
categories = ["article"]
tags = ["html5", "iis"]
+++

<p>Having recently picked up an iPod Touch, to replace my Classic, I've become very interested in HTML5's ability to navigate content offline.</p>
<p>In my environment I decided to create a separate directory for my manifest files. I'm also running IIS 7, on Server 2008 R2, so .manifest files are already defined for WPF.</p>
<p>So that that isn't an issue, I created a Web.config file in the manifest directory with the below contents. This effectively removes the already-defined MIME type, and replaces it with the one needed for the HTML5 functionality.</p>
<pre class="code"><code class="xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;configuration&gt;
    &lt;system.webServer&gt;
        &lt;staticContent&gt;
            &lt;remove fileExtension=".manifest" /&gt;
            &lt;mimeMap fileExtension=".manifest" mimeType="text/cache-manifest" /&gt;
        &lt;/staticContent&gt;
    &lt;/system.webServer&gt;
&lt;/configuration&gt;</code></pre>
<p>Any number of online sites can then be used to confirm that the file is passed with the correct type.</p>
