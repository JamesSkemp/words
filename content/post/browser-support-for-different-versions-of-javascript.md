+++
title = "Browser support for different versions of JavaScript"
description = "A look at documentation for support of JavaScript in various main-stream browsers."
draft = false
comments = true
date = "2007-01-19T22:04:00-06:00"
modified = "2007-07-22T19:32:47-05:00"
slug = "Browser-support-for-different-versions-of-JavaScript"
blogengine = "a2423eea-1856-450c-8652-579bc02c2040"
categories = ["software", "Internet"]
tags = ["firefox", "internet explorer", "javascript"]
+++

<p>
After a number of Google searches, I&#39;ve been unable to find a listing of what browsers support what versions of JavaScript.  The few sites I did find were AnyBrowser.com and Mozilla.org.  Unfortunately, the information they provide is pretty focused.  In this article I&#39;ll be going over this information, and trying to dig up more.<!--more--><!--adsense-->
</p>
<p>
<a rel="nofollow" href="http://www.anybrowser.com/javascript.html" onclick="window.open(this.href);return false;">AnyBrowser.com</a> provides information for IE 2 to IE 5, Netscape 2 to Netscape 6, and AOL 3 to 5.  This covers JavaScript 1.3 (IE 5 and AOL 5) and JavaScript 1.4 (Netscape 6).
</p>
<p>
<a rel="nofollow" href="http://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Reference:About" onclick="window.open(this.href);return false;">Mozilla.org</a> provides information for JavaScript 1.0 to JavaScript 1.7, but only for Netscape and Mozilla/Firefox.  JavaScript 1.5 is Navigator 6 and Mozilla 0.6x-0.9x, JavaScript 1.6 is Firefox 1.5, and JavaScript 1.7 is Firefox 2.
</p>
<div class="note">
<p>
Interestingly, JavaScript 1.4 is listed as n/a on Mozilla, and Netscape 6 under JavaScript 1.5, but AnyBrowser has 6 under 1.4 ...
</p>
</div>
<p>
Using the Web as my guide, I&#39;ve determined two ways that I believe will test for JavaScript 1.6 and JavaScript 1.7 support, based upon the following two pages.
</p>
<ul>
	<li><a rel="nofollow" href="http://developer.mozilla.org/en/docs/New_in_JavaScript_1.6" onclick="window.open(this.href);return false;">http://developer.mozilla.org/en/docs/New_in_JavaScript_1.6</a></li>
	<li><a rel="nofollow" href="http://developer.mozilla.org/en/docs/New_in_JavaScript_1.7" onclick="window.open(this.href);return false;">http://developer.mozilla.org/en/docs/New_in_JavaScript_1.7</a></li>
</ul>
<p>
For JavaScript 1.6, I&#39;ll be using the following code snippet.
</p>
<blockquote>
	<p>
	var num = 15;<br />
	document.write(String.replace(num, /5/, &#39;2&#39;) + &quot; (should be &#39;12&#39;)&lt;br /&gt;\n&quot;);
	</p>
</blockquote>
<p>
For JavaScript 1.7, I&#39;ll be using this code, as well as the previous code.
</p>
<blockquote>
	<p>
	var x = 5;<br />
	var y = 0;<br />
	document.write( let(x = x + 10, y = 12) x+y + &quot; (should be &#39;27&#39;)&lt;br /&gt;\n&quot;);<br />
	document.write(x+y + &quot;&lt;br /&gt;\n&quot;);
	</p>
</blockquote>
<p>
The testing page is available on my <a href="http://strivinglife.cfdeveloper.co.uk/javascript_text.cfm" onclick="window.open(this.href);return false;">CFDeveloper site</a>.
</p>
<p>
First, if you know of any code that I can use to test JavaScript 1.5 and 1.4 support, please post or email to me, so I can add that to my testing page.
</p>
<p>
Second, if you can test a different browser/version, please also post your results.
</p>
<h4>Testing results</h4>
<p>
My testing of Firefox 2.0.0.1, Internet Explorer 7.0.5730.11, and Opera 9.10.  Since the current version of Netscape uses either IE or FF for rendering, I&#39;ve skipped any testing of it.
</p>
<p>
<strong>Firefox 2.0.0.1</strong> displays one line for JavaScript 1.5 and less.  These are simple document.write()s, so they should display in most browsers.  Version information is passed through language, not the type, and the type is text/javascript.  In addition, it displays the scripts for 1.6 and 1.7 whether the type is text/javascript or application/javascript, and the version is stated.  For 1.6, it doesn&#39;t display the 1.7 code if the type is text/javascript, with no version.  It does for 1.6.  So, 1.6 has three groups of two lines, while 1.7 has two groups of four lines.  From what I can tell, this is expected behaviour.
</p>
<p>
<strong>Internet Explorer 7.0.5730.11</strong> and <strong>Opera 9.10</strong> have the same display for this page.  Through JavaScript 1.5, they each have one line for each - which is to be expected.  For 1.6, they have a single line, which is the first, and simple, document.write() of some text.  No version is passed, and the type is set to text/javascript.  At this point, nothing else is displayed.  For 1.7, nothing is displayed.
</p>
<p>
If, for 1.6, we change &lt;script language=&quot;javascript1.6&quot; type=&quot;text/javascript&quot;&gt; to &lt;script language=&quot;javascript1.6&quot; type=&quot;application/javascript&quot;&gt;, only Opera keeps the initial document.write for 1.6.  Internet Explorer displays nothing under the 1.6 heading.
</p>
<h4>Current conclusions</h4>
<p>
Based upon this initial testing, it appears that application/javascript, and setting the version in the type, is not supported by the current version of Internet Explorer.  In addition, Firefox is the only one of the three browsers tested that supports up to JavaScript 1.7.  Based upon how IE and Opera behaved with the JavaScript 1.6 test, I&#39;d say that there is no support for 1.6 features, but that doesn&#39;t stop them from giving it a go.  If they run into a problem, they appear to quit looking through the script block.
</p>
<p>
I&#39;d be very interested in documentation regarding this, so if you know more, please do post what you can share.
</p>

