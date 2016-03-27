+++
title = "Referring to JavaScript documentation in Visual Studio via reference"
description = "How to add a reference to a VSDOC file within Visual Studio for improved Intellisense."
draft = false
comments = true
date = "2010-07-03T13:32:00-05:00"
modified = "2010-07-03T14:07:10-05:00"
slug = "Referring-to-JavaScript-documentation-in-Visual-Studio-via-reference"
blogengine = "9b832525-0219-41bb-a265-40baffe73ee0"
categories = ["tutorials / guides"]
tags = ["visual studio", "jquery"]
+++

<p>While I don't use Microsoft or Google's CDNs for jQuery, I do have a separate sub-domain where I serve these files from (and will eventually use a CDN, I'm sure). However, this means that in Visual Studio I miss out on the helpful documentation functionality.</p>
<p>Based on a comment on <a rel="external" href="http://encosia.com/2008/12/10/3-reasons-why-you-should-let-google-host-jquery-for-you/">3 reasons why you should let Google host jQuery for you</a> it turns out there's a fairly easy way to get Intellisense; simply include the following in your JavaScript file.</p>
<pre class="code"><code class="js">/// &lt;Reference Path="/Scripts/jquery-1.4.1-vsdoc.js"/&gt;</code></pre>
<p>You'll probably want a copy stored locally so that you can use this without the extra traffic.</p>
