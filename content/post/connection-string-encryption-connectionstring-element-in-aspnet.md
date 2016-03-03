+++
title = "Connection String encryption (connectionString element) in ASP.NET"
summary = "ASP.NET can encrypt a connection string, whether it be stored in Web.config or a file determined by the configSource attribute."
draft = false
comments = true
date = "2010-02-01T22:10:00-06:00"
modified = "2010-02-01T22:12:35-06:00"
slug = "Connection-String-encryption-connectionString-element-in-ASPNET"
blogengine = "b23c8e76-af5f-4e1e-9813-9abd43dfb3c9"
categories = ["tutorials / guides"]
tags = ["asp.net"]
+++

<p>From what I've been able to determine, setting up an ODBC connection in Windows and using that for ASP.NET generally seems to be frowned upon. Instead, ASP.NET uses a Web.config&nbsp;file to store a number of settings, including all the connection strings you'll be using (whether you're using Windows authentication or user names and passwords).</p>
<p>For example:</p>
<pre class="code"><code class="xml">&lt;?xml version="1.0"?&gt;
&lt;configuration&gt;
	&lt;appSettings/&gt;
	&lt;connectionStrings&gt;
		&lt;add name="TestDatabase001Reader" connectionString="Data Source=192.168.56.102,1433;Initial Catalog=TestingDatabase001;User Id=DataReader;Password=DataReader" providerName="System.Data.SqlClient"/&gt;
	&lt;/connectionStrings&gt;
	&lt;system.web&gt;
		...
	&lt;/system.web&gt;
&lt;/configuration&gt;</code></pre>
<p>However, it's also possible to store the connection strings in a completely different file by tweaking the connectionString in Web.config like so:</p>
<pre class="code"><code class="xml">&lt;connectionStrings configSource="ConnectionStrings.config"&gt;
&lt;/connectionStrings&gt;</code></pre>
<p>Then ConnectionStrings.config would be created and consist of the following:</p>
<pre class="code"><code class="xml">&lt;?xml version="1.0"?&gt;
&lt;connectionStrings&gt;
	&lt;add name="TestDatabase001Reader" connectionString="Data Source=192.168.56.102,1433;Initial Catalog=TestingDatabase001;User Id=DataReader;Password=DataReader" providerName="System.Data.SqlClient"/&gt;
&lt;/connectionStrings&gt;</code></pre>
<p>The problem arises when the Web.config file is compromised, either by pushing it without a .config extension, sending it to someone else, or someone having browse access your Web site's directory. How do you encrypt these connection strings, and can you do so if you decide to store them in a separate file?</p>
<p>The following is how to verify that either way works just fine.</p>
<h3>SqlConnectionEncryption.aspx</h3>
<pre class="code"><code class="csharp">&lt;%@ Page Language="C#" AutoEventWireup="true" CodeBehind="SqlConnectionEncryption.aspx.cs" Inherits="WebApplication1.SqlConnectionEncryption" %&gt;

&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml" &gt;
&lt;head runat="server"&gt;
    &lt;title&gt;SQL Connection Encryption example&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;form id="form1" runat="server"&gt;
    &lt;div&gt;
		&lt;asp:GridView ID="GridView1" runat="server"&gt;
		&lt;/asp:GridView&gt;
		&lt;div id="Options" runat="server"&gt;&lt;/div&gt;
    &lt;/div&gt;
    &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
<h3>SqlConnectionEncryption.aspx.cs</h3>
<pre class="code"><code class="csharp">using System;
using System.Collections;
using System.Configuration;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Security;
using System.Web.UI;
using System.Web.UI.HtmlControls;
using System.Web.UI.WebControls;
using System.Web.UI.WebControls.WebParts;
using System.Xml.Linq;
using System.Data.SqlClient;
using System.Web.Configuration;

namespace WebApplication1 {
	public partial class SqlConnectionEncryption : System.Web.UI.Page {
		protected void Page_Load(object sender, EventArgs e) {

			string action = Request.QueryString["action"];

			Options.InnerHtml = "";

			DataTable results = new DataTable();

			using (SqlConnection connection = new SqlConnection()) {
				connection.ConnectionString = ConfigurationManager.ConnectionStrings["TestDatabase001Reader"].ToString();
				SqlCommand command = new SqlCommand();
				command.Connection = connection;
				command.CommandText = "SELECT * FROM NameTable";
				command.CommandType = CommandType.Text;

				connection.Open();
				results.Load(command.ExecuteReader());
				connection.Close();
			}

			if (results.Rows.Count &gt; 0) {
				GridView1.DataSource = results;
				GridView1.DataBind();
			}

			Configuration config = WebConfigurationManager.OpenWebConfiguration(Request.ApplicationPath);
			ConfigurationSection configSection = config.GetSection("connectionStrings");

			if (!configSection.SectionInformation.IsProtected) {
				configSection.SectionInformation.ProtectSection("RsaProtectedConfigurationProvider");
				config.Save();
				Options.InnerHtml += "Configuration encrypted.&lt;br /&gt;";
			} else {
				//configSection.SectionInformation.UnprotectSection();
				//config.Save();
				//Options.InnerHtml += "Configuration unencrypted.&lt;br /&gt;";
				Options.InnerHtml += "Configuration already encrypted.&lt;br /&gt;";
			}

			Options.InnerHtml += "Web configuration path: " + config.FilePath + "&lt;br /&gt;";
			Options.InnerHtml += "Section path: " + configSection.ElementInformation.Source + "&lt;br /&gt;";
			Options.InnerHtml += "&lt;br /&gt;";
		}
	}
}</code></pre>
<p>Depending upon your Web.config setup, you'll either see Web.config for both, or Web.config for one and ConnectionStrings.config for the other.</p>
