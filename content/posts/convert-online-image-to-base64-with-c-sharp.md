+++
title = "Convert online image to base64 with C#"
summary = "Code to convert an image online to base64."
draft = false
comments = true
date = "2010-12-12T16:51:00-06:00"
modified = "2010-12-12T17:00:10-06:00"
slug = "Convert-online-image-to-base64-with-C-sharp"
blogengine = "72c819ff-ad10-4dea-a6c4-79515c2b6211"
categories = ["Internet"]
tags = [".net", "c#"]
+++

<p>The following code will convert an online image to a base64 string.</p>
<p>The code was specifically written for use in <a rel="external" href="http://www.linqpad.net/">LINQPad</a>, hence the use of Dump().</p>
<pre class="code"><code class="csharp">String url = "http://ecx.images-amazon.com/images/I/51MVXV3QQ6L._SL500_SS150_.jpg";

Uri uri = new Uri(url);

WebClient client = new WebClient();
byte[] imageBytes = client.DownloadData(uri);

string base64String = Convert.ToBase64String(imageBytes);

base64String.Dump();

base64String.Length.Dump();
("&lt;img src='data:image/jpg;base64," + "' /&gt;").Length.Dump();

client.Dispose();</code></pre>
<p>The length dumps are given to get an idea of what size would be added to a file if added inline.</p>
