+++
title = "Script to simplify Netflix activity pages (in progress)"
summary = "I love Netflix, but there's no easy way to get a listing of the movies I've rated through the service. To ease with that, I've finally started on a script that will clean the Netflix output, so it's a bit easier to parse."
draft = false
comments = true
date = "2012-03-18T16:11:00-05:00"
modified = "2012-03-18T16:16:34-05:00"
slug = "Script-to-simplify-Netflix-activity-pages"
blogengine = "e3a21182-9818-415e-a8f9-0eec2efb3a6b"
categories = ["tutorials / guides"]
tags = ["netflix", "chrome"]
+++

<p>I love Netflix, but there's no easy way to get a listing of the movies I've rated through the service.</p>
<p>To ease with that, I've finally started on a script that will clean the Netflix output, so it's a bit easier to parse.</p>
<p>Fire up Chrome, visit either&nbsp;https://www2.netflix.com/RentalActivity?all=true or&nbsp;https://account.netflix.com/WiViewingActivity?all=true, open a console, and use the following two scripts:</p>
<h3>Script 1: Load jQuery</h3>
<pre class="code"><code class="js">var GM_JQ = document.createElement('script'); 
GM_JQ.src = 'https://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js';
GM_JQ.type = 'text/javascript'; 
document.getElementsByTagName('head')[0].appendChild(GM_JQ);</code></pre>
<h3>Script 2: Remove rating graphics</h3>
<pre class="code"><code class="js">$('.stbrIl').hide();
$('.stbrMaskFg').css('background-image', 'none').css('text-indent', '0').css('width', '200px').css('vertical-aign', 'middle');
$('.stbrMaskBg').css('background-image', 'none');</code></pre>
<p>There's still work to be done, but it's a sufficient start. I've thought about a user script, and might implement that once this is done.</p>
