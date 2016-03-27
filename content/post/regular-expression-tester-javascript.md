+++
title = "Regular Expression tester - JavaScript"
description = "A JavaScript-based regular expression tester? Yup. [slnet0514:0208a137-2b45-4ef2-85f9-4d8b8bb722d2]"
draft = false
comments = true
date = "2008-01-21T18:15:00-06:00"
modified = "2011-08-05T16:17:47-05:00"
slug = "Regular-Expression-tester-JavaScript"
blogengine = "0208a137-2b45-4ef2-85f9-4d8b8bb722d2"
categories = ["tutorials / guides"]
tags = ["javascript"]
+++

<p>In a previous post, I posted the code I used for <a href="/words/post/Regular-Expression-tester-ColdFusion.aspx">a ColdFusion regular expression tester</a>.</p>
<p>This time I've got an attempt at a JavaScript version. There's a number of TODOs, but ...</p>
<pre class="code"><code class="html">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
 &nbsp;"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
 &lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
 &lt;head&gt;
 &lt;meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" /&gt;
 &lt;title&gt;JavaScript Regular Expression Tester&lt;/title&gt;
 &lt;style type="text/css"&gt;
 &nbsp;#form_help {
 &nbsp;&nbsp;float:right;
 &nbsp;&nbsp;font-size:.8em;
 &nbsp;&nbsp;width:50%;
 &nbsp;}
 &nbsp;#form_results {
 &nbsp;&nbsp;margin:1em;
 &nbsp;&nbsp;width:45%;
 &nbsp;}
 &nbsp;.highlight {
 &nbsp;&nbsp;background-color:#ff9;
 &nbsp;}
 &nbsp;#form_highlighttext {
 &nbsp;&nbsp;border:1px dashed #ccc;
 &nbsp;&nbsp;margin-left:1em;
 &nbsp;&nbsp;width:45%;
 &nbsp;}
 &lt;/style&gt;
 &lt;script type="text/javascript"&gt;
 &nbsp;function RemoveHTML(TextContent) {
 &nbsp;&nbsp;var str = '';
 &nbsp;&nbsp;str = TextContent;
 &nbsp;&nbsp;str = str.replace(/&lt;/g, "&amp;lt;");
 &nbsp;&nbsp;
 &nbsp;&nbsp;return str;
 &nbsp;}
 &nbsp;function TestExpression() {
 &nbsp;&nbsp;var Expression = '';
 &nbsp;&nbsp;var ExpressionParameters = 'gm';
 &nbsp;&nbsp;var ExpressionText = '';
 &nbsp;&nbsp;try {
 &nbsp;&nbsp;&nbsp;document.getElementById('form_error').innerHTML = '';
 &nbsp;&nbsp;&nbsp;document.getElementById('form_results').innerHTML = '';
 &nbsp;&nbsp;&nbsp;document.getElementById('form_highlighttext').innerHTML = '';
 &nbsp;&nbsp;&nbsp;if (document.getElementById('InputExpression').value != '' &amp;&amp; document.getElementById('InputText').value != '') {
 &nbsp;&nbsp;&nbsp;&nbsp;// TODO better check and error writing - use span with _s
 &nbsp;&nbsp;&nbsp;&nbsp;if (document.getElementById('CheckCase').checked) {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ExpressionParameters += 'i';
 &nbsp;&nbsp;&nbsp;&nbsp;}
 &nbsp;&nbsp;&nbsp;&nbsp;Expression = document.getElementById('InputExpression').value;
 &nbsp;&nbsp;&nbsp;&nbsp;ExpressionText = document.getElementById('InputText').value;
 &nbsp;&nbsp;&nbsp;&nbsp;var ExpressionObject = new RegExp(Expression, ExpressionParameters);
 &nbsp;&nbsp;&nbsp;&nbsp;var ExpressionTest = ExpressionObject.test(ExpressionText);
 &nbsp;&nbsp;&nbsp;&nbsp;if (ExpressionTest == true) {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_results').innerHTML = '&lt;p&gt;The following results were found for your search:&lt;/p&gt;';
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// Testing it appears to run it, so ...
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ExpressionObject = new RegExp(Expression, ExpressionParameters);
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;var StringPosition = 0;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;var LastPosition = 0;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;var CountResults = 0;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;var ExpressionResults = ExpressionObject.exec(ExpressionText);
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (ExpressionObject.global) {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;while (ExpressionResults != null) {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_results').innerHTML += '' + RemoveHTML(ExpressionResults[0]) + ' (' + ExpressionResults.index + ' - ' + ExpressionObject.lastIndex + ')' + '&lt;br /&gt;';
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (CountResults == 0) {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;StringPosition = 0;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;} else {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;StringPosition = LastPosition;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_highlighttext').innerHTML += RemoveHTML(ExpressionText.substring(StringPosition, ExpressionResults.index)) + '&lt;span class="highlight"&gt;' + RemoveHTML(ExpressionText.substring(ExpressionResults.index, ExpressionObject.lastIndex)) + '&lt;/span&gt;';
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LastPosition = ExpressionObject.lastIndex;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ExpressionResults = ExpressionObject.exec(ExpressionText);
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CountResults++;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (LastPosition &amp;&amp; LastPosition &lt; ExpressionText.length) {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_highlighttext').innerHTML += RemoveHTML(ExpressionText.substring(LastPosition, ExpressionText.length));
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;} else {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// TODO
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_results').innerHTML += '' + ExpressionResults[0] + ' (' + ExpressionResults.index + ')' + '&lt;br /&gt;';
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_results').innerHTML += '&lt;br /&gt;&lt;br /&gt;';
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//document.getElementById('form_highlighttext').innerHTML += ExpressionText.substring(StringPosition, ExpressionResults.index) + '&lt;span class="highlight"&gt;' + ExpressionResults + '&lt;/span&gt;';
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
 &nbsp;&nbsp;&nbsp;&nbsp;} else {
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_error').innerHTML = 'No match found.';
 &nbsp;&nbsp;&nbsp;&nbsp;}
 &nbsp;&nbsp;&nbsp;} else {
 &nbsp;&nbsp;&nbsp;&nbsp;document.getElementById('form_error').innerHTML = 'You must enter both an expression and text to check that expression against.';
 &nbsp;&nbsp;&nbsp;}
 &nbsp;&nbsp;&nbsp;return false;
 &nbsp;&nbsp;} catch(e) {
 &nbsp;&nbsp;&nbsp;alert(e.message);
 &nbsp;&nbsp;}
 &nbsp;}
 &lt;/script&gt;
 &lt;/head&gt;
 &lt;body&gt;
 &nbsp;&lt;div id="form_help"&gt;
 &nbsp;&nbsp;&lt;p&gt;Regular expression notation:&lt;/p&gt;
 &nbsp;&nbsp;&lt;ul&gt;
 &nbsp;&nbsp;&nbsp;&lt;li&gt;\b = Word boundary&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;\B = Word nonboundary&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;\d = Numeral (0-9)&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;\D = Nonnumeral&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;\s = Single whitespace&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;\S = Single nonwhitespace&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;\w = Letter, numeral, underscore&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;\W = Not \w&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;. = Any character except newline&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;[] = Any character(s) in brackets&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;[^] = Not []&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;* = Preceding zero or more times&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;? = Preceding zero or one time&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;+ = Precending one or more times&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;{&lt;em&gt;n&lt;/em&gt;} = The preceding &lt;em&gt;n&lt;/em&gt; times&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;{&lt;em&gt;n&lt;/em&gt;,} = &lt;em&gt;n&lt;/em&gt; or more times &lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;{&lt;em&gt;n&lt;/em&gt;,&lt;em&gt;m&lt;/em&gt;}= At least &lt;em&gt;n&lt;/em&gt;, at most &lt;em&gt;m&lt;/em&gt;, times&lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;^ = Beginning of the string or line &lt;/li&gt;
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;li&gt;$ = End of the string or line &lt;/li&gt;
 &nbsp;&nbsp;&lt;/ul&gt;
 &nbsp;&lt;/div&gt;
 &nbsp;&lt;form onsubmit="return false;"&gt;
 &nbsp;&nbsp;&lt;label for="InputExpression"&gt;Regular expression:&lt;/label&gt;&lt;input type="text" id="InputExpression" value="" /&gt;&lt;br /&gt;
 &nbsp;&nbsp;&lt;label for="CheckCase"&gt;Ignore case:&lt;/label&gt;&lt;input type="checkbox" id="CheckCase" /&gt;&lt;br /&gt;
 &nbsp;&nbsp;&lt;textarea cols="50" id="InputText" rows="5"&gt;Hello and welcome. I do hope you'll come again. Will you?&lt;/textarea&gt;&lt;br /&gt;
 &nbsp;&nbsp;&lt;input type="button" onclick="TestExpression();" value="Test expression" /&gt;
 &nbsp;&lt;/form&gt;
 &nbsp;&lt;div id="form_error" style="color:red;"&gt;&lt;/div&gt;
 &nbsp;&lt;div id="form_results"&gt;&lt;/div&gt;
 &nbsp;&lt;div id="form_highlighttext"&gt;&lt;/div&gt;
 &lt;/body&gt;
 &lt;/html&gt;</code></pre>
<p>As always, comments appreciated.</p>
