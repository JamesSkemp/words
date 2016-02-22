+++
title = "Determine BlogEngine.NET comments that haven't been published"
summary = "C# code to parse a directory of BlogEngine.NET posts (determined by the user selecting one) for unapproved comments."
draft = false
comments = true
date = "2009-12-06T15:55:00-06:00"
modified = "2009-12-06T16:27:46-06:00"
slug = "Determine-BlogEngineNET-comments-that-havent-been-published"
blogengine = "8e5d3187-a46a-4989-a886-df7edaa97e07"
categories = ["tutorials / guides"]
tags = ["blogengine.net", "c#", "linq to xml", "xml"]
+++

<p>Unfortunately, BlogEngine.NET doesn't currently have a very good way to determine, at a glance, all of the comments that haven't been approved. While this will certainly be coming in a future release, or as an extension, I figured writing something simple to do this would be a good LINQ to XML test for me.</p>
<p>You can download the built executable, or play with the code, which is included below.</p>
<p><a rel="download" href="http://jamesrskemp.com/applications/TestBlogEngine.7z">Download the executable</a>&nbsp;(7-Zip format). Requires <a rel="external" href="http://smallestdotnet.com/">.NET Framework 3.5</a>.</p>
<div class="note">
<p>The form I created consisted of a TextBox, Button, and a DataGridView, with the default names.</p>
</div>
<pre class="code"><code class="csharp">using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml.Linq;

namespace TestBlogEngine {
	public partial class Form1 : Form {
		public Form1() {
			InitializeComponent();
		}

		private void button1_Click(object sender, EventArgs e) {
			OpenFileDialog sampleFile = new OpenFileDialog();
			sampleFile.Filter = "xml files (*.xml)|*.xml|All files (*.*)|*.*";

			if (sampleFile.ShowDialog() == DialogResult.OK) {
				textBox1.Text = sampleFile.FileName;

				string postsDirectory = System.IO.Path.GetDirectoryName(sampleFile.FileName);
				sampleFile.Dispose();

				string[] postFiles = System.IO.Directory.GetFiles(postsDirectory);

				DataTable comments = new DataTable();
				comments.Columns.Add("Post");
				comments.Columns.Add("CommentApproved");
				comments.Columns.Add("FileId");

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
									comment["FileId"] = "/post.aspx?id=" + System.IO.Path.GetFileNameWithoutExtension(postFile);
									comments.Rows.Add(comment);
								}
							}

						}
					}
				}

				postXml = null;

				dataGridView1.DataSource = comments;

			}
		}
	}
}</code></pre>
<p>EDIT: Scott Guthrie's excellent <a rel="external" href="http://weblogs.asp.net/scottgu/archive/2007/08/07/using-linq-to-xml-and-how-to-build-a-custom-rss-feed-reader-with-it.aspx">Using LINQ to XML (and how to build a custom RSS Feed Reader with it)</a> is <em>the</em> article that I keep going back to when I forget LINQ to XML basics.</p>
