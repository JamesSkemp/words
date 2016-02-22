+++
title = "Importing a custom namespace / custom type into an XSD"
summary = "How to save and import a custom type into an XML Schema Document (XSD)."
draft = false
comments = true
date = "2010-09-05T09:00:00-05:00"
modified = "2010-09-04T18:05:16-05:00"
slug = "Importing-a-custom-namespace-custom-type-into-an-XSD"
blogengine = "810b200f-f12c-4394-abe2-1d69267e7e70"
categories = ["tutorials / guides"]
tags = ["xsd", "xml"]
+++

<p>I have a custom type that I use in a couple of my documents.</p>
<p>Unfortunately, in the past I was adding this to each xsd, as I needed it. However, I've now figured out how to import it into xsd files as needed.</p>
<h3>Original schema</h3>
<p>Currently I'm adding the following at the top of each xsd:</p>
<pre class="code"><code class="xml">&lt;xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"&gt;
	&lt;xs:simpleType name="customDateType"&gt;
		&lt;xs:restriction base="xs:string"&gt;
			&lt;xs:annotation&gt;
				&lt;xs:documentation&gt;&lt;![CDATA[Allows for a year, a year and a month, or a year, month, and day, to be defined.]]&gt;&lt;/xs:documentation&gt;
			&lt;/xs:annotation&gt;
			&lt;xs:pattern value="\d{4}(-\d{2}){0,2}"/&gt;
		&lt;/xs:restriction&gt;
	&lt;/xs:simpleType&gt;
	&lt;!-- Remainder of schema goes here. --&gt;
&lt;/xs:schema&gt;</code></pre>
<h3>New schema</h3>
<p>Instead of the above I create a new file, for example <a href="http://media.jamesrskemp.com/xsd/2010/09/04/CustomDateType.xsd">media.jamesrskemp.com/xsd/2010/09/04/CustomDateType.xsd</a>, which looks like the following:</p>
<pre class="code"><code class="xml">&lt;xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://media.jamesrskemp.com/ns/CustomDateType" version="1"&gt;
	&lt;xs:simpleType name="customDateType"&gt;
		&lt;xs:restriction base="xs:string"&gt;
			&lt;xs:annotation&gt;
				&lt;xs:documentation&gt;&lt;![CDATA[Allows for a year, a year and a month, or a year, month, and day, to be defined.]]&gt;&lt;/xs:documentation&gt;
			&lt;/xs:annotation&gt;
			&lt;xs:pattern value="\d{4}(-\d{2}){0,2}"/&gt;
		&lt;/xs:restriction&gt;
	&lt;/xs:simpleType&gt;
&lt;/xs:schema&gt;</code></pre>
<p>Then I need to update the original XSD to refer to this. After some messing around with oXygen, it turns out it needs to look like this:</p>
<pre class="code"><code class="xml">&lt;xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:cdt="http://media.jamesrskemp.com/ns/CustomDateType"&gt;
	&lt;xs:import namespace="http://media.jamesrskemp.com/ns/CustomDateType" schemaLocation="http://media.jamesrskemp.com/xsd/2010/09/04/CustomDateType.xsd"/&gt;
	&lt;!-- Remainder of schema continues here. --&gt;
</code></pre>
<p>And with those minor changes I, or anyone else, can use my custom type.</p>
