+++
title = "Regular Expression tester - ColdFusion"
summary = "A regular expression tester, built on ColdFusion. [slnet0514:31402614-3e73-435d-b58f-bb146f10b1b2]"
draft = false
comments = true
date = "2008-01-10T22:15:00-06:00"
modified = "2009-12-20T18:14:49-06:00"
slug = "Regular-Expression-tester-ColdFusion"
blogengine = "31402614-3e73-435d-b58f-bb146f10b1b2"
categories = ["tutorials / guides"]
tags = ["coldfusion"]
+++

<p>I stumbled upon some code I had written back in September, for testing regular expressions. This uses ColdFusion, and is currently 'running' on ColdFusion MX 6.1 and ColdFusion 7.0.</p>
<p>It's a pity to not make it available, since it's such an easy template ...</p>
<pre class="code"><code class="coldfusion">&lt;!--- --- ---
DESCRIPTION:
	&nbsp;Basic way to test a regular expression.

CALLED BY:
	???

CALLS:
	???

ASSUMPTIONS:
	???

MODIFICATION HISTORY:
  DATE		USER	ACTION
  09/24/2007	J.Skemp	Created template.

--- --- ---&gt;

&lt;style type="text/css"&gt;
	form {
		margin:0;
		padding:0;
	}
	form label, .label_kludge {
		display:block;
		float:left;
		width:180px;
		padding:0;
		margin:5px 0 0;
		text-align:right;
	}
	form input, form textarea, form select {
		width:200px;
		margin:5px 0 0 10px;
	}
	textarea {
		overflow:auto;
	}
	form br {
		clear:left;
	}
&lt;/style&gt;

&lt;cfparam name="RegularExpression" default="" /&gt;
&lt;cfparam name="TestString" default="" /&gt;
&lt;cfparam name="CaseSensitive" default="off" /&gt;

&lt;h1&gt;The great regular expression testing solution&lt;/h1&gt;
&lt;cfform&gt;
	&lt;label for="RegularExpression"&gt;Regular Expression:&lt;/label&gt;&lt;cfinput type="text" name="RegularExpression" style="width:350px;" value="#RegularExpression#" /&gt;&lt;br /&gt;
	&lt;label for="TestString"&gt;Test String:&lt;/label&gt;&lt;cfinput type="text" name="TestString" style="width:350px;" value="#TestString#" /&gt;&lt;br /&gt;
	&lt;label for="CaseSensitive"&gt;Case Sensitive:&lt;/label&gt;&lt;input type="checkbox" name="CaseSensitive" &lt;cfif CaseSensitive EQ "on"&gt;checked="checked"&lt;/cfif&gt; /&gt;&lt;br /&gt;
	&lt;span class="label_kludge"&gt; &lt;/span&gt;&lt;input type="submit" value="Test" /&gt;
&lt;/cfform&gt;

&lt;cfif RegularExpression NEQ "" AND TestString NEQ ""&gt;
	&lt;cfif CaseSensitive EQ "on"&gt;
		&lt;cfset FindText = REFind(RegularExpression, TestString) /&gt;
	&lt;cfelse&gt;
		&lt;cfset FindText = REFindNoCase(RegularExpression, TestString) /&gt;
	&lt;/cfif&gt;
	&lt;p&gt;Result: &lt;cfif FindText EQ 0&gt;&lt;strong&gt;no&lt;/strong&gt; &lt;/cfif&gt;match found&lt;/p&gt;
&lt;/cfif&gt;</code></pre>
<h3>Updates</h3>
<p>May 4, 2008: Corrected a simple label error.</p>
