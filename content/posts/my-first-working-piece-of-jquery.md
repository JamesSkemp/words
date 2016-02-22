+++
title = "My first, working, piece of jQuery"
summary = "The first piece of jQuery that I wrote. Woohoo."
draft = false
comments = true
date = "2009-04-23T19:00:00-05:00"
modified = "2009-10-15T07:26:41-05:00"
slug = "My-first-working-piece-of-jQuery"
blogengine = "88562486-6c13-4b36-9155-30c631bcc569"
categories = ["StrivingLife"]
tags = ["jquery"]
+++

<p>This is the first piece of jQuery that I wrote, for production use, that works exactly as I'd like it to. Some code has been changed.</p>
<pre class="code"><code class="js">try {
	$(document).ready(function(){
		$('div#headerLogin')
			.prepend($(document.createElement('div'))
			.addClass('headerLoggedIn')
			.append('Logged in as: &lt;span&gt;&lt;cfoutput&gt;#query.displayName#&lt;/cfoutput&gt;&lt;/span&gt; &lt;span&gt;&lt;a href="/logout/"&gt;logout&lt;/a&gt;&lt;/span&gt;')
		);
		$('div.headerLoggedIn')
			.after('&lt;span&gt;Hello&lt;cfif IsDefined("query.first_name") AND Trim(query.first_name) NEQ ""&gt;, &lt;cfoutput&gt;#query.first_name#&lt;/cfoutput&gt;&lt;/cfif&gt;&lt;/span&gt;');
	});
} catch (ex) {}</code></pre>
<p>It's for a site that runs ColdFusion, hence the CF tags.</p>
<p>Basically it finds the div with an id of headerLogin and adds to that a new div, with a class and some text. Then additional text is added to that new div.</p>
<p>Pretty simple, but ...</p>
