+++
title = "Enabling PHP file_put_contents() support on IIS 7.5 on Windows Server 2008 R2"
summary = "To save content on Windows Server 2008 R2 using PHP on IIS 7.5, make sure the necessary user has permission."
draft = false
comments = true
date = "2010-09-01T21:20:00-05:00"
modified = "2010-09-01T21:30:33-05:00"
slug = "Enabling-PHP-file_put_contents-support-on-IIS-75-on-Windows-Server-2008-R2"
blogengine = "a39eb027-76a5-41fa-87d4-d5cf339bf22c"
categories = ["software"]
tags = ["iis", "windows server 2008 r2", "php"]
+++

<p>I've already installed the current verison of PHP 5.2 on my Windows Server 2008 R2 machine, but unfortunately wasn't able to get content saved via the file_put_contents function.</p>
<p>It seems that you need to add and give IUSR the necessary permissions on the file (or directory) in order for writes to work properly.</p>
