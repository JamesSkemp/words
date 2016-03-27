+++
title = "ASP.NET charts example: Odin Sphere: Part 2 - Parsing the XML"
description = "In part two of a series on creating charts with ASP.NET, we grab an XML data file and populate our custom objects from part one with the necessary data."
draft = false
comments = true
date = "2010-08-14T14:00:00-05:00"
modified = "2010-08-14T14:39:03-05:00"
slug = "ASPNET-charts-example-Odin-Sphere-Part-2-Parsing-the-XML"
blogengine = "9e8764f2-dfb8-45ff-b44a-488a96558de0"
categories = ["tutorials / guides"]
tags = ["xml", "c#", ".net", "asp.net"]
+++

<p>In <a href="http://strivinglife.com/words/post/ASPNET-charts-example-Odin-Sphere-Part-1-Introduction-and-model.aspx">part one of this series</a> we covered what we'd be doing, and what model we'd be using for the data.</p>
<p>This time we'll parse the XML file that contains the data we need, and populate the objects.</p>
<h3>Loading the XML file</h3>
<p>The XML file we'll be loading is located at&nbsp;<a href="http://jamesrskemp.com/files/OdinSphere.xml">http://jamesrskemp.com/files/OdinSphere.xml</a>, and to keep it simple, we'll load it in assuming we're on a different server/domain.</p>
<p>First we'll need to add the following so we can make use of XDocument.</p>
<pre class="code"><code class="csharp">using System.Xml.Linq;</code></pre>
<p>Next we'll update ProcessRequest by loading the XML file.</p>
<pre class="code"><code class="csharp">XDocument dataFile = XDocument.Load("http://jamesrskemp.com/files/OdinSphere.xml");</code></pre>
<p>And then we'll parse it out into our custom objects.</p>
<pre class="code"><code class="csharp">IEnumerable&lt;Character&gt; characterData = from characters in dataFile.Descendants("Character")
	select new Character {
		Name = characters.Attribute("name").Value,
		HpLevels = (from levels in characters.Element("HP").Element("Levels").Descendants("Level")
			select new HpLevel {
				Level = int.Parse(levels.Attribute("id").Value),
				HitPoints = int.Parse(levels.Attribute("hitPoints").Value)
			}
		).ToList()
	};</code></pre>
<p>With that done, we can now verify the data by displaying some very basic information on the page.</p>
<pre class="code"><code class="csharp">		context.Response.ContentType = "text/plain";
		foreach (Character character in characterData) {
			context.Response.Write(character.Name + Environment.NewLine);
			context.Response.Write("Maximum HP level = " + character.HpLevels.Last().Level.ToString() + Environment.NewLine + Environment.NewLine);

		}</code></pre>
<p>With that aspect verified, we can create and output our graphs, which we'll cover in part three.</p>
