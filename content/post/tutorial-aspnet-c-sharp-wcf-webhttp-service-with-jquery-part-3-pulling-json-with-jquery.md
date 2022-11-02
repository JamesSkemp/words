+++
title = "Tutorial: ASP.NET (C#) WCF WebHttp service with jQuery: Part 3 - Pulling JSON with jQuery"
description = "In this tutorial, leading up to a WCF WebHttp service that can be queried with jQuery, we complete our tutorial by modifying the WCF service to return JSON data to jQuery requests, and output that information to users."
draft = false
comments = true
date = "2010-06-25T08:00:00-05:00"
modified = "2010-07-12T08:22:22-05:00"
slug = "Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Part-3-Pulling-JSON-with-jQuery"
blogengine = "2e4b01d3-0956-4b5e-99f6-69fc7159881f"
categories = ["tutorials / guides"]
tags = ["asp.net", ".net", "c#", "wcf webhttp", "rest", "jquery", "json"]
+++

> See the <a href="/post/tutorial-aspnet-c-sharp-wcf-webhttp-service-with-jquery-table-of-contents/">table of contents</a> for more information.

<p>In this series we've started with a new loan class, that contains information about a loan, including the total amount due, how much is to be paid per payment, the interest rate, and etcetera. A method is available that will generate information about the number of payments required to pay off the loan.</p>
<p>In the second part we created a WCF WebHttp service, or a WCF REST service, to use the class/assembly from that loan object and return XML data for GET requests.</p>
<p>In this final part we'll be using jQuery to request information from the service, in JSON format, and display that information to users.</p>

## Why JSON?

<p>For maximum flexibility, and because I myself will be hosting the services on their own domain/sub-domain, we'll be taking advantage of jQuery's ability to make JSONP - JSON with Padding - requests, allowing us to pull data, no matter what our domain.</p>

## Getting started with jQuery

<p>jQuery is such an advanced library that I can't cover much in this article. See <a rel="external" href="http://jquery.com/">the official jQuery site</a> for more information, including tutorials. For our purposes you'll want to download a copy of&nbsp;jQuery 1.4.2 (or whatever the current release is, assuming things haven't changed too terribly since the time of this writing) for production.</p>
<p>We'll then create a very simple HTML page that we'll modify for our tutorial.</p>

```xml
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
	<title>Test page</title>
</head>
<body>
	<div id="pulledData">
	</div>
<script type="text/javascript" src="http://media.jamesrskemp.com/js/jquery-1.4.2.min.js"></script>
<script type="text/javascript">
	function processData(data) {
		try {
			// JavaScript will go either here - in the *function*
		} catch (ex) {
			alert("Error: " + ex.Message);
		}
	}

	try {
		if ($) {
			// or JavaScript will go here - in the *request*
		}
	} catch (ex) {
		alert("Error: " + ex.Message);
	}
</script>
</body>
</html>
```

## Verifying the service can be called with jQuery, on the same domain

<p>With our base jQuery file, let's verify the Web service, by making a simple request for a loan: <a href="http://localhost:49821/FormulasService/Loan?name=asdf&amp;total=4956.24&amp;payment=97.85&amp;yearlyPayments=12&amp;yearlyInterest=4.25">http://localhost:49821/FormulasService/Loan?name=asdf&amp;total=4956.24&amp;payment=97.85&amp;yearlyPayments=12&amp;yearlyInterest=4.25</a> (remember to change the port as needed). Assuming this is running fine, which it should be, we can move onto attempting to query this with jQuery.</p>
<p>In the same project as the above service, add our base html file, from above, and add the following to the second block, making sure that the port is correct.</p>

```javascript
$.ajax({
	type: "GET",
	url: 'http://localhost:49821/FormulasService/Loan?name=asdf&amp;total=4956.24&amp;payment=97.85&amp;yearlyPayments=12&amp;yearlyInterest=4.25',
	dataType: 'xml',
	success: function (data) { processData(data); }
});
```

Then add the following to the function.

```javascript
alert('hey');
```

<p>So in our first block we're calling the service once the page is ready, and our function on success. The function then gives a very simple alert, so we easily know that the call has succeeded. If we run this on the same domain (localhost and a port), we should get the alert message. However, opening it by itself (by double-clicking on it in Windows Explorer) will result in no messages at all.</p>
<p>Let's tweak this now to use JSON instead. Tweak the second block so that the dataType line is as follows.</p>

```javascript
dataType: 'json',
```

<p>In our function, add, or replace the existing alert, with the following:</p>

```javascript
alert('Loan name: ' + data.Name);
```

<p>Depending upon the name you've given the loan, you should see an alert message in Chrome or Firefox, with that name. However, if we now try to open this from a different domain, or just via Windows Explorer, we'll see that our loan name is undefined. If we were to look at the response returned from the service, we'd see it's blank.</p>

## JSONP

<p>Now let's update the dataType once again.</p>

```javascript
dataType: 'jsonp',
```

<p>Refresh now and nothing happens, on anything. However, if we were to take a look at the response we'd see that in fact something is returned, it just happens to be XML, which doesn't help us here. And if we switch the dataType to xml, now we can't use it cross-domain (not to mention we lose out on JSON).</p>

## The fix

<p>The fix, found after hours of research and changing settings, requires modifications to our service.</p>
<p>First, let's change the dataType back to JSONP. Since our request no longer passed application/json as an accept-header, the Web service returns the default format, which happens to be XML, which in turn means nothing works. But we can switch the default format type.</p>
<p>Open Web.config in the service and modify the lone standardEndpoint element to the following.</p>

```xml
<standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true" defaultOutgoingResponseFormat="Json"/>
```

<p>The important part is the new attribute at the end. Build the service and test it again and you'll find that the jQuery called from the same server now works, while the jQuery from a different domain does not.</p>
<p>So we're close, but not quite there.</p>

## Localhost no longer

<p>Unfortunately, this is where we can no longer test locally. The missing item is the crossDomainScriptAccessEnabled attribute on the standardEndpoint element.</p>

```xml
<standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true" defaultOutgoingResponseFormat="Json" crossDomainScriptAccessEnabled="true"/>
```

<p>Since we're authenticated, however, this will horribly fail, which can be shown by just browsing to the service via http://localhost:49821/FormulasService/Loan?name=asdf&amp;total=4956.24&amp;payment=97.85&amp;yearlyPayments=12&amp;yearlyInterest=4.25 and getting a message&nbsp;that "Cross domain javascript callback is not supported in authenticated services."</p>
<p>If you have a server that supports it, go ahead and build the service and push it, with those two new attributes. If you don't, change your jQuery url so that it points to services.jamesrskemp.com, and change the name parameter to your email. (Obviously, if you've pushed the service to your own server, go ahead and use your domain in place of mine.)</p>

> Update: Of course, we can also switch off authentication and be able to access this via localhost again. Just add the following to your Web.config within the System.Web element.
> ```xml
> <authentication mode="None"/>
> ```

<p>With that done you can now refresh either the copy on the same domain, or a local copy, and have the service return the loan name passed.</p>
<p>Now we can modify our function as follows, to get a semi-nice output:</p>

```javascript
var outputContent = "";
outputContent += "Loan name: " + data.Name + "<br />";
outputContent += "Starting balance: " + data.Total + "<br />";

$.each(data.Payments, function (i, payment) { outputContent += "After a payment of " + payment.Total + ", the remaining amount is $" + payment.LoanRemaining + "<br />";});

$('#pulledData').html(outputContent);
```

You can <a rel="external" href="https://media.jamesrskemp.com/articles/ServiceExamples/FormulasService_Loan.htm">see this in action</a>&nbsp;on my media sub-domain,&nbsp;with possible improvements after this article is finished.

And with that, you should have more than enough information to get cracking on your own services, with your own jQuery implementations.
