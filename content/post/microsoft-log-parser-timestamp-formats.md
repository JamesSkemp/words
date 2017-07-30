+++
title = "Microsoft Log Parser timestamp formats"
description = "Timestamp formats supported by Microsoft Log Parser."
draft = false
comments = true
date = "2009-02-06T20:32:00-06:00"
modified = "2011-07-17T15:38:10-05:00"
slug = "Microsoft-Log-Parser-timestamp-formats"
blogengine = "cee9cabe-8990-4dce-a777-1ed280d3ffb8"
categories = ["software", "tutorials / guides"]
tags = ["log parser"]
aliases = ["/post/Microsoft-Log-Parser-timestamp-formats/"]
+++

<p>The following article covers the <a rel="external" href="http://logparserplus.com/functions#function_TO_TIMESTAMP">timestamp</a> format specifiers accepted by Microsoft Log Parser.</p>
<h3>Date</h3>
<ul>
<li>
<div>Year</div>
<ul>
<li>
<div>y, yy, yyy, yyyy = last 1, 2, 3, or 4 digits, relative to 2000</div>
</li>
</ul>
</li>
<li>
<div>Month</div>
<ul>
<li>
<div>M = no leading zero</div>
</li>
<li>
<div>MM = leading zero</div>
</li>
<li>
<div>MP = leading space</div>
</li>
<li>
<div>MX = no leading zero, or with or without zero when parsing</div>
</li>
<li>
<div>MMM = 3-character abbreviation</div>
</li>
<li>
<div>MMMM = full name of month</div>
</li>
</ul>
</li>
<li>
<div>Day</div>
<ul>
<li>
<div>d = no leading zero</div>
</li>
<li>
<div>dd = leading zero</div>
</li>
<li>
<div>dp = leading space</div>
</li>
<li>
<div>dx = no leading zero, or with or without zero when parsing</div>
</li>
<li>
<div>ddd = 3-character abbreviation</div>
</li>
<li>
<div>dddd = full name of day</div>
</li>
</ul>
</li>
</ul>
<h3>Time</h3>
<ul>
<li>
<div>Hour</div>
<ul>
<li>
<div>h or H = no leading zero</div>
</li>
<li>
<div>hh or HH = leading zero</div>
</li>
<li>
<div>hp or HP = leading space</div>
</li>
<li>
<div>hx or HX = leading zero, or with or without leading zero when parsing</div>
</li>
</ul>
</li>
<li>
<div>Minute</div>
<ul>
<li>
<div>m = no leading zero</div>
</li>
<li>
<div>mm = leading zero</div>
</li>
<li>
<div>mp = leading space</div>
</li>
<li>
<div>mx = leading zero, or with or without leading zero when parsing</div>
</li>
</ul>
</li>
<li>
<div>Second</div>
<ul>
<li>
<div>s&nbsp;= no leading zero</div>
</li>
<li>
<div>ss&nbsp;= leading zero</div>
</li>
<li>
<div>sp = leading space</div>
</li>
<li>
<div>sx = leading zero, or with or without leading zero when parsing</div>
</li>
</ul>
</li>
<li>
<div>Millisecond</div>
<ul>
<li>
<div>l&nbsp;= no leading zero</div>
</li>
<li>
<div>ll&nbsp;= leading zero</div>
</li>
<li>
<div>lp = leading space</div>
</li>
<li>
<div>lx = leading zero, or with or without leading zero when parsing</div>
</li>
</ul>
</li>
<li>
<div>Nanosecond</div>
<ul>
<li>
<div>n&nbsp;= no leading zero</div>
</li>
<li>
<div>nn&nbsp;= leading zero</div>
</li>
<li>
<div>np = leading space</div>
</li>
<li>
<div>nx = leading zero, or with or without leading zero when parsing</div>
</li>
</ul>
</li>
<li>
<div>Other</div>
<ul>
<li>
<div>tt = AM/PM</div>
</li>
<li>
<div>? = space, or any character (wildcard) when parsing</div>
</li>
<li>
<div>any other character, not listed above, is listed verbatim&nbsp;</div>
</li>
</ul>
</li>
</ul>
<p>For more about Log Parser, visit <a href="http://LogParserPlus.com">LogParserPlus.com</a>.</p>
