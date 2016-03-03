+++
title = "Parsing Last.fm Web Services' artist.getSimilar with C# and LINQ to XML"
summary = "How to programmatically make a request to Last.fm's Web Services for similar artists, and parse the response with LINQ to XML, using C# and .NET Framework 3.5"
draft = false
comments = true
date = "2009-09-12T16:33:00-05:00"
modified = "2009-09-12T21:41:09-05:00"
slug = "Parsing-Lastfm-Web-Services-artistgetSimilar-with-C-and-LINQ-to-XML"
blogengine = "cf9297f6-b8d7-4bb5-85b2-b9105b019a5e"
categories = ["article", "tutorials / guides"]
tags = [".net", "c#", "linq to xml", "last.fm"]
+++

<p>The following covers how to parse the XML response of artist.getSimilar, from Last.fm's Web Services.</p>
<h3>Setup and assumptions</h3>
<p>The first step is sign up for a free <a rel="external" href="http://www.last.fm/api">API account at Last.fm</a>.</p>
<p>You'll also need to target .NET Framework 3.5 when you setup your project, so as to access LINQ functionality.</p>
<p>When writing the steps listed below, I was working on a Windows Forms Application, but the steps should be the same, or very similar, for other project types.</p>
<h3>Creating the base class</h3>
<p>The first thing I've done is created a new class file in my project called Lastfm.cs, resulting in the following.</p>
<pre class="code"><code class="csharp">using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace JamesRSkemp.WebServices {
	class Lastfm {
		private const string LastFmApiKey = "EnterYourApiKeyHere";

	}
}</code></pre>
<p>We'll add a new method to the Lastfm class to return the base Url we'll need to make Web service requests.</p>
<pre class="code"><code class="csharp">		/// &lt;summary&gt;
		/// Get the base Url that we'll use to make Web service requests.
		/// &lt;/summary&gt;
		/// &lt;returns&gt;The base Url to use to make Web service requests.&lt;/returns&gt;
		static private string GetBaseRequestUrl() {
			string baseUrl = "http://ws.audioscrobbler.com/2.0/?api_key=" + LastFmApiKey;
			return baseUrl;
		}</code></pre>
<p>Next we'll create a method to make a request to a Web service and return the full response.</p>
<pre class="code"><code class="csharp">		/// &lt;summary&gt;
		/// Gets the data from an HTTP request.
		/// &lt;/summary&gt;
		/// &lt;param name="requestUrl"&gt;The full Url of the request to make.&lt;/param&gt;
		/// &lt;returns&gt;Returns a string with the text returned from the request.&lt;/returns&gt;
		private string GetServiceResponse(string requestUrl) {
			string httpResponse = "";

			HttpWebRequest request = (HttpWebRequest)WebRequest.Create(requestUrl);
			request.Timeout = 15000;
			HttpWebResponse response = null;
			StreamReader reader = null;

			try {
				response = (HttpWebResponse)request.GetResponse();
				reader = new StreamReader(response.GetResponseStream());

				httpResponse = reader.ReadToEnd();
			} finally {
				if (reader != null) {
					reader.Close();
				}
				if (response != null) {
					response.Close();
				}
			}

			return httpResponse;
		}</code></pre>
<p>The following references must also be added.</p>
<pre class="code"><code class="csharp">using System.Net;
using System.IO;</code></pre>
<p>When we use this class, we want to have our data returned in an easy to use format. For ease, we'll have it return a DataTable. We'll have to add the appropriate reference first.</p>
<pre class="code"><code class="csharp">using System.Data;</code></pre>
<p>We can then began our method as follows.</p>
<pre class="code"><code class="csharp">		public DataTable GetSimilarArtists(string artistName) {
			if (String.IsNullOrEmpty(artistName)) {
				throw new Exception("Artist name must be populated.");
			} else {
				string requestUrl = GetBaseRequestUrl();
				requestUrl += "&amp;method=artist.getSimilar&amp;artist=" + System.Web.HttpUtility.UrlEncode(artistName.Trim());

				string serviceResponse = GetServiceResponse(requestUrl);

				DataTable similarArtists = new DataTable();
				
				// TODO

				return similarArtists;
			}
		}</code></pre>
<p>If we were to make a request now, we'd see that the data returned is formatted similar to the following, for a request for <strong>Bruce Springsteen</strong>. (For ease and sanity, data truncated.)</p>
<pre class="code"><code class="xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;lfm status="ok"&gt;
&lt;similarartists artist="Bruce Springsteen"&gt;
&lt;artist&gt;
    &lt;name&gt;Bruce Springsteen &amp; The E Street Band&lt;/name&gt;
    &lt;mbid&gt;5a1283bf-81d5-4700-8919-683eeaaf2beb&lt;/mbid&gt;
    &lt;match&gt;100&lt;/match&gt;
    &lt;url&gt;www.last.fm/music/Bruce%2BSpringsteen%2B%2526%2BThe%2BE%2BStreet%2BBand&lt;/url&gt;
    &lt;image size="small"&gt;http://userserve-ak.last.fm/serve/34/8415485.jpg&lt;/image&gt;
    &lt;image size="medium"&gt;http://userserve-ak.last.fm/serve/64/8415485.jpg&lt;/image&gt;
    &lt;image size="large"&gt;http://userserve-ak.last.fm/serve/126/8415485.jpg&lt;/image&gt;
    &lt;image size="extralarge"&gt;http://userserve-ak.last.fm/serve/252/8415485.jpg&lt;/image&gt;
    &lt;image size="mega"&gt;http://userserve-ak.last.fm/serve/500/8415485/Bruce+Springsteen++The+E+Street+Band+estreet.jpg&lt;/image&gt;
    &lt;streamable&gt;1&lt;/streamable&gt;
&lt;/artist&gt;
[...]
&lt;/similarartists&gt;&lt;/lfm&gt;</code></pre>
<p>We'd first need to add a reference so that we can parse through the returned response.</p>
<pre class="code"><code class="csharp">using System.Xml.Linq;</code></pre>
<p>We can now create our LINQ to XML query to access the similar artist's name and match percentage.</p>
<pre class="code"><code class="csharp">				var xmlResponse = XElement.Parse(serviceResponse);

				// Parse through the returned Xml for the name and match value for each similar artist.
				var artists = from artistsSimilar in xmlResponse.Descendants("artist")
							  select new {
								  name = artistsSimilar.Element("name").Value,
								  match = artistsSimilar.Element("match").Value
							  };</code></pre>
<p>Next we can create the DataTable that we'll use to store the name and math values.</p>
<pre class="code"><code class="csharp">				DataTable similarArtists = new DataTable();
				similarArtists.Columns.Add("Artist");
				similarArtists.Columns.Add("Match", System.Type.GetType("System.Double"));</code></pre>
<p>Finally we can loop through each result returned from our LINQ to XML query, adding a new row to the table, for each.</p>
<pre class="code"><code class="csharp">				if (artists.Count() &gt; 0) {
					DataRow artistsRow;
					foreach (var artist in artists) {
						artistsRow = similarArtists.NewRow();
						artistsRow["Artist"] = artist.name;
						artistsRow["Match"] = artist.match;
						similarArtists.Rows.Add(artistsRow);
					}
				}</code></pre>
<p>Finally we return the populated DataTable.</p>
<pre class="code"><code class="csharp">				return similarArtists;</code></pre>
<p>Assuming a Windows Form Application with a text box (textBox1), a DataGridView (dataGridView1), and a button (button1), we could do the following (assuming the appropriate references have been added).</p>
<pre class="code"><code class="csharp">		private void button1_Click(object sender, EventArgs e) {
			if (!String.IsNullOrEmpty(textBox1.Text)) {
				Lastfm lastFmRequest = new Lastfm();

				DataTable results = lastFmRequest.GetSimilarArtists(textBox1.Text);

				dataGridView1.DataSource = results;
			} else {
				MessageBox.Show("You must enter an artist to continue.");
				textBox1.Focus();
			}
		}</code></pre>
<p>Taken together, that results in the following. (<a rel="download" href="http://media.jamesrskemp.com/articles/JamesRSkemp.WebServices.Lastfm.cs.txt">Download JamesRSkemp.WebServices.Lastfm.cs</a>.)</p>
<pre class="code"><code class="csharp">/*
Created by James Skemp - <a href="http://jamesrskemp.com/">http://jamesrskemp.com/</a>
Version 1.0
More information at http://strivinglife.com/words/post/Parsing-Lastfm-Web-Services-artistgetSimilar-with-C-and-LINQ-to-XML.aspx
Shared under a Creative Commons Attribution 3.0 United States License - http://creativecommons.org/licenses/by/3.0/us/
*/
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;
using System.IO;
using System.Data;
using System.Xml.Linq;

namespace JamesRSkemp.WebServices {
	class Lastfm {
		/// &lt;summary&gt;
		/// Key used to access Last.fm Web services.
		/// &lt;/summary&gt;
		private const string LastFmApiKey = "EnterYourApiKeyHere";

		/// &lt;summary&gt;
		/// Return artists similar to the one passed, with a match percentage.
		/// &lt;/summary&gt;
		/// &lt;param name="artistName"&gt;The name of the artist to use for the request.&lt;/param&gt;
		/// &lt;returns&gt;DataTable with artist names and match percentage, as a Double.&lt;/returns&gt;
		public DataTable GetSimilarArtists(string artistName) {
			if (String.IsNullOrEmpty(artistName)) {
				throw new Exception("Artist name must be populated.");
			} else {
				string requestUrl = GetBaseRequestUrl();
				requestUrl += "&amp;method=artist.getSimilar&amp;artist=" + System.Web.HttpUtility.UrlEncode(artistName.Trim());

				string serviceResponse = GetServiceResponse(requestUrl);

				var xmlResponse = XElement.Parse(serviceResponse);

				// Parse through the returned Xml for the name and match value for each similar artist.
				var artists = from artistsSimilar in xmlResponse.Descendants("artist")
							  select new {
								  name = artistsSimilar.Element("name").Value,
								  match = artistsSimilar.Element("match").Value
							  };

				DataTable similarArtists = new DataTable();
				similarArtists.Columns.Add("Artist");
				similarArtists.Columns.Add("Match", System.Type.GetType("System.Double"));

				if (artists.Count() &gt; 0) {
					DataRow artistsRow;
					foreach (var artist in artists) {
						artistsRow = similarArtists.NewRow();
						artistsRow["Artist"] = artist.name;
						artistsRow["Match"] = artist.match;
						similarArtists.Rows.Add(artistsRow);
					}
				}

				return similarArtists;
			}
		}

		/// &lt;summary&gt;
		/// Get the base Url that we'll use to make Web service requests.
		/// &lt;/summary&gt;
		/// &lt;returns&gt;The base Url to use to make Web service requests.&lt;/returns&gt;
		private string GetBaseRequestUrl() {
			string baseUrl = "http://ws.audioscrobbler.com/2.0/?api_key=" + LastFmApiKey;
			return baseUrl;
		}

		/// &lt;summary&gt;
		/// Gets the data from an HTTP request.
		/// &lt;/summary&gt;
		/// &lt;param name="requestUrl"&gt;The full Url of the request to make.&lt;/param&gt;
		/// &lt;returns&gt;Returns a string with the text returned from the request.&lt;/returns&gt;
		private string GetServiceResponse(string requestUrl) {
			string httpResponse = "";

			HttpWebRequest request = (HttpWebRequest)WebRequest.Create(requestUrl);
			request.Timeout = 15000;
			HttpWebResponse response = null;
			StreamReader reader = null;

			try {
				response = (HttpWebResponse)request.GetResponse();
				reader = new StreamReader(response.GetResponseStream());

				httpResponse = reader.ReadToEnd();
			} finally {
				if (reader != null) {
					reader.Close();
				}
				if (response != null) {
					response.Close();
				}
			}

			return httpResponse;
		}
	}
}</code></pre>
<p>Advanced error handling is missing, but this should give you a basic idea of how you can go about easily accessing Last.fm's Web Services, and parsing returned data.</p>
<h3>Final thoughts</h3>
<p>Questions? Comments? Concerns? Please add a comment below.</p>
<p><strong>Updated 9/12/2009, 15:55:</strong> I was doing it in my implementation, but added simple check for a populated textBox1 to the above code.</p>
