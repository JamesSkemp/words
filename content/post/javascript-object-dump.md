+++
title = "JavaScript object dump"
description = "What I've used to dump a JavaScript object to the screen, when I haven't had access to Firebug."
draft = false
comments = true
date = "2010-03-27T06:43:00-05:00"
modified = "2010-03-27T07:04:57-05:00"
slug = "JavaScript-object-dump"
blogengine = "7eafdb1f-0f42-49e8-ac14-34ddae2a48ed"
categories = ["tutorials / guides"]
tags = ["javascript"]
+++

<p>I thought I posted this before, but I guess I did not.</p>
<p>Here's one way to dump a JavaScript object for analysis (if you don't have access to Firebug, or a similar tool).</p>
<p>Note it only dumps one level of data, and the code below is specifically for dumping an exception (catch ex), but swap ex in the <del>three spots</del> <ins>one spot</ins> with whatever object you'd like dumped.</p>
<pre class="code"><code class="jscript">var objectInfo = "";
// Change ex to whatever object you want to debug.
var objectToDebug = ex;
for (var prop in objectToDebug) {
	objectInfo += "property: " + prop + " value: [" + objectToDebug[prop] + "]\n";
}
objectInfo += "toString(): " + " value: [" + objectToDebug.toString() + "]";
alert(objectInfo);</code></pre>
<p>I'm almost positive I found this code (pre-modifications) somewhere, but can't determine where that was (and having emailed myself this in December, lost my browsing history from that time). <ins>I've also updated the code to make use of variables, instead of the old method of adding the object to dump in a total of three spots.</ins></p>
<p><ins>And here's a function:</ins></p>
<pre class="code"><code class="jscript">function dumpObject(o) {
	var objectInfo = "";
	var objectToDebug = o;
	for (var prop in objectToDebug) {
		objectInfo += "property: " + prop + " value: [" + objectToDebug[prop] + "]\n";
	}
	objectInfo += "toString(): " + " value: [" + objectToDebug.toString() + "]";
	alert(objectInfo);
}</code></pre>
