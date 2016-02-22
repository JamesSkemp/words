+++
title = "ColdFusion: cfscript to determine if variable exists and output html-escaped"
summary = "Snippet of ColdFusion to determine if a particular variable exists and if it does, return a trimmed, HTML-escaped, version."
draft = false
comments = true
date = "2009-10-08T20:45:00-05:00"
modified = "2009-12-20T17:59:50-06:00"
slug = "ColdFusion-cfscript-to-determine-if-variable-exists-and-output-html-escaped"
blogengine = "064a48e0-ead7-4540-90df-94b475b72224"
categories = ["article"]
tags = ["coldfusion"]
+++

<p>There may be an easier way to do this in ColdFusion, but I finally created a function to determine whether a variable exists and if it does, returns in, all html-escaped.</p>
<pre class="code"><code class="coldfusion">&lt;cfscript&gt;
	// Checks the passed CF variable to see if it exists, and if it does, outputs a trimmed and html-ready version of the value.
	function checkForValueOutput(data) {
		if (IsDefined(data)) {
			return HtmlEditFormat(Trim(Evaluate(data)));
		} else {
			return "";
		}
	}
&lt;/cfscript&gt;</code></pre>
<p>(Obviously, this can rather easily be converted to a function.)</p>
<p>This results in a change from:</p>
<pre class="code"><code class="xml">&lt;input type="text" id="someField" name="someField"&nbsp;value="&lt;cfif IsDefined("FORM.someField") AND Trim(FORM.someField) NEQ ""&gt;&lt;cfoutput&gt;#HtmlEncodedFormat(Trim(FORM.someField))#&lt;/cfoutput&gt;&lt;/cfif&gt;" /&gt;</code></pre>
<p>To:</p>
<pre class="code"><code class="xml">&lt;input type="text" id="someField" name="someField"&nbsp;value="&lt;cfoutput&gt;#checkForValueOutput("FORM.someField")#&lt;/cfoutput&gt;" /&gt;</code></pre>
<p>Much easier to read, and much shorter.</p>
