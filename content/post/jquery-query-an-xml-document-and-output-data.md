+++
title = "jQuery: Query an Xml document and output data"
description = "jQuery to pull data from an Xml file, and add it to the page."
draft = false
comments = true
date = "2009-05-03T21:11:00-05:00"
modified = "2009-10-15T07:31:48-05:00"
slug = "jQuery-Query-an-Xml-document-and-output-data"
blogengine = "8922118c-44ef-41fc-bc80-5be258af1a33"
categories = ["StrivingLife", "tutorials / guides"]
tags = ["jquery", "xml"]
+++

<p>I back-dated my first piece of jQuery code, but have decided not to with my second.</p>
<p>Anyways, I had a hard time finding code, written in jQuery, to pull data from an Xml file and add it to a page. Combining a couple of tutorials online, I created the following (on April 27).</p>
<p>This was for a message, so I started out with the Xml file, creating something like this:</p>
<pre class="code"><code class="xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;messages&gt;
	&lt;system&gt;&lt;![CDATA[Test system message.]]&gt;&lt;/system&gt;
&lt;/messages&gt;</code></pre>
<p>I wanted multiple messages to be able to be stored, hence the format.&nbsp;</p>
<p>Next I had to create the code to pull in the message that I wanted.</p>
<pre class="code"><code class="html">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head&gt;
	&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
	&lt;title&gt;Untitled Document&lt;/title&gt;
	&lt;script type="text/javascript" src="jquery-1.3.2.min.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript"&gt;
		try {
			$(document).ready(function(){
				$.ajax({
					type: 'GET',
					url: 'message.xml',
					dataType: 'xml',
					processData: false,
					success: function(data,message) {$('#wrapper')
						.append('&lt;div id="systemMessage"&gt;' + $(data).find('messages system').text() + '&lt;/div&gt;');}
				});
			});
		} catch (ex) {}
	&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
	&lt;div id="wrapper"&gt;
	&lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
<p>This is where it got tricky, since I couldn't find code that did this, just a number of individual pieces of it. Putting it all together, it worked as I wanted.</p>
<p>We needed to refresh the content as well, and with the help of a plug-in, we were able to make this data call when we wanted (on a timer) and refresh the contents of the div as appropriate.</p>
