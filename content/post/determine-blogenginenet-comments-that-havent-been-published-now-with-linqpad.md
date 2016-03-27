+++
title = "Determine BlogEngine.NET comments that haven't been published - with LINQPad"
description = "Find all BlogEngine.NET posts with unapproved comments using this code and LINQPad."
draft = false
comments = true
date = "2009-12-31T14:20:00-06:00"
modified = "2009-12-31T14:27:33-06:00"
slug = "Determine-BlogEngineNET-comments-that-havent-been-published-now-with-LINQPad"
blogengine = "1172a040-9649-43de-9ce9-04c111d8cac5"
categories = ["tutorials / guides"]
tags = ["blogengine.net", "c#", "linq to xml", "xml", "linqpad"]
+++

<p>At the beginning of the month I wrote a post on <a href="http://strivinglife.com/words/post/Determine-BlogEngineNET-comments-that-havent-been-published.aspx">how to find BlogEngine.NET comments that had not yet been published/approved</a>.</p>
<p>Having purchased a copy of <a rel="external" href="http://linqpad.net/">LINQPad</a> a short while ago (autocompletion costs, the program with all other functionality does not; give it a try if you develop in .NET - it's <em>very</em> cool), and having got slammed this morning with some spammer who had an hour to kill, I decided to adapt my code for LINQPad.</p>
<pre class="code"><code class="csharp">string postsDirectory = @"C:\posts";

string[] postFiles = System.IO.Directory.GetFiles(postsDirectory);

DataTable comments = new DataTable();
	comments.Columns.Add("Post");
	comments.Columns.Add("CommentApproved");
	comments.Columns.Add("FileId");
	comments.Columns.Add("IpAddress");

XDocument postXml;

foreach (string postFile in postFiles) {
	postXml = XDocument.Load(postFile);

	var posts = from postData in postXml.Descendants("post")
		select new {
			Title = postData.Element("title").Value,
			CommentItems = (from commentItems in postData.Element("comments").Elements("comment")
				select commentItems).ToList()
		};

	foreach (var post in posts) {
		if (post.CommentItems.Count &gt; 0) {
			foreach (var commentItem in post.CommentItems) {
				if (commentItem.Attribute("approved") != null &amp;&amp; commentItem.Attribute("approved").Value == "False") {
					DataRow comment = comments.NewRow();
					comment["Post"] = post.Title;
					comment["CommentApproved"] = commentItem.Attribute("approved").Value;
					comment["IpAddress"] = commentItem.Element("ip").Value;
					comment["FileId"] = "/post.aspx?id=" + System.IO.Path.GetFileNameWithoutExtension(postFile);
					comments.Rows.Add(comment);
				}
			}

		}
	}
}

postXml = null;

comments.Dump();</code></pre>
<p>You'll want to change postsDirectory accordingly.</p>
<p>This will output all unapproved comments, the post they are associated with, the post GUID, and the commentor's IP address.</p>
<p>It's relatively easy to expand this to display more or less information, as desired. For example, <strong>website</strong> and <strong>author</strong> can be swapped in in place of <strong>ip</strong> in the last foreach.</p>
<p>Comments/questions/etcetera welcome and appreciated.</p>
