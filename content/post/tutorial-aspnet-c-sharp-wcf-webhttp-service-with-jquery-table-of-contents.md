+++
title = "Tutorial: ASP.NET (C#) WCF WebHttp service with jQuery: Table of Contents"
description = "In the next week I'll be writing a tutorial on creating a RESTful Web service that can be consumed by jQuery and returns loan payoff information."
draft = false
comments = true
date = "2010-06-21T08:00:00-05:00"
modified = "2010-06-25T00:03:17-05:00"
slug = "Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Table-of-Contents"
blogengine = "6cb63f7d-8ab2-4b8b-b557-b5d7dec638c2"
categories = ["tutorials / guides"]
tags = ["asp.net", ".net", "c#", "wcf webhttp", "rest", "jquery"]
+++

<p>A while ago (<a href="http://strivinglife.com/words/post/Test-application-in-ASPNET-C-sharp-Amortization-schedule.aspx">a year and a quarter</a>)&nbsp;I created an <a rel="external" href="http://jamesrskemp.com/testing/asp.net/Amortization.aspx">amortization schedule generator</a> in ASP.NET, as an attempt to help me determine when I could expect to have a loan paid off, depending upon how much money I threw at it.</p>
<p>For better or worse, some of the practices I put in place aren't the best, and either way I've been meaning to tweak the interface so that I could do various comparisons. If I pay x dollars more a month, how much faster would I have it paid off? How much would I save in interest? How much am I paying in interest as it is? I also really wanted to work&nbsp;with JSON and jQuery, for practice.</p>
<p>Now that I've found <a href="http://strivinglife.com/words/post/RESTful-WCF-Web-services-easily.aspx">WCF WebHttp</a>, I think I have everything I need to make it happen.</p>
<h3>Final product</h3>
<p>When I'm done I hope to have a WCF WebHttp service that will take a loan and return the total number of payments required to pay the loan off, with interest information. Variables will include the total loan amount, the annual percent, the number of payments per year, and the amount per payment. We'll be able to make requests to the service, via jQuery, and parse out the results for display on a page.</p>
<h3>Tools used</h3>
<p>To develop this I'll be using Visual Studio 2010 Professional, .NET Framework 4, and Windows Server 2008 R2, with&nbsp;jQuery&nbsp;1.4.2. For browser testing&nbsp;I'll be using Internet Explorer 8 and Chrome 5.0.x.</p>
<h3>Steps</h3>
<p>The steps to create this product are listed below, with links to the articles that cover them.</p>
<ol>
<li><a href="http://strivinglife.com/words/post/Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Part-1-Loan-object.aspx">Object determination and creation</a></li>
<li><a href="http://strivinglife.com/words/post/Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Part-2-WCF-WebHttp-service.aspx">Web service determination, creation, and testing</a></li>
<li><a href="http://strivinglife.com/words/post/Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Part-3-Pulling-JSON-with-jQuery.aspx">jQuery implementation and enabling JSON results on our WCF RESTful Web service</a></li>
</ol>
<p>(Steps subject to change/consolidation as articles are written.)</p>
