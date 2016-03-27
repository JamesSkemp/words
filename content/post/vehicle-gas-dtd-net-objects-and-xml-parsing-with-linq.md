+++
title = "Vehicle gas DTD .NET objects and XML parsing with LINQ"
description = "Having created an XML document, with DTD, to store vehicle fillups, here's a look at a rough object and how to parse them out of XML via LINQ."
draft = false
comments = true
date = "2010-06-10T22:20:00-05:00"
modified = "2010-06-10T22:46:27-05:00"
slug = "Vehicle-gas-DTD-NET-objects-and-XML-parsing-with-LINQ"
blogengine = "eb2d03cc-cfc5-4b7f-bff8-daae83e3798b"
categories = ["tutorials / guides"]
tags = [".net", "c#", "linq to xml", "xml", "vehicle gas"]
+++

<div class="note">
<p>The code contained below is a rough draft, and will eventually be moved into an assembly, and the code posted.</p>
</div>
<p>At <a href="http://strivinglife.com/words/post/2007-VW-Rabbit-10000-miles.aspx">some point in 2007</a> I started <a href="http://jamesrskemp.net/vehicle_gas.xml">keeping track of my gas mileage</a> in an XML file, with a custom DTD for validation (and intellisense in oXygen).</p>
<p>I present below the code necessary to create an rough object from the XML, and the LINQ to parse it out.</p>
<h3>C# objects</h3>
<pre class="code"><code class="csharp">	public class Vehicle {
		public int Id { get; set; }
		public String Make { get; set; }
		public String Model { get; set; }
		public int Year { get; set; }
		public IEnumerable Fillups { get; set; }
	}

	public class Fillup {
		public int Id { get; set; }
		public DateTime Date { get; set; }
		public int MilesTotal { get; set; }
		public Decimal MilesDriven { get; set; }
		public Decimal Gallons { get; set; }
		public Decimal CostPerGallon { get; set; }
		public Decimal CostTotal { get; set; }
		public String Notes { get; set; }
	}</code></pre>
<h3>LINQ to XML</h3>
<pre class="code"><code class="csharp">XDocument vehicleGasXml = XDocument.Load(@"C:\path\to\vehicle_gas.xml");

IEnumerable vehicles = from vehicle in vehicleGasXml.Descendants("vehicle")
	select new Vehicle {
		Id = int.Parse(vehicle.Attribute("id").Value),
		Make = vehicle.Element("make").Value,
		Model = vehicle.Element("model").Value,
		Year = int.Parse(vehicle.Element("year").Value),
		Fillups = from fillup in vehicle.Descendants("fillup")
			select new Fillup {
			  Id = int.Parse(fillup.Attribute("id").Value),
			  Date = DateTime.ParseExact(fillup.Element("date").Value, "yyyy-MM-dd", System.Globalization.CultureInfo.InvariantCulture),
			  MilesTotal = int.Parse(fillup.Element("milesCar").Value),
			  MilesDriven = decimal.Parse(fillup.Element("milesDriven").Value),
			  Gallons = decimal.Parse(fillup.Element("gallons").Value),
			  CostPerGallon = decimal.Parse(fillup.Element("costGallon").Value),
			  CostTotal = decimal.Parse(fillup.Element("costTotal").Value),
			  Notes = fillup.Element("notes").Value
			}
	};</code></pre>
<p>As always, suggestions appreciated. (Although I've already got code that, using .NET 4, creates some rather nice charts with the information contained within a document such as this, and consider this close to complete; name information isn't grabbed, but I'm not sure that's altogether necessary ...)</p>
