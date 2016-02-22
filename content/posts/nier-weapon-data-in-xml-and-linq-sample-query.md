+++
title = "Nier weapon data in XML (and LINQ sample query)"
summary = "Information about a new XML data file with Nier weapon upgrade information."
draft = false
comments = true
date = "2011-10-16T21:59:00-05:00"
modified = "2011-10-16T22:07:47-05:00"
slug = "Nier-weapon-data-in-XML-and-LINQ-sample-query"
blogengine = "80ace96d-6863-4cdc-9849-c32ee730156b"
categories = ["gaming"]
tags = ["xml", "playstation 3", "xbox 360", "nier"]
+++

<p>Going through the game <a href="http://strivinglife.com/words/post/Review-Nier-2010-Xbox-360-PlayStation-3.aspx">Nier</a> yet again, I wanted an easier way to track what weapon levels I had already upgraded to, and what items I still needed to unlock weapon items.</p>
<p>Phase one towards that goal is creating an XML file with weapon upgrade information which is available online: <a rel="external" href="http://media.jamesrskemp.com/xml/NierWeapons.xml">Nier weapon data</a>. An XML schema document for this information is also available: <a rel="external" href="http://media.jamesrskemp.com/xsd/2011/10/NierWeapons.xsd">Nier weapon XSD</a>.</p>
<h3>Sample LINQ query</h3>
<p>The following query can be run from LINQPAD, and will either display all items with their counts, or a grouped listing of items with the total quantity needed.</p>
<pre class="code"><code class="csharp">XDocument weaponsXml = XDocument.Load(@"http://media.jamesrskemp.com/xml/NierWeapons.xml");

var items = weaponsXml
	.Descendants()
	.Elements("Item")
	.Select(i =&gt; new WeaponItem { Name = i.Attribute("Name").Value, Quantity = i.Attribute("Quantity") != null ? int.Parse(i.Attribute("Quantity").Value) : 1 })
	.OrderBy(i =&gt; i.Name).ThenBy(i =&gt; i.Quantity)
	;

var itemsGrouped = items.GroupBy(i =&gt; i.Name).Select(g =&gt; new WeaponItem { Name = g.Key, Quantity = g.Sum(i =&gt; i.Quantity) });

//items.Dump();
itemsGrouped.Dump();

}
public class WeaponItem {
	public string Name {get;set;}
	public int Quantity {get;set;}</code></pre>
