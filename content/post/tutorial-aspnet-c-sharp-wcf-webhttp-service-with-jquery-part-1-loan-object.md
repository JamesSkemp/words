+++
title = "Tutorial: ASP.NET (C#) WCF WebHttp service with jQuery: Part 1 - Loan object"
summary = "In this tutorial, leading up to a WCF WebHttp service that can be queried with jQuery, we create a simple loan object, with associated methods."
draft = false
comments = true
date = "2010-06-22T21:15:00-05:00"
modified = "2010-06-22T21:39:52-05:00"
slug = "Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Part-1-Loan-object"
blogengine = "42b930de-fe0a-4c32-903a-de043b843ffb"
categories = ["tutorials / guides"]
tags = ["asp.net", ".net", "c#"]
+++

<div class="note">
<p>See the <a href="http://strivinglife.com/words/post/Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Table-of-Contents.aspx">table of contents</a> for more information.</p>
</div>
<p>As already noted in the table of contents, the end goal will to have a service that returns enough information to be able to generate an amortization&nbsp;schedule for a loan. I'm not in financial services, and haven't been very good in math since some point in high school, but this seems to work fairly well.</p>
<p>The first thing we're going to do is generate an assembly that we'll then use in the WCF WebHttp service. We'll then create a service that works with this, and finally the jQuery to get information out of the service and display it.</p>
<h3>Defining the loan object</h3>
<p>A loan consists of a total amount due, an amount paid per payment, the number of payments made&nbsp; and the interest rate, per year. While not necessary, since we may want multiple loans to be available at once, we'll also say that loans can have a name, or description.</p>
<p>While Decimal may be better, that gives us something like this for our class.</p>
<pre class="code"><code class="csharp">using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Data;

namespace JamesRSkemp.Formulas {
	public class Amortization {

		/// &lt;summary&gt;
		/// Loan, with a total amount due, payment amount, number of payments per year, and interest rate per year.
		/// &lt;/summary&gt;
		public class Loan {
			/// &lt;summary&gt;
			/// Name of the loan.
			/// &lt;/summary&gt;
			public String Name { get; set; }
			/// &lt;summary&gt;
			/// Total amount due on the loan.
			/// &lt;/summary&gt;
			public Double Total { get; set; }
			/// &lt;summary&gt;
			/// The amount paid per payment.
			/// &lt;/summary&gt;
			public Double PaymentAmount { get; set; }
			/// &lt;summary&gt;
			/// The number of payments made per year. Usually 12.
			/// &lt;/summary&gt;
			public int PaymentsPerYear { get; set; }
			/// &lt;summary&gt;
			/// Percent of interest, per year.
			/// &lt;/summary&gt;
			public Double InterestPerYear { get; set; }
			/// &lt;summary&gt;
			/// List of individual payments. Only populated/updated by UpdatePayments method.
			/// &lt;/summary&gt;
			public List&lt;Payment&gt; Payments { get; set; }

			/// &lt;summary&gt;
			/// Creates a new instance of a loan. By default sets the number of payments per year to 12.
			/// &lt;/summary&gt;
			public Loan() {
				this.PaymentsPerYear = 12;
			}
		}
	}
}</code></pre>
<p>You'll notice that I'm setting the number of payments per year to 12 when the object is initialized, as most loans tend to follow that.</p>
<p>We have payments defined separately, which I've defined as follows.</p>
<pre class="code"><code class="csharp">/// &lt;summary&gt;
/// Loan payment.
/// &lt;/summary&gt;
public class Payment {
	/// &lt;summary&gt;
	/// Total payment amount.
	/// &lt;/summary&gt;
	public Double Total { get; set; }
	/// &lt;summary&gt;
	/// Amount of payment applied to interest.
	/// &lt;/summary&gt;
	public Double Interest { get; set; }
	/// &lt;summary&gt;
	/// Amount of payment applied to the principal.
	/// &lt;/summary&gt;
	public Double Principal { get; set; }
	/// &lt;summary&gt;
	/// Amount of the loan remaining after this payment is made.
	/// &lt;/summary&gt;
	public Double LoanRemaining { get; set; }
	/// &lt;summary&gt;
	/// New loan payment.
	/// &lt;/summary&gt;
	public Payment() {
	}
}</code></pre>
<p>You can see that I've assumed a payment will have a total amount paid, with what amount went towards interest and what towards the principal. For tracking ease, I've also put the loan's remaining amount on the payment as well, although this isn't really necessary. Of course, we don't have a date associated with the payment (which might be a good idea for expansion purposes), so perhaps it is.</p>
<p>Now we have to come up with some way to populate the payments. For this purpose I've added a method to Loan object which allows the payments to be populated, or updated.</p>
<pre class="code"><code class="csharp">/// &lt;summary&gt;
/// Updates payments on a loan.
/// &lt;/summary&gt;
/// &lt;returns&gt;If payments cannot be updated, returns false.&lt;/returns&gt;
public Boolean UpdatePayments() {
	Boolean paymentsUpdated = false;

	if (this.Payments == null) {
		this.Payments = new List&lt;Payment&gt;();
	} else {
		this.Payments.Clear();
	}

	// Determine how much interest should be applied per payment.
	Double interestPerPayment = (this.InterestPerYear / 100) / this.PaymentsPerYear;

	// Store how much we need to pay. In this case, what the first payment will be.
	Double periodPaymentAmount = interestPerPayment * this.Total;

	if (periodPaymentAmount &gt;= this.PaymentAmount) {
		throw new Exception("The amount of interest on the first payment is greater than the amount that will be paid.");
	} else {
		Double totalRemaining = this.Total;

		while (totalRemaining &gt; 0) {
			Payment currentPayment = new Payment();
			currentPayment.Total = this.PaymentAmount;
			currentPayment.Interest = Math.Round(totalRemaining * interestPerPayment, 2);
			currentPayment.Principal = Math.Round(currentPayment.Total - currentPayment.Interest, 2);
			currentPayment.LoanRemaining = Math.Round(totalRemaining - currentPayment.Principal, 2);
						// If we now have a remaining amount on the loan less than 0, we've paid too much.

			if (currentPayment.LoanRemaining &lt; 0) {
				currentPayment.Total += currentPayment.LoanRemaining;
				currentPayment.Principal += currentPayment.LoanRemaining;
				currentPayment.LoanRemaining = 0;
			}

			this.Payments.Add(currentPayment);

			totalRemaining = currentPayment.LoanRemaining;
			currentPayment = null;
		}
		paymentsUpdated = true;
	}

	return paymentsUpdated;
}</code></pre>
<p>You can see that this clears any existing payment information, then loops through and generates a list of payments, which are then associated with the loan. In case the remaining amount due is less than 0, we take that from the payment amount and principal paid to zero the loan.</p>
<h3>Testing this out</h3>
<p>At this point you're more than willing to create a simple command-line client that references this assembly. You can also grab a copy of <a rel="external download" href="http://media.jamesrskemp.com/articles/JamesRSkemp.Formulas.Amortization.cs.txt">JamesRSkemp.Formulas.Amortization</a> online, and compare results with a slightly different version that I use in my <a rel="external" href="http://jamesrskemp.com/testing/asp.net/Amortization.aspx">amortization schedule generator</a>.</p>
<h3>Next time ...</h3>
<p>Now that we have this assembly ready we can look at the next piece, which will be to generate the WCF WebHttp service that actually makes use of this.</p>
