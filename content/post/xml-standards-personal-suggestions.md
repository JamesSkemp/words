+++
title = "XML standards - personal suggestions"
description = "Personal standards I'll be applying to all future XML creation."
draft = false
comments = true
date = "2010-09-03T16:20:00-05:00"
modified = "2010-09-03T16:34:08-05:00"
slug = "XML-standards-personal-suggestions"
blogengine = "7f784245-d78a-458b-a825-0446017af7c7"
categories = ["article"]
tags = ["xml", "xsd", "dtd"]
+++

<p>As I prepare to create another XML data file, I started looking at the standards I use to create XML files, and what the recommendations are.</p>
<h3>Elements</h3>
<p>In the past I've used camel case, but on a recent file used Pascal case instead. I think this was more becauase I've started to using Pascal case for public items (variables), and camel case for private items, as that's fairly standard in development.</p>
<p>I generally stay away from underscores, as camel and Pascal case are both perfectly readable, in my opinion.</p>
<p>Hyphens seem to be generally frowned upon, due to various language restrictions.</p>
<p>Suggestion: camel case.</p>
<h3>XSD</h3>
<p>The other question was versioning of XSD (or DTD) files. According to&nbsp;the 2004 article <a rel="external" href="http://www.ibm.com/developerworks/webservices/library/ws-version/">Best practices for Web services versioning</a>, the W3C recommends the company name, a date stamp (year and month), but IBM recommends (in the article) including the day as well.</p>
<p>I've been slowly moving these documents over to my media.jamesrskemp.com domain, under either a xsd or dtd folder. Looking at the W3C listing of <a rel="external" href="http://www.w3.org/QA/2002/04/valid-dtd-list.html">Recommended Doctype Declarations to use in your Web document</a>, this doesn't seem to be all that horrible, realizing of course that the are DTD references and not XSD (true XML) references.</p>
<p>Another alternative would be xsd.jamesrskemp.com/<em>date</em>/file.xsd and dtd.jamesrskemp.com/<em>date</em>/file.dtd, but this is basically the same as using a sub-directory before (although it does simplify things).</p>
<p>Suggestion: http://<em>whatever</em>/YYYY/MM/DD/file.ext, with all older items staying where they are.</p>
