+++
title = "AVG 8 setup parameters"
description = "Unfortunately, there doesn't appear to be a master list of parameters that can be passed to disable AVG 8 functionality/features. Here's an attempt at one. [slnet0514:1987c242-6a2d-403a-a420-2434de377f16]"
draft = false
comments = false
date = "2008-06-14T20:30:00-05:00"
modified = "2010-02-10T07:19:36-06:00"
slug = "AVG-8-setup-parameters"
blogengine = "1987c242-6a2d-403a-a420-2434de377f16"
categories = ["software"]
tags = []
+++

<p>AVG is a pretty good piece of anti-virus software.</p>
<p>However, as was recently noticed, it's Link Scanner functionality can be, and is, quite the resource hog.</p>
<p>When running the installation program, it's possible to pass parameters to disable this functionality. However, there's no complete listing of parameters on the site.</p>
<p>In an attempt to make this information&nbsp;easier to find, I include it below.&nbsp;</p>
<blockquote>
<p>installation without Web Shield<br />avg_*.exe /REMOVE_FEATURE fea_AVG_HttpScanner</p>
<p>installation without Personal E-mail Scanner<br />avg_*.exe /REMOVE_FEATURE fea_AVG_EMC</p>
<p>installation without AVG Firewall<br />avg_*.exe /REMOVE_FEATURE fea_AVG_Firewall</p>
<p>In case you do not want the AVG Tray application to start automatically, please use this parameter for the installation:<br />avg_*.exe /NO_CC_STARTUP</p>
<p>installation without Link Scanner<br />avg_*.exe /REMOVE_FEATURE fea_AVG_SafeSurf /REMOVE_FEATURE fea_AVG_SafeSearch</p>
</blockquote>
<div class="tip">
<p>These parameters <em>appear</em> to be only passable to the installer, and not the setup program, that is included in an install's directory.</p>
<p>Additionally, parameters are case-sensitive.</p>
</div>
<p>If the installer was in the root of the C drive, the following example would disable Link Scanner, for AVG Free:</p>
<blockquote>
<p>c:\avg_free_stf_*.exe /REMOVE_FEATURE fea_AVG_SafeSurf /REMOVE_FEATURE fea_AVG_SafeSearch&nbsp;</p>
</blockquote>
<p>(Where the * is replaced by your specific version.)</p>
<p>If you know of parameters not listed here, please post a comment below.</p>
