+++
title = "Function to Parse a Microsoft JSON DateTime returned from a WCF service in JavaScript"
summary = "A simple function to convert a Microsoft WCF JSON DateTime to a format we can use within JavaScript."
draft = false
comments = true
date = "2010-07-04T14:57:00-05:00"
modified = "2010-07-04T15:26:47-05:00"
slug = "Parsing-Microsoft-JSON-DateTime-from-WCF-service"
blogengine = "4f64570a-6182-417a-a8d5-6760a0fdbee1"
categories = ["tutorials / guides"]
tags = ["javascript", "wcf", "wcf webhttp", "json"]
+++

<p>When a DateTime is converted to JSON in a WCF Web service (WebHttp in this particular case) it's semi-difficult to convert that to something we can use when we return the date to a client via JavaScript. For example:</p>
<pre><code>"LastPlayed":"\/Date(1278187099000-0400)\/"</code></pre>
<p>After almost an hour of research and goofing around with this, I've come up with the following, which seems to work just fine on Internet Explorer 8, Firefox 3.6, and Chrome 5.0.</p>
<pre class="code"><code class="js">function parseMicrosoftJsonDateTime(content) {
	try {
		content = content.replace(/\//g, '');
		var contentDate = eval('new ' + content);
		return contentDate.toDateString() + ' ' + contentDate.toTimeString();
	} catch (ex) {
		return content;
	}
}</code></pre>
<p>As you can see if it fails at any point I just return whatever was passed. Otherwise since the only thing bothering us are the two /s, I'm first removing all of those. Then I'm creating a new variable, which ends up call new Date(x). This date variable can then be converted to a string via standard JavaScript functionality.</p>
<p>There may be a better way to handle this, but this is fairly quick, and works just as I need it to.</p>
<h3>Sample outputs</h3>
<p>Internet Explorer 8: Sat Jul 3 2010 14:58:18 CDT</p>
<p>Chrome 5.0 and Firefox 3.6: Sat Jul 03 2010 14:58:18 GMT-0500 (Central Daylight Time)</p>
