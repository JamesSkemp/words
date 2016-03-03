+++
title = "ASP.NET charts example: Odin Sphere: Part 1 - Introduction and model"
summary = "In this series we use data from Odin Sphere to create charts with ASP.NET. After a short introduction, part one creates the object model we'll populate from the data."
draft = false
comments = true
date = "2010-08-13T22:50:00-05:00"
modified = "2010-08-14T12:23:43-05:00"
slug = "ASPNET-charts-example-Odin-Sphere-Part-1-Introduction-and-model"
blogengine = "955cf777-dbb6-4404-916d-974cd8ae1292"
categories = ["tutorials / guides"]
tags = ["xml", "c#", ".net", "asp.net"]
+++

<p>For a while now I've been meaning to work with <a rel="external" href="http://weblogs.asp.net/scottgu/archive/2010/02/07/built-in-charting-controls-vs-2010-and-net-4-series.aspx">ASP.NET 4's built-in charting functionality</a>. While I was going to use it alongside my gas tracking, I think I'm instead going to use my <a rel="external download" href="http://jamesrskemp.com/files/OdinSphere.xml">Odin Sphere leveling guide</a>, so I don't have to create an XSLT for the output.</p>
<p>In this part of the series I'll outline the data model I'll be using, and preliminary setups.</p>
<h3>Method</h3>
<p>So that this can easily be deployed anywhere, I'm going to opt not to use the control itself, but rather programmatically create the charts/graphs. I'll be&nbsp;creating a generic handler (.ashx) to handle the output.</p>
<p>I'll be using LINQ to XML to query the XML file that stores the content and may implement some level of caching at some point.</p>
<p>My environment is Visual Studio 2010 and .NET Framework 4. The controls are available for 3.5 and 2008, however, and 2010 Express should also suffice.</p>
<h3>Data model</h3>
<p>For this chart I'd like to chart each character's HP progression as they level, with each character displaying on the same graph.</p>
<p>This then gives us a List of Character, with each Character having a Name and a List of HpLevel, with HpLevel containing a Level and a HP total.</p>
<p>In our new Generic Handler (OdinSphere.ashx) we'll add the following within the existing public class:</p>
<pre class="code"><code class="csharp">	/// &lt;summary&gt;
	/// One of the five playable characters in Odin Sphere, for the Playstation 2.
	/// &lt;/summary&gt;
	public class Character {
		/// &lt;summary&gt;
		/// Name of the character.
		/// &lt;/summary&gt;
		public String Name { get; set; }
		/// &lt;summary&gt;
		/// List of hit point leveling information.
		/// &lt;/summary&gt;
		public List&lt;HpLevel&gt; HpLevels { get; set; }
	}

	/// &lt;summary&gt;
	/// Hit point information at a particular level.
	/// &lt;/summary&gt;
	public class HpLevel {
		/// &lt;summary&gt;
		/// Level of the character.
		/// &lt;/summary&gt;
		public int Level { get; set; }
		/// &lt;summary&gt;
		/// Hit points at a level, for a character.
		/// &lt;/summary&gt;
		public int HitPoints { get; set; }
	}</code></pre>
<p>These also require the following:</p>
<pre class="code"><code class="csharp">using System.Collections.Generic;
using System.Linq;</code></pre>
<p>At this point we've got our objects defined and set, so we can grab the data from the XML file and create our necessary objects ... which is exactly what we'll do in the second part of this series.</p>
