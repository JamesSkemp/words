+++
title = "Interesting feature with parsing XML with jQuery on Safari"
summary = "Interesting results on parsing XML with jQuery on current versions of various browsers."
draft = false
comments = true
date = "2011-03-27T20:39:00-05:00"
modified = "2011-03-28T19:54:01-05:00"
slug = "Interesting-feature-with-parsing-XML-with-jQuery-on-Safari"
blogengine = "c52444bf-6521-435b-bece-b4fe00c426d5"
categories = ["article", "Internet", "software"]
tags = ["html", "jquery", "xml"]
+++

<p>I've been playing around with HTML5 quite a bit recently, in particular with offline Web applications.</p>
<p>My second experiment (my first is on pause) was with making <a rel="external" href="http://media.jamesrskemp.com/xml/video_games.xml">my video games</a> available, so that I can access the listing when I'm out shopping at used game stores.</p>
<p>It's still in progress, but you can see my <a rel="external" href="http://media.jamesrskemp.com/xmlHtml/video_games.html">offline listing of video games</a> now.</p>
<p>My main intention is to make this available on my iPod Touch, so I was a bit dismayed when I found that the listing didn't display the title of the game. Everything else displayed just fine, but not the titles. Naturally, after some searching about I posted my question to Stack Overflow - <a rel="external" href="http://stackoverflow.com/questions/5427259/xmldocument-via-jquery-ajax-call-stored-as-string-in-localstorage-results-in-sa">XMLDocument (via jQuery ajax call) stored as string in localStorage results in Safari not finding title elements</a>.</p>
<p>After further research, it looks like I was missing a parseXML call, which results in the data correctly being pulled/displayed in Safari.</p>
<p>I decided to do some further testing on this issue, and I believe I've discovered why it's displaying as it is.</p>
<h3>The test code</h3>
<p>I created a bit of test code - <a href="http://jamesrskemp.com/testing/jQueryXmlParsing.html">jQuery XML parsing</a> - and that I've posted below.</p>
<pre class="code"><code class="html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;title&gt;jQuery XML Parsing testing - JamesRSkemp.com&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
	&lt;h1&gt;jQuery XML Parsing testing&lt;/h1&gt;
	&lt;p&gt;The following test code was created to test Internet Explorer 9, Chrome 10, Firefox 4, Opera 11, Safari 5 (Windows), and Safari on iOS 4.3. Read more in &lt;a href="http://strivinglife.com/words/post/Interesting-feature-with-parsing-XML-with-jQuery-on-Safari.aspx" rel="external"&gt;Interesting feature with parsing XML with jQuery on Safari&lt;/a&gt;.&lt;/p&gt;
	&lt;noscript&gt;You must have JavaScript enabled to view this test.&lt;/noscript&gt;
	&lt;div id="TestOutput"&gt;&lt;/div&gt;
	&lt;script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.5.1/jquery.min.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript"&gt;
		// We'll store an example of an XML file as a string of text.
		var xmlContent = "&lt;?xml version='1.0'?&gt;&lt;Books&gt;&lt;Book&gt;&lt;Title&gt;Book 1&lt;/Title&gt;&lt;Author&gt;Book 1 Author&lt;/Author&gt;&lt;/Book&gt;&lt;Book&gt;&lt;Title&gt;Book 2&lt;/Title&gt;&lt;Author&gt;Book 2 Author&lt;/Author&gt;&lt;/Book&gt;&lt;Book&gt;&lt;Title&gt;Book 3&lt;/Title&gt;&lt;Author&gt;Book 3 Author&lt;/Author&gt;&lt;/Book&gt;&lt;Book&gt;&lt;Title&gt;Book 4&lt;/Title&gt;&lt;Author&gt;Book 4 Author&lt;/Author&gt;&lt;/Book&gt;&lt;Book&gt;&lt;Title&gt;Book 5&lt;/Title&gt;&lt;Author&gt;Book 5 Author&lt;/Author&gt;&lt;/Book&gt;&lt;/Books&gt;";
		var testOutputText = "";

		var simpleCall = $(xmlContent);
		var simpleParse = $.parseXML(xmlContent);
		var parse = $($.parseXML(xmlContent));

		try {
			testOutputText += "Type of $(xmlContent): " + typeof simpleCall + "&lt;br /&gt;";
			testOutputText += "To string: " + simpleCall.toString() + "&lt;br /&gt;";
			testOutputText += "Length: " + simpleCall.length + "&lt;br /&gt;";
			if (typeof simpleCall === 'object') {
				for (var prop in simpleCall) {
					//testOutputText += "	property: " + prop + " value: [" + simpleCall[prop] + "]\n";
				}
			}
			simpleCall.find("Book").each(function () {
				testOutputText += "&lt;em&gt;" + $(this).find('Title').text() + "&lt;/em&gt; by " + $(this).find("Author").text() + "&lt;br /&gt;";
			});
		} catch (e) {
			testOutputText += "&lt;span style='color:red;'&gt;There was an error processing at this point.&lt;/span&gt;&lt;br /&gt;";
		}

		try {
			testOutputText += "Type of $.parseXML(xmlContent): " + typeof simpleParse + "&lt;br /&gt;";
			testOutputText += "To string: " + simpleParse.toString() + "&lt;br /&gt;";
			testOutputText += "Length: " + simpleParse.length + "&lt;br /&gt;";
			if (typeof simpleParse === 'object') {
				for (var prop in simpleParse) {
					//testOutputText += "	property: " + prop + " value: [" + simpleParse[prop] + "]\n";
				}
			}
			simpleParse.find("Book").each(function () {
				testOutputText += "&lt;em&gt;" + $(this).find('Title').text() + "&lt;/em&gt; by " + $(this).find("Author").text() + "&lt;br /&gt;";
			});
		} catch (e) {
			testOutputText += "&lt;span style='color:red;'&gt;There was an error processing at this point.&lt;/span&gt;&lt;br /&gt;";
		}

		try {
			testOutputText += "Type of $($.parseXML(xmlContent)): " + typeof parse + "&lt;br /&gt;";
			testOutputText += "To string: " + parse.toString() + "&lt;br /&gt;";
			testOutputText += "Length: " + parse.length + "&lt;br /&gt;";
			if (typeof parse === 'object') {
				for (var prop in parse) {
					//testOutputText += "	property: " + prop + " value: [" + simpleParse[prop] + "]\n";
				}
			}
			parse.find("Book").each(function () {
				testOutputText += "&lt;em&gt;" + $(this).find('Title').text() + "&lt;/em&gt; by " + $(this).find("Author").text() + "&lt;br /&gt;";
			});
		} catch (e) {
			testOutputText += "&lt;span style='color:red;'&gt;There was an error processing at this point.&lt;/span&gt;&lt;br /&gt;";
		}

		$('#TestOutput').append(testOutputText);
	&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
<h3>What the test does</h3>
<p>I did a couple of things with this test.</p>
<p>First, I created a string with the following XML, and saved it as xmlContent.</p>
<pre class="code"><code class="xml">&lt;?xml version='1.0'?&gt;
&lt;Books&gt;
	&lt;Book&gt;
		&lt;Title&gt;Book 1&lt;/Title&gt;
		&lt;Author&gt;Book 1 Author&lt;/Author&gt;
	&lt;/Book&gt;
	&lt;Book&gt;
		&lt;Title&gt;Book 2&lt;/Title&gt;
		&lt;Author&gt;Book 2 Author&lt;/Author&gt;
	&lt;/Book&gt;
	&lt;Book&gt;
		&lt;Title&gt;Book 3&lt;/Title&gt;
		&lt;Author&gt;Book 3 Author&lt;/Author&gt;
	&lt;/Book&gt;
	&lt;Book&gt;
		&lt;Title&gt;Book 4&lt;/Title&gt;
		&lt;Author&gt;Book 4 Author&lt;/Author&gt;
	&lt;/Book&gt;
	&lt;Book&gt;
		&lt;Title&gt;Book 5&lt;/Title&gt;
		&lt;Author&gt;Book 5 Author&lt;/Author&gt;
	&lt;/Book&gt;
&lt;/Books&gt;</code></pre>
<p>Next I created three variables, storing different things. First, I did $(xmlContent), then $.parseXML(xmlContent), and finally $($.parseXML(xmlContent)).</p>
<h3>The results</h3>
<p>Interestingly, on IE 9, Chrome 10, Firefox 4, Opera 11, Safari 5 (Windows), the first and third tests return the type of <strong>object Object</strong>.</p>
<p>For the second test we have <strong>object Document</strong> on IE 9, Chrome 10, Safari 5, and Safari on iOS 4.3, and <strong>object XMLDocument</strong> on Firefox 4 and Opera 11.</p>
<p>But for the first test, while we have a length of <em>2</em> on IE 9, Chrome 10, Firefox 4, and Opera 11, we only have a length of 1 on Safari 5 and Safari on iOS 4.3.</p>
<p>The fix, then, is to make sure to use the last of the three, but it seems odd that this wouldn't work on only one of the tested browsers.</p>
