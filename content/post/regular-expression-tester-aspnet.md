+++
title = "Regular Expression tester - ASP.NET"
description = "A regular expression tester, built on ASP.NET 3.5. [slnet0514:c1bcb6bf-9cce-48f2-ba11-ae9afde4a4d3]"
draft = false
comments = true
date = "2008-05-04T21:50:00-05:00"
modified = "2008-05-04T21:48:49-05:00"
slug = "Regular-Expression-tester-ASPNET"
blogengine = "c1bcb6bf-9cce-48f2-ba11-ae9afde4a4d3"
categories = ["tutorials / guides"]
tags = [".net", "c#"]
+++

<p>
I&#39;ve posted code in <a href="/words/post/Regular-Expression-tester-ColdFusion.aspx" target="_blank">ColdFusion</a> and <a href="/words/post/Regular-Expression-tester-JavaScript.aspx" target="_blank">JavaScript</a> for a regular expression tester. Since I&#39;m looking at ASP.NET development ... here&#39;s one built on ASP.NET (3.5, but it should run fine on 2.0), in C#. 
</p>
<h3>RegularExpression.aspx</h3>
<blockquote>
	<p>
	&lt;%@ Page Language=&quot;C#&quot; AutoEventWireup=&quot;true&quot;&nbsp; CodeFile=&quot;RegularExpression.aspx.cs&quot; Inherits=&quot;_Default&quot; %&gt; 
	</p>
	<p>
	&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt; 
	</p>
	<p>
	&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;<br />
	&lt;head runat=&quot;server&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp; &lt;title&gt;ASP.NET 3.5 Regular Expression tester&lt;/title&gt;<br />
	&nbsp;&nbsp;&nbsp; &lt;style type=&quot;text/css&quot;&gt;<br />
	&nbsp;&nbsp;form {<br />
	&nbsp;&nbsp;&nbsp;margin:0;<br />
	&nbsp;&nbsp;&nbsp;padding:0;<br />
	&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;form label, .label_kludge {<br />
	&nbsp;&nbsp;&nbsp;display:block;<br />
	&nbsp;&nbsp;&nbsp;float:left;<br />
	&nbsp;&nbsp;&nbsp;width:180px;<br />
	&nbsp;&nbsp;&nbsp;padding:0;<br />
	&nbsp;&nbsp;&nbsp;margin:5px 0 0;<br />
	&nbsp;&nbsp;&nbsp;text-align:right;<br />
	&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;form input, form textarea, form select {<br />
	&nbsp;&nbsp;&nbsp;width:200px;<br />
	&nbsp;&nbsp;&nbsp;margin:5px 0 0 10px;<br />
	&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;textarea {<br />
	&nbsp;&nbsp;&nbsp;overflow:auto;<br />
	&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;form br {<br />
	&nbsp;&nbsp;&nbsp;clear:left;<br />
	&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;&nbsp; &lt;/style&gt;<br />
	&lt;/head&gt;<br />
	&lt;body&gt;<br />
	&nbsp;&lt;h1&gt;ASP.NET 3.5 Regular Expression Tester&lt;/h1&gt;<br />
	&nbsp;&nbsp;&nbsp; &lt;form id=&quot;form1&quot; runat=&quot;server&quot;&gt;<br />
	&nbsp;&nbsp;&nbsp; &lt;div&gt;<br />
	&nbsp;&nbsp;&nbsp; <br />
	&nbsp;&nbsp;&nbsp; &nbsp;&lt;asp:Label ID=&quot;lbl_RegularExpression&quot; runat=&quot;server&quot; Text=&quot;Regular Expression:&quot; <br />
	&nbsp;&nbsp;&nbsp;AssociatedControlID=&quot;RegularExpression&quot;&gt;&lt;/asp:Label&gt;<br />
	&nbsp;&nbsp;&lt;asp:TextBox ID=&quot;RegularExpression&quot; runat=&quot;server&quot; Width=&quot;350&quot;&gt;&lt;/asp:TextBox&gt;<br />
	&nbsp;&nbsp;&lt;asp:RequiredFieldValidator ID=&quot;RequiredFieldValidator1&quot; runat=&quot;server&quot; <br />
	&nbsp;&nbsp;&nbsp;ControlToValidate=&quot;RegularExpression&quot; Display=&quot;Dynamic&quot; <br />
	&nbsp;&nbsp;&nbsp;ErrorMessage=&quot;You must enter a regular expression.&quot; SetFocusOnError=&quot;True&quot;&gt;You <br />
	&nbsp;&nbsp;must enter a regular expression.&lt;/asp:RequiredFieldValidator&gt;<br />
	&nbsp;&nbsp;&lt;br /&gt;<br />
	&nbsp;&nbsp;&lt;asp:Label ID=&quot;lbl_TestString&quot; runat=&quot;server&quot; Text=&quot;Test String:&quot; <br />
	&nbsp;&nbsp;&nbsp;AssociatedControlID=&quot;TestString&quot;&gt;&lt;/asp:Label&gt;<br />
	&nbsp;&nbsp;&nbsp; <br />
	&nbsp;&nbsp;&nbsp; &nbsp;&lt;asp:TextBox ID=&quot;TestString&quot; runat=&quot;server&quot; Width=&quot;350px&quot;&gt;&lt;/asp:TextBox&gt;<br />
	&nbsp;&nbsp;&lt;asp:RequiredFieldValidator ID=&quot;RequiredFieldValidator2&quot; runat=&quot;server&quot; <br />
	&nbsp;&nbsp;&nbsp;Display=&quot;Dynamic&quot; <br />
	&nbsp;&nbsp;&nbsp;ErrorMessage=&quot;You must enter a string to test the regular expression against.&quot; <br />
	&nbsp;&nbsp;&nbsp;ControlToValidate=&quot;TestString&quot;&gt;You <br />
	&nbsp;&nbsp;must enter a string to test the regular expression against.&lt;/asp:RequiredFieldValidator&gt;<br />
	&nbsp;&nbsp;&lt;br /&gt;<br />
	&nbsp;&nbsp;&lt;asp:Label ID=&quot;lbl_CaseSensitive&quot; runat=&quot;server&quot; Text=&quot;Case Sensitive:&quot; <br />
	&nbsp;&nbsp;&nbsp;AssociatedControlID=&quot;CaseSensitive&quot;&gt;&lt;/asp:Label&gt;<br />
	&nbsp;&nbsp;&lt;asp:CheckBox ID=&quot;CaseSensitive&quot; runat=&quot;server&quot; /&gt;<br />
	&nbsp;&nbsp;&lt;br /&gt;<br />
	&nbsp;&nbsp;&lt;br /&gt;<br />
	&nbsp;&nbsp;&lt;span class=&quot;label_kludge&quot;&gt;&amp;nbsp;&lt;/span&gt;&lt;asp:Button ID=&quot;btn_Test&quot; <br />
	&nbsp;&nbsp;&nbsp;runat=&quot;server&quot; Text=&quot;Test&quot; onclick=&quot;btn_Test_Click&quot; /&gt;<br />
	&nbsp;&nbsp;&lt;br /&gt;<br />
	&nbsp;&nbsp;&lt;asp:Label ID=&quot;lbl_Results&quot; runat=&quot;server&quot;&gt;&lt;/asp:Label&gt;<br />
	&nbsp;&nbsp;&lt;br /&gt;<br />
	&nbsp;&nbsp;&nbsp; <br />
	&nbsp;&nbsp;&nbsp; &lt;/div&gt;<br />
	&nbsp;&nbsp;&nbsp; &lt;/form&gt;<br />
	&lt;/body&gt;<br />
	&lt;/html&gt; 
	</p>
</blockquote>
<h3>RegularExpression.aspx.cs</h3>
<blockquote>
	<p>
	using System;<br />
	using System.Configuration;<br />
	using System.Data;<br />
	using System.Linq;<br />
	using System.Web;<br />
	using System.Web.Security;<br />
	using System.Web.UI;<br />
	using System.Web.UI.HtmlControls;<br />
	using System.Web.UI.WebControls;<br />
	using System.Web.UI.WebControls.WebParts;<br />
	using System.Xml.Linq;<br />
	using System.Text.RegularExpressions; 
	</p>
	<p>
	public partial class _Default : System.Web.UI.Page <br />
	{<br />
	&nbsp;&nbsp;&nbsp; protected void Page_Load(object sender, EventArgs e) {<br />
	&nbsp;&nbsp;if (this.IsPostBack) {<br />
	&nbsp;&nbsp;&nbsp;Boolean MatchCheck;<br />
	&nbsp;&nbsp;&nbsp;if (this.CaseSensitive.Checked) {<br />
	&nbsp;&nbsp;&nbsp;&nbsp;MatchCheck = Regex.IsMatch(this.TestString.Text, this.RegularExpression.Text);<br />
	&nbsp;&nbsp;&nbsp;} else {<br />
	&nbsp;&nbsp;&nbsp;&nbsp;MatchCheck = Regex.IsMatch(this.TestString.Text, this.RegularExpression.Text, RegexOptions.IgnoreCase);<br />
	&nbsp;&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;&nbsp;if (MatchCheck) {<br />
	&nbsp;&nbsp;&nbsp;&nbsp;this.lbl_Results.Text = &quot;Result: match found&quot;;<br />
	&nbsp;&nbsp;&nbsp;} else {<br />
	&nbsp;&nbsp;&nbsp;&nbsp;this.lbl_Results.Text = &quot;Result: no match found&quot;;<br />
	&nbsp;&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;}<br />
	&nbsp;&nbsp;&nbsp; }<br />
	&nbsp;protected void btn_Test_Click(object sender, EventArgs e) {&nbsp;<br />
	&nbsp;}<br />
	} 
	</p>
</blockquote>
<h3>See it in action!</h3>
<p>
Want to see it in action? You can do so on <a href="http://jamesrskemp.com/testing/asp.net/RegularExpression.aspx" target="_blank">JamesRSkemp.com</a>. 
</p>

