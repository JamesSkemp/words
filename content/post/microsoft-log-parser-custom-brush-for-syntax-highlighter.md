+++
title = "Microsoft Log Parser custom brush for Syntax Highlighter"
description = "A custom Syntax Highlighter brush is now available for Microsoft Log Parser."
draft = false
comments = true
date = "2009-10-18T13:41:00-05:00"
modified = "2009-10-18T14:18:07-05:00"
slug = "Microsoft-Log-Parser-custom-brush-for-Syntax-Highlighter"
blogengine = "38b00801-47b7-4135-97f5-6a47ed40f484"
categories = ["software", "StrivingLife"]
tags = ["log parser"]
+++

<p>It still needs a touch of work, but a basic custom brush for <a rel="external" href="http://alexgorbatchev.com/wiki/SyntaxHighlighter">Syntax Highlighter</a> is available for download.</p>
<p><a rel="external download" href="http://media.jamesrskemp.com/js/shBrushLogParser.js">Download the Microsoft Log Parser custom brush for Syntax Highlighter 2.0.320</a>.</p>
<p>Example included below and at <a rel="external" href="http://logparserplus.com/Examples/Queries.aspx">LogParserPlus.com</a>:</p>
<pre class="code"><code class="logparser">logparser -rtp:-1 "SELECT cs-uri-stem, cs-uri-query, date, sc-status, cs(Referer) INTO 200sReport.txt FROM ex0902*.log WHERE (sc-status &gt;= 200 AND sc-status &lt; 300) ORDER BY sc-status, date, cs-uri-stem, cs-uri-query"</code></pre>
<p>Comments and suggestions are welcomed.</p>
