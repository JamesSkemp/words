+++
title = "XML Schema Definition creation: Journal - Part 2: XSD file with <oXygen/> XML Editor"
summary = "In part 2 of a new series, I cover how I created a new XML Schema Definition for journal-like XML files. This time we work with oXygen XML Editor to graphically create the XSD."
draft = false
comments = true
date = "2009-12-23T07:30:00-06:00"
modified = "2009-12-24T18:02:21-06:00"
slug = "XML-Schema-Definition-creation-Journal-Part-2-XSD-file-with-oXygen-XML-Editor"
blogengine = "28cb6b61-484c-4d34-8131-ac07d87999c7"
categories = ["tutorials / guides"]
tags = ["xml", "xml schema definition", "xsd", "oxygen xml editor"]
+++

<p>In <a href="http://strivinglife.com/words/post/XML-Schema-Definition-creation-Journal-Part-1-Primary-layout.aspx">the first part of this series</a> I had outlined a sample layout that I wanted to use for a series of XML files that I would be creating over the course of 2010.</p>
<p>This time I'm going to create the actual XML Schema Definition file with <a rel="external" href="http://www.oxygenxml.com/">&lt;oXygen/&gt; XML Editor</a>, version 11.1.</p>
<div class="note">
<p>I've been using &lt;oXygen/&gt; since January 2008, and wouldn't trade it for any other XML editor.</p>
</div>
<p>If you don't have &lt;oXygen/&gt; you can still follow along. The finished product is available online&nbsp;and as you follow along you'll get a sense of what the tool is doing. A trial version of the application is also available.</p>
<p><a href="http://media.jamesrskemp.com/xsd/JournalSimple.xsd">Download/view the Journal XML Schema Definition</a>.</p>
<h3>Creating an empty XSD&nbsp;in &lt;oXygen/&gt;</h3>
<p>After starting &lt;oXygen/&gt; select File &gt; New... and select xsd - XML Schema (<a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_1.jpg">Figure 1</a>).</p>
<p>At this point we won't select/enter a Target namespace, and will use the default xs prefix and appropriate namespace,&nbsp;as shown in&nbsp;<a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_2.jpg">Figure 2</a>.</p>
<p>Once we have a new file created, select the 'Text' 'tab' in the bottom left-hand corner of the application. This gives us a model view as well as the XML behind the model, as shown in <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_3.jpg">Figure 3</a>.</p>
<div class="note">
<p>12/23/2009: <span style="text-decoration: line-through;">While working on the next part of this series I realized that I was wrong to have the elements and attributes camel case, instead of Pascal case. The XSD has been updated, but the guide has been left as it was created. Just uppercase the initial character and you'll be fine. Or leave it as is.</span> Actually, I have no idea what I'm talking about.</p>
</div>
<h3>Filling out the XSD</h3>
<p>Now that we have a model, we can start creating our schema definition graphically. We'll start at the top, with the root element.</p>
<p>Right-click on the schema box and select Append child &gt; xs:element. Make sure the name is set to Name and enter "journal" as the Value. (<a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_4.jpg">Figure&nbsp;4</a>.)&nbsp;Press OK. Note that the text version is also updated accordingly. As you make changes, try to pay attention to what happens below. Luckily, the interface is pretty obvious, adding explanatory text to the standard items. It will also highlight where errors are, as they arise.</p>
<p>Since we've got an attribute to add to the journal element, as well as an entry element, we'll next add these. Right-click on journal, select Append child &gt; xs:complexType, leaving everything blank (<a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_5.jpg">Figure 5</a>). Right-click on this new item (a 'box') and select Append child &gt; xs:sequence. Again, leave everything blank (<a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_6.jpg">Figure 6</a>).&nbsp;Right-click on the 'box' again and select Append child &gt; xs:attribute. This time we'll expand the box using the arrow and change the name (to source), the type (to xs:string), and the use (to required) as shown in <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_7.jpg">Figure 7</a>.</p>
<p>Now our journal element is finished, but we need to add the entry element and&nbsp;its attribute and children elements.</p>
<p>Right-click on the icon of three boxes (added when we added an xs:sequence above) and select Append child &gt; xs:element. Name is entry and maxOccurs is unbounded, since this element can repeat any number of times. (<a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_8.jpg">Figure 8</a>.)</p>
<p>Repeating what we did before, we'll right-click on entry and select Append child &gt; xs:complexType, leaving everything blank again. Right-click on this new item and select Append child &gt; xs:sequence, again leaving everything blank. Right-click on the box again (the xs:complexType) and select Append child &gt; xs:attribute. Giving this a name of id, a type of xs:string, and use of required we end up with something like <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_9.jpg">Figure 9</a>.</p>
<p>Now we're at a point where we have more than one element at the same level, but some also have children. Luckily, we already know what to do to finish this up.</p>
<p>Right-click on the three boxes (above the id attribute) and select Append child &gt; xs:element five times. Once all five are created we can update the names accordingly, until we have <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_10.jpg">Figure 10</a>. A sequence states that the items must appear in a particular order, 0 or more times. So just follow the sample layout as you name, which determines how they must appear in the XML document.</p>
<p>The author element has an element within it, so we'll do our now standard of right-clicking on it and Append child &gt; xs:complexType then Append child &gt; xs:sequence on the new item. Finally Append child &gt; xs:element, giving it a name of name and type of xs:string. See <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_11.jpg">Figure 11</a> for this final step.</p>
<p>Double click on dateCreated, then dateUpdated, changing the type of both to xs:dateTime. <span style="text-decoration: line-through;">Then change the nillable value of dateUpdated to true.</span> See <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_12.jpg">Figure 12</a>. Contrary to the figure, based on our initial layout we want dateCreated and dateUpdated to be the same initially, so it should actually never be null. You can remove this attribute by double clicking on the item in model view and removing it there (right-click in the appropriate Attribute cell and select Remove)&nbsp;or by removing it from the XML itself.</p>
<p>Finally double click on text and change the type to xs:string.</p>
<p>Now we'll repeat the complexType/sequence additions a couple more times. Right-click on supplements and append an xs:complexType, xs:sequence and xs:element, with a name of supplement. Right-click on supplement and again append an xs:complexType, xs:sequence, two xs:element, and an xs:attribute on xs:complexType (the single box). This gives us <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_13.jpg">Figure 13</a>.</p>
<p>The first element name is dateAdded, type is xs:dateTime. The second element name is text, type is xs:string. Attribute name is id and type is xs:positiveInteger, with use of required.</p>
<p>You may have noticed another possible option. positiveInteger starts at 1 while nonNegativeInteger starts at 0. Per the rough schema we want to start at 1, and are therefore using the former.</p>
<p>Finally change maxOccurs on supplement to unbounded, since we want to allow multiple supplement elements. <a href="http://media.jamesrskemp.com/graphics/oXygenXmlEditor/oXygen_XmlSchemaDefinition_14.jpg">Figure 14</a> shows this and most of the last few changes we had made as well.</p>
<p>Save the file, calling it whatever you want. (I choose <a href="http://media.jamesrskemp.com/xsd/JournalSimple.xsd">JournalSimple.xsd</a>, as I can see expanding this to allow comments, for example.)</p>
<h3>Validating the schema</h3>
<p>&lt;oXygen/&gt; XML Editor has a tool to generate sample XML files from an XML Schema Definition (XSD). Select Tools &gt; Generate Sample XML Files..., select an XSD file (will be the current XSD if you still have it open), choose the output directory, and run. In my case, that gave me an output like the following.</p>
<pre class="code"><code class="xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;journal xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:noNamespaceSchemaLocation="file:/D:/projects/media/xsd/JournalSimple.xsd" source="source0"&gt;
	&lt;entry id="id0"&gt;
		&lt;author&gt;
			&lt;name&gt;name0&lt;/name&gt;
		&lt;/author&gt;
		&lt;dateCreated&gt;2006-05-04T18:13:51.0Z&lt;/dateCreated&gt;
		&lt;dateUpdated&gt;2006-05-04T18:13:51.0Z&lt;/dateUpdated&gt;
		&lt;text&gt;text0&lt;/text&gt;
		&lt;supplements&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text1&lt;/text&gt;
			&lt;/supplement&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text2&lt;/text&gt;
			&lt;/supplement&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text3&lt;/text&gt;
			&lt;/supplement&gt;
		&lt;/supplements&gt;
	&lt;/entry&gt;
	&lt;entry id="id1"&gt;
		&lt;author&gt;
			&lt;name&gt;name1&lt;/name&gt;
		&lt;/author&gt;
		&lt;dateCreated&gt;2006-05-04T18:13:51.0Z&lt;/dateCreated&gt;
		&lt;dateUpdated&gt;2006-05-04T18:13:51.0Z&lt;/dateUpdated&gt;
		&lt;text&gt;text4&lt;/text&gt;
		&lt;supplements&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text5&lt;/text&gt;
			&lt;/supplement&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text6&lt;/text&gt;
			&lt;/supplement&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text7&lt;/text&gt;
			&lt;/supplement&gt;
		&lt;/supplements&gt;
	&lt;/entry&gt;
	&lt;entry id="id2"&gt;
		&lt;author&gt;
			&lt;name&gt;name2&lt;/name&gt;
		&lt;/author&gt;
		&lt;dateCreated&gt;2006-05-04T18:13:51.0Z&lt;/dateCreated&gt;
		&lt;dateUpdated&gt;2006-05-04T18:13:51.0Z&lt;/dateUpdated&gt;
		&lt;text&gt;text8&lt;/text&gt;
		&lt;supplements&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text9&lt;/text&gt;
			&lt;/supplement&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text10&lt;/text&gt;
			&lt;/supplement&gt;
			&lt;supplement id="50"&gt;
				&lt;dateAdded&gt;2006-05-04T18:13:51.0Z&lt;/dateAdded&gt;
				&lt;text&gt;text11&lt;/text&gt;
			&lt;/supplement&gt;
		&lt;/supplements&gt;
	&lt;/entry&gt;
&lt;/journal&gt;</code></pre>
<p>While not perfect, based on what we want, it's not too bad. And it shows us that we're on track, since the elements and attributes we wanted on items are there.</p>
<h3>Next steps</h3>
<p>At this point we've created our XSD. Is the series at an end? I suppose we'll find out if/once part 3 is released.</p>
