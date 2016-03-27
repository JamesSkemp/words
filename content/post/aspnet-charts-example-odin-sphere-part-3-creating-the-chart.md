+++
title = "ASP.NET charts example: Odin Sphere: Part 3 - Creating the chart"
description = "In this final part of the series, we use data from an XML file to create a chart of leveling information for Odin Sphere characters."
draft = false
comments = true
date = "2010-08-15T13:00:00-05:00"
modified = "2010-08-14T14:34:28-05:00"
slug = "ASPNET-charts-example-Odin-Sphere-Part-3-Creating-the-chart"
blogengine = "192e5cf0-d2f9-44e6-99b0-5c4b3a1c3109"
categories = ["tutorials / guides"]
tags = ["xml", "c#", ".net", "asp.net"]
+++

<p>In part one of this series we covered what we'd be doing, and what data model we'd be using.</p>
<p>In part two of this series we used LINQ to XML to query the XML file with the data we want to display.</p>
<p>This time we'll be doing the heavy lifting of actually creating the chart and displaying it to the user. For ease, I'll be implementing very basic caching.</p>
<h3>Preliminary requirement</h3>
<p>Before you can use the charting functionality you need to have a reference to System.Web.DataVisualization. We can then use this in our handler as below.</p>
<pre class="code"><code class="csharp">using System.Web.UI.DataVisualization.Charting;</code></pre>
<p>Next we can do the heavy lifting of creating the basics of the chart:</p>
<pre class="code"><code class="csharp">// Create a new chart, and set the basic properties of it.
Chart hpChart = new Chart();
hpChart.Width = 800;
hpChart.Height = 500;
hpChart.Titles.Add("Odin Sphere HP leveling");
hpChart.Palette = ChartColorPalette.Bright;
hpChart.Legends.Add("Main");
hpChart.Legends[0].LegendStyle = LegendStyle.Row;
hpChart.Legends[0].Docking = Docking.Bottom;
// Create a new area for the main chart to display within.
ChartArea mainArea = new ChartArea("Main chart");
// Set the properties for the x-axis.
mainArea.AxisX.Name = "Level";
mainArea.AxisX.Title = "Level";
mainArea.AxisX.MajorGrid.LineColor = System.Drawing.Color.DimGray;
mainArea.AxisX.MinorGrid.Enabled = true;
mainArea.AxisX.MinorGrid.LineColor = System.Drawing.Color.LightGray;
// Set the properties for the y-axis.
mainArea.AxisY.Name = "Hit points";
mainArea.AxisY.Title = "Hit points";
mainArea.AxisY.MajorGrid.LineColor = System.Drawing.Color.DimGray;
mainArea.AxisY.MinorGrid.Enabled = true;
mainArea.AxisY.MinorGrid.LineColor = System.Drawing.Color.LightGray;
mainArea.AxisY.MinorGrid.Interval = 50;
hpChart.ChartAreas.Add(mainArea);</code></pre>
<p>With our chart created we can now add our data.</p>
<pre class="code"><code class="csharp">foreach (Character character in characterData) {
	// Add a new series of points for each character.
	Series characterSeries = new Series();
	characterSeries.Name = character.Name;
	characterSeries.ChartType = SeriesChartType.Line;
	foreach (HpLevel characterLevel in character.HpLevels) {
		// Add a point for each level recorded.
		characterSeries.Points.AddXY(characterLevel.Level, characterLevel.HitPoints);
	}
	hpChart.Series.Add(characterSeries);
}</code></pre>
<p>Since we want to cache the chart, we'll add an informational message.</p>
<pre class="code"><code class="csharp">// Add a new informational title.
Title cacheTitle = new Title("Cached " + DateTime.Now.ToString() + " and based on http://jamesrskemp.com/files/OdinSphere.xml");
cacheTitle.Docking = Docking.Bottom;
hpChart.Titles.Add(cacheTitle);</code></pre>
<p>Next we'll set the rendering type of the chart and add it to the cache.</p>
<pre class="code"><code class="csharp">hpChart.RenderType = RenderType.BinaryStreaming;
// Cache our object for an amount of time
HttpRuntime.Cache.Add("OdinSphereChart", hpChart, null, DateTime.Now.AddMinutes(5), System.Web.Caching.Cache.NoSlidingExpiration, System.Web.Caching.CacheItemPriority.Low, null);</code></pre>
<p>Everything above, as well as the XDocument load from part two, can be wrapped by a check for whether the chart is in the cache.</p>
<pre class="code"><code class="csharp">// Determine whether the chart is already cached.
if (HttpRuntime.Cache["OdinSphereChart"] == null) {
//...
}</code></pre>
<p>And then we can finally output the chart to the user.</p>
<pre class="code"><code class="csharp">// Output the cached chart to the browser.
using (System.IO.MemoryStream stream = new System.IO.MemoryStream()) {
	((Chart)HttpRuntime.Cache["OdinSphereChart"]).SaveImage(stream);
	context.Response.ContentType = "image/png";
	context.Response.BinaryWrite(stream.GetBuffer());
}</code></pre>
<h3>Final code</h3>
<p>At the end of our exercise, our handler (OdinSphere.ashx) looks something like the following:</p>
<pre class="code"><code class="csharp">&lt;%@ WebHandler Language="C#" Class="OdinSphere" %&gt;

using System;
using System.Web;
using System.Collections.Generic;
using System.Linq;
using System.Xml.Linq;
using System.Text;
using System.Web.UI.DataVisualization.Charting;

public class OdinSphere : IHttpHandler {

	/// &lt;summary&gt;
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
	}

	public void ProcessRequest(HttpContext context) {
		// Determine whether the chart is already cached.
		if (HttpRuntime.Cache["OdinSphereChart"] == null) {
			// Grab the current data.
			XDocument dataFile = XDocument.Load("http://jamesrskemp.com/files/OdinSphere.xml");
			IEnumerable&lt;Character&gt; characterData = from characters in dataFile.Descendants("Character")
												   select new Character {
													   Name = characters.Attribute("name").Value,
													   HpLevels = (from levels in characters.Element("HP").Element("Levels").Descendants("Level")
																   select new HpLevel {
																	   Level = int.Parse(levels.Attribute("id").Value),
																	   HitPoints = int.Parse(levels.Attribute("hitPoints").Value)
																   }
													   ).ToList()
												   };

			// Create a new chart, and set the basic properties of it.
			Chart hpChart = new Chart();
			hpChart.Width = 800;
			hpChart.Height = 500;
			hpChart.Titles.Add("Odin Sphere HP leveling");
			hpChart.Palette = ChartColorPalette.Bright;
			hpChart.Legends.Add("Main");
			hpChart.Legends[0].LegendStyle = LegendStyle.Row;
			hpChart.Legends[0].Docking = Docking.Bottom;
			// Create a new area for the main chart to display within.
			ChartArea mainArea = new ChartArea("Main chart");
			// Set the properties for the x-axis.
			mainArea.AxisX.Name = "Level";
			mainArea.AxisX.Title = "Level";
			mainArea.AxisX.MajorGrid.LineColor = System.Drawing.Color.DimGray;
			mainArea.AxisX.MinorGrid.Enabled = true;
			mainArea.AxisX.MinorGrid.LineColor = System.Drawing.Color.LightGray;
			// Set the properties for the y-axis.
			mainArea.AxisY.Name = "Hit points";
			mainArea.AxisY.Title = "Hit points";
			mainArea.AxisY.MajorGrid.LineColor = System.Drawing.Color.DimGray;
			mainArea.AxisY.MinorGrid.Enabled = true;
			mainArea.AxisY.MinorGrid.LineColor = System.Drawing.Color.LightGray;
			mainArea.AxisY.MinorGrid.Interval = 50;
			hpChart.ChartAreas.Add(mainArea);

			foreach (Character character in characterData) {
				// Add a new series of points for each character.
				Series characterSeries = new Series();
				characterSeries.Name = character.Name;
				characterSeries.ChartType = SeriesChartType.Line;
				foreach (HpLevel characterLevel in character.HpLevels) {
					// Add a point for each level recorded.
					characterSeries.Points.AddXY(characterLevel.Level, characterLevel.HitPoints);
				}
				hpChart.Series.Add(characterSeries);
			}

			// Add a new informational title.
			Title cacheTitle = new Title("Cached " + DateTime.Now.ToString() + " and based on http://jamesrskemp.com/files/OdinSphere.xml");
			cacheTitle.Docking = Docking.Bottom;
			hpChart.Titles.Add(cacheTitle);
			
			hpChart.RenderType = RenderType.BinaryStreaming;
			// Cache our object for an amount of time
			HttpRuntime.Cache.Add("OdinSphereChart", hpChart, null, DateTime.Now.AddMinutes(5), System.Web.Caching.Cache.NoSlidingExpiration, System.Web.Caching.CacheItemPriority.Low, null);
		}

		// Output the cached chart to the browser.
		using (System.IO.MemoryStream stream = new System.IO.MemoryStream()) {
			((Chart)HttpRuntime.Cache["OdinSphereChart"]).SaveImage(stream);
			context.Response.ContentType = "image/png";
			context.Response.BinaryWrite(stream.GetBuffer());
		}
	}
 
    public bool IsReusable {
        get {
            return false;
        }
    }
}</code></pre>
<p>You can <a rel="external download" href="http://jamesrskemp.com/testing/OdinSphere.ashx">see this in action</a> online.</p>
