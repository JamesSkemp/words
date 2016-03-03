+++
title = "Domain name XML"
summary = "Here's an XML structure, with DTD, for storing domain name information. [slnet0514:ef3fdc7d-e451-484d-8874-77d9fed38538]"
draft = false
comments = true
date = "2008-06-15T10:00:00-05:00"
modified = "2009-06-01T22:47:18-05:00"
slug = "Domain-name-XML"
blogengine = "ef3fdc7d-e451-484d-8874-77d9fed38538"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>In <a href="/words/post/XML-creation-Part-01.aspx">XML creation:&nbsp;Part 1</a>,&nbsp;I went about creating an XML document, with&nbsp;both a CSS and XSLT, that was used to store <a href="http://jamesrskemp.com/video_games.xml" target="_blank">my video game information</a>.</p>
<p>Yesterday I was going through my domains, and realized that it would be pretty helpful to have an XML document where I could store domain name information, since I've got too many to keep track of in my head.</p>
<h3>The layout</h3>
<p>Using lists, this the version 1 that I came up with yesterday:</p>
<ul>
<li>
<div>domains</div>
<ul>
<li>
<div>domain</div>
<ul>
<li>
<div>name</div>
</li>
<li>
<div>created</div>
<ul>
<li>
<div>year</div>
</li>
<li>
<div>month</div>
</li>
<li>
<div>day</div>
</li>
</ul>
</li>
<li>
<div>expires</div>
<ul>
<li>
<div>year</div>
</li>
<li>
<div>month</div>
</li>
<li>day</li>
</ul>
</li>
<li>
<div>registrar</div>
</li>
<li>
<div>servers</div>
<ul>
<li>
<div>server</div>
<ul>
<li>ip</li>
<li>
<div>path</div>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<ul>
<li>
<div>subdomains</div>
<ul>
<li>
<div>subdomain</div>
<ul>
<li>
<div>name</div>
</li>
<li>
<div>path</div>
</li>
<li>
<div>server</div>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<p>Now that we've got a layout, let's create an empty structure.</p>
<h3>Empty structure</h3>
<p>Unlike <a href="/words/post/XML-creation-Part-02.aspx">the last time we did this</a>, we'll use attributes much more this time.</p>
<div class="note">
<p>I'll be using&nbsp;<a href="http://www.oxygenxml.com/" target="_blank">&lt;oXygen/&gt; XML Editor</a> to create this.</p>
</div>
<pre class="code"><code class="xml">
&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&nbsp; &nbsp; &lt;domains&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;domain id="1"&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;name&gt;jamesrskemp.net&lt;/name&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;created year="2002" month="12" day="11"/&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;expires year="2009" month="5" day="15"/&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;registrar&gt;GoDaddy&lt;/registrar&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;servers&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;server id="1"&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;ip&gt;76.12.10.196&lt;/ip&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;path&gt;\Inetpub\wwwroot\jamesrskemp&lt;/path&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/server&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/servers&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;subdomains&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;subdomain id="1" name="www" server="1"&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;path&gt;http://jamesrskemp.com&lt;/path&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;/subdomain&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/subdomains&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;/domain&gt;
&nbsp; &nbsp; &lt;/domains&gt;
</code></pre>
<h3>Document Type Definition (DTD)</h3>
<p>The domain_names.dtd&nbsp;for the above XML is listed below.</p>
<pre class="code"><code class="xml">
&lt;!ELEMENT domains (domain*)&gt;
&lt;!ELEMENT domain (name, created, expires, registrar, servers*, subdomains*)&gt;
&lt;!ATTLIST domain id CDATA #REQUIRED&gt;

&lt;!ELEMENT name (#PCDATA)&gt;
&lt;!ELEMENT created EMPTY&gt;
&lt;!ATTLIST created year CDATA #REQUIRED&gt;
&lt;!ATTLIST created month CDATA #REQUIRED&gt;
&lt;!ATTLIST created day CDATA #REQUIRED&gt;
&lt;!ELEMENT expires EMPTY&gt;
&lt;!ATTLIST expires year CDATA #REQUIRED&gt;
&lt;!ATTLIST expires month CDATA #REQUIRED&gt;
&lt;!ATTLIST expires day CDATA #REQUIRED&gt;
&lt;!ELEMENT registrar (#PCDATA)&gt;

&lt;!ELEMENT servers (server*)&gt;

&lt;!ELEMENT server (ip, path)&gt;
&lt;!ATTLIST server id CDATA #REQUIRED&gt;

&lt;!ELEMENT ip (#PCDATA)&gt;
&lt;!ELEMENT path (#PCDATA)&gt;

&lt;!ELEMENT subdomains (subdomain*)&gt;

&lt;!ELEMENT subdomain (path)&gt;
&lt;!ATTLIST subdomain id CDATA #REQUIRED&gt;
&lt;!ATTLIST subdomain name CDATA #REQUIRED&gt;
&lt;!ATTLIST subdomain server CDATA #REQUIRED&gt;
</code></pre>
<div class="note">
<p>I've yet to figure out how to serve the DTD like the W3C is. Any ideas? I've already tried serving content as application/xml-dtd, but then Validome.org couldn't handle the DTD, so I had to switch it to application/xml.</p>
</div>
<h3>Final XML</h3>
<p>With the XML and DTD created, we now have a valid XML document.</p>
<p><a href="http://jamesrskemp.com/domain_names.xml" target="_blank">View the completed XML document</a>.</p>
