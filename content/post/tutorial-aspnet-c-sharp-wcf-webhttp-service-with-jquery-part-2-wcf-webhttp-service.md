+++
title = "Tutorial: ASP.NET (C#) WCF WebHttp service with jQuery: Part 2 - WCF WebHttp service"
description = "In this tutorial, leading up to a WCF WebHttp service that can be queried with jQuery, we use a WCF WebHttp template to quickly create a RESTful Web service, with a method to return loans for set data."
draft = false
comments = true
date = "2010-06-24T08:00:00-05:00"
modified = "2010-06-24T22:17:26-05:00"
slug = "Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Part-2-WCF-WebHttp-service"
blogengine = "06d05ffb-a004-46b1-85f7-bab92d8d8753"
categories = ["tutorials / guides"]
tags = ["asp.net", ".net", "c#", "wcf webhttp", "rest"]
+++

<div class="note">
<p>See the <a href="http://strivinglife.com/words/post/Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Table-of-Contents.aspx">table of contents</a> for more information.</p>
</div>
<p>In the last part we created a Loan object, that we determined we would later use to power our Web service. Ths object has a handful of properties and a method to update a list of payments to bring the loan to $0.</p>
<p>This time we're going to create a Web service to respond to requests from data.</p>
<h3>Requirements</h3>
<p>As this seems to be built for .NET Framework 4, you'll want to be running Visual Studio 2010 and .NET Framework 4.</p>
<p>You'll also want to add the WCF REST Service Template 40(CS) to Visual Studio 2010. You can install this by going to Tools &gt; Extension Manager &gt; Online Gallery &gt; Templates &gt; WCF. You can also view more information about this template in the <a rel="external" href="http://visualstudiogallery.msdn.microsoft.com/en-us/fbc7e5c1-a0d2-41bd-9d7b-e54c845394cd">Visual Studio Gallery</a>.</p>
<h3>Modifying the WCF template</h3>
<p>With the WCF REST Service Template installed you can create a new project and select the template from Online Templates.</p>
<p>You can go ahead and build the template and give it a quick run, just to see how it behaves. With this template, our work is going to be cut significantly in half.</p>
<p>With the project ready, go ahead and either add a reference to the built assembly from part 1, or add the class directly.</p>
<p>Now we'll create a new class for our new service (I've opted to call mine FormulasService.cs) and using the default Service1.cs, add in the necessary references.</p>
<pre class="code"><code class="csharp">using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;
using System.ComponentModel;
// depending upon your assembly name, this may be different
using JamesRSkemp.Formulas;</code></pre>
<p>You'll also want to make sure your class has the appropriate attributes.</p>
<pre class="code"><code class="csharp">	[ServiceContract]
	[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
	[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]</code></pre>
<p>Next we'll register the service by opening Global.asax.cs and adding the following, with the string value and typeof&nbsp;dependent upon what you've decided to call your service.</p>
<pre class="code"><code class="csharp">RouteTable.Routes.Add(new ServiceRoute("FormulasService", new WebServiceHostFactory(), typeof(FormulasService)));</code></pre>
<p>Now that our references are added and our route is registered we can try browsing to our service. However, a service must have at least one method, so we'll create a dummy one.</p>
<pre class="code"><code class="csharp">		// todo - remove
		// need at least one method - may as well create a dummy one for validation
		[WebGet(UriTemplate = "Dummy")]
		[Description("Dummy operation.")]
		public String DummyMethod() {
			return "It works.";
		}</code></pre>
<p>Now if we build and start our project we should be able to browse to http://localhost:50996/FormulasService/help&nbsp;and http://localhost:50996/FormulasService/Dummy (swapping out the port accordingly) to see the wonderful documentation that's built into WCF WebHttp services, and our own method.</p>
<p>I've left in some todo items that you can complete later, but now that we've validated things are running okay, we can go ahead and add a new method, such as the following.</p>
<pre class="code"><code class="csharp">[WebGet(UriTemplate = "Loan?name={name}&amp;total={amount}&amp;payment={payment}&amp;yearlyPayments={paymentsPerYear}&amp;yearlyInterest={interestPerYear}")]
[Description("Create a new loan with set properties")]
public Amortization.Loan CreateLoan(String name, String amount, String payment, String paymentsPerYear, String interestPerYear) {
	Double loanAmount, loanPayment, loanInterest;
	int loanPaymentsPerYear;

	Double.TryParse(amount, out loanAmount);
	Double.TryParse(payment, out loanPayment);
	int.TryParse(paymentsPerYear, out loanPaymentsPerYear);
	Double.TryParse(interestPerYear, out loanInterest);

	// todo - validation of items &gt; 0

	// todo - validation that the loan terms make sense (interest &lt; payments)

	// If everything looks okay, create a new loan.
	Amortization.Loan newLoan = new Amortization.Loan();
	newLoan.Name = name;
	newLoan.Total = loanAmount;
	newLoan.PaymentAmount = loanPayment;
	newLoan.PaymentsPerYear = loanPaymentsPerYear;
	newLoan.InterestPerYear = loanInterest;

	try {
		newLoan.UpdatePayments();
	} catch (Exception ex) {
		newLoan.Name = ex.Message + " | " + ex.StackTrace;
		// todo, throw appropriate error here
	}

	return newLoan;
}</code></pre>
<p>As you can see, I'm allowing GET requests, and am having them pass everything we need to generate a loan, with payments. Note that the method uses strings instead of the appropriate type. Feel free to modify this, but the service <em>will</em> throw an error.</p>
<p>Build and start the project and you should be able to browse to http://localhost:50996/FormulasService/Loan?name=asdf&amp;total=4956.24&amp;payment=97.85&amp;yearlyPayments=12&amp;yearlyInterest=4.25 (changing the port as needed) to view returned data, in XML format.</p>
<p>If we'd prefer, we can change this to return JSON instead, either by adding an attribute or modifying the standardEndpoint element in Web.config, by adding something like defaultOutgoingResponseFormat="Json".</p>
<p>For more information on how this works, read <a rel="external" href="http://blogs.msdn.com/b/endpoint/archive/2010/01/18/automatic-and-explicit-format-selection-in-wcf-webhttp-services.aspx">Automatic and Explicit Format Selection in WCF WebHttp Services</a>.</p>
<h3>Next time ...</h3>
<p>Now that we have a working WCF WebHttp service, that responds to GET requests with XML data, we can look at how we can interact with this service with jQuery, and have the service return JSON results.</p>
