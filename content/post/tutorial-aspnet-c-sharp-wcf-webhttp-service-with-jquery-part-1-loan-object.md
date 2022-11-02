+++
title = "Tutorial: ASP.NET (C#) WCF WebHttp service with jQuery: Part 1 - Loan object"
description = "In this tutorial, leading up to a WCF WebHttp service that can be queried with jQuery, we create a simple loan object, with associated methods."
draft = false
comments = true
date = "2010-06-22T21:15:00-05:00"
modified = "2010-06-22T21:39:52-05:00"
slug = "Tutorial-ASPNET-C-sharp-WCF-WebHttp-service-with-jQuery-Part-1-Loan-object"
blogengine = "42b930de-fe0a-4c32-903a-de043b843ffb"
categories = ["tutorials / guides"]
tags = ["asp.net", ".net", "c#"]
+++

> See the <a href="/post/tutorial-aspnet-c-sharp-wcf-webhttp-service-with-jquery-table-of-contents/">table of contents</a> for more information.

<p>As already noted in the table of contents, the end goal will to have a service that returns enough information to be able to generate an amortization&nbsp;schedule for a loan. I'm not in financial services, and haven't been very good in math since some point in high school, but this seems to work fairly well.</p>
<p>The first thing we're going to do is generate an assembly that we'll then use in the WCF WebHttp service. We'll then create a service that works with this, and finally the jQuery to get information out of the service and display it.</p>

## Defining the loan object
<p>A loan consists of a total amount due, an amount paid per payment, the number of payments made&nbsp; and the interest rate, per year. While not necessary, since we may want multiple loans to be available at once, we'll also say that loans can have a name, or description.</p>
<p>While Decimal may be better, that gives us something like this for our class.</p>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Data;

namespace JamesRSkemp.Formulas {
	public class Amortization {

		/// <summary>
		/// Loan, with a total amount due, payment amount, number of payments per year, and interest rate per year.
		/// </summary>
		public class Loan {
			/// <summary>
			/// Name of the loan.
			/// </summary>
			public String Name { get; set; }
			/// <summary>
			/// Total amount due on the loan.
			/// </summary>
			public Double Total { get; set; }
			/// <summary>
			/// The amount paid per payment.
			/// </summary>
			public Double PaymentAmount { get; set; }
			/// <summary>
			/// The number of payments made per year. Usually 12.
			/// </summary>
			public int PaymentsPerYear { get; set; }
			/// <summary>
			/// Percent of interest, per year.
			/// </summary>
			public Double InterestPerYear { get; set; }
			/// <summary>
			/// List of individual payments. Only populated/updated by UpdatePayments method.
			/// </summary>
			public List<Payment> Payments { get; set; }

			/// <summary>
			/// Creates a new instance of a loan. By default sets the number of payments per year to 12.
			/// </summary>
			public Loan() {
				this.PaymentsPerYear = 12;
			}
		}
	}
}
```

You'll notice that I'm setting the number of payments per year to 12 when the object is initialized, as most loans tend to follow that.

We have payments defined separately, which I've defined as follows.

```csharp
/// <summary>
/// Loan payment.
/// </summary>
public class Payment {
	/// <summary>
	/// Total payment amount.
	/// </summary>
	public Double Total { get; set; }
	/// <summary>
	/// Amount of payment applied to interest.
	/// </summary>
	public Double Interest { get; set; }
	/// <summary>
	/// Amount of payment applied to the principal.
	/// </summary>
	public Double Principal { get; set; }
	/// <summary>
	/// Amount of the loan remaining after this payment is made.
	/// </summary>
	public Double LoanRemaining { get; set; }
	/// <summary>
	/// New loan payment.
	/// </summary>
	public Payment() {
	}
}
```

You can see that I've assumed a payment will have a total amount paid, with what amount went towards interest and what towards the principal. For tracking ease, I've also put the loan's remaining amount on the payment as well, although this isn't really necessary. Of course, we don't have a date associated with the payment (which might be a good idea for expansion purposes), so perhaps it is.

Now we have to come up with some way to populate the payments. For this purpose I've added a method to Loan object which allows the payments to be populated, or updated.

```csharp
/// <summary>
/// Updates payments on a loan.
/// </summary>
/// <returns>If payments cannot be updated, returns false.</returns>
public Boolean UpdatePayments() {
	Boolean paymentsUpdated = false;

	if (this.Payments == null) {
		this.Payments = new List<Payment>();
	} else {
		this.Payments.Clear();
	}

	// Determine how much interest should be applied per payment.
	Double interestPerPayment = (this.InterestPerYear / 100) / this.PaymentsPerYear;

	// Store how much we need to pay. In this case, what the first payment will be.
	Double periodPaymentAmount = interestPerPayment * this.Total;

	if (periodPaymentAmount >= this.PaymentAmount) {
		throw new Exception("The amount of interest on the first payment is greater than the amount that will be paid.");
	} else {
		Double totalRemaining = this.Total;

		while (totalRemaining > 0) {
			Payment currentPayment = new Payment();
			currentPayment.Total = this.PaymentAmount;
			currentPayment.Interest = Math.Round(totalRemaining * interestPerPayment, 2);
			currentPayment.Principal = Math.Round(currentPayment.Total - currentPayment.Interest, 2);
			currentPayment.LoanRemaining = Math.Round(totalRemaining - currentPayment.Principal, 2);
						// If we now have a remaining amount on the loan less than 0, we've paid too much.

			if (currentPayment.LoanRemaining < 0) {
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
}
```

<p>You can see that this clears any existing payment information, then loops through and generates a list of payments, which are then associated with the loan. In case the remaining amount due is less than 0, we take that from the payment amount and principal paid to zero the loan.</p>

## Testing this out
<p>At this point you're more than willing to create a simple command-line client that references this assembly. You can also grab a copy of <a rel="external download" href="https://media.jamesrskemp.com/articles/JamesRSkemp.Formulas.Amortization.cs.txt">JamesRSkemp.Formulas.Amortization</a> online, and compare results with a slightly different version that I use in my <a rel="external" href="http://jamesrskemp.com/testing/asp.net/Amortization.aspx">amortization schedule generator</a>.</p>

## Next time ...
<p>Now that we have this assembly ready we can look at the next piece, which will be to generate the WCF WebHttp service that actually makes use of this.</p>
