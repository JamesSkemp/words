+++
title = "Parsing Yahoo! Music's Artist Web Services with C# and LINQ to XML - Search for artists"
description = "Example of parsing Yahoo! Music's Search for artists Web service method, with C# and LINQ to XML. [slnet0514:3fb52809-c1d8-42e8-9560-7461a68a0020]"
draft = false
comments = true
date = "2009-09-12T21:30:00-05:00"
modified = "2009-09-12T21:40:02-05:00"
slug = "Parsing-Yahoo!-Musics-Artist-Web-Services-with-C-and-LINQ-to-XML-Search-for-artists"
blogengine = "3fb52809-c1d8-42e8-9560-7461a68a0020"
categories = ["article", "tutorials / guides"]
tags = [".net", "c#", "linq to xml", "yahoo! music"]
+++

<p>Similar to my post on <a href="http://strivinglife.com/words/post/Parsing-Lastfm-Web-Services-artistgetSimilar-with-C-and-LINQ-to-XML.aspx">parsing Last.fm's artist.getSimilar</a>, I've been working with Yahoo! Music's Web services today.</p>
<p>Unfortunately, Yahoo!'s services aren't quite as friendly as those made available by Last.fm.</p>
<p>So that I remember, and others don't have to tackle this as well, here's the class I've created. (<a rel="external" href="http://media.jamesrskemp.com/articles/JamesRSkemp.WebServices.YahooMusic.cs.txt">Download JamesRSkemp.WebServices.YahooMusic.cs</a>.)</p>
<pre class="code"><code class="csharp">/*
Created by James Skemp - http://jamesrskemp.com/
Version 1.0
More information at http://strivinglife.com/words/post/Parsing-Yahoo!-Musics-Artist-Web-Services-with-C-and-LINQ-to-XML-Search-for-artists.aspx
Shared under a Creative Commons Attribution 3.0 United States License - http://creativecommons.org/licenses/by/3.0/us/
*/
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;
using System.IO;
using System.Xml.Linq;
using System.Data;

namespace JamesRSkemp.WebServices {
	class YahooMusic {
		/// &lt;summary&gt;
		/// Key used to access Yahoo! Music Web services.
		/// &lt;/summary&gt;
		private string AppId = "";

		/// &lt;summary&gt;
		/// Create a new YahooMusic object.
		/// &lt;/summary&gt;
		/// &lt;param name="appId"&gt;Application ID from Yahoo! Developer Network.&lt;/param&gt;
		public YahooMusic(string appId) {
			if (appId.Trim() != "") {
				AppId = appId;
			} else {
				throw new Exception("You must pass a valid API identifier.");
			}
		}

		/// &lt;summary&gt;
		/// Return artists similar to the one passed, with a match percentage.
		/// &lt;/summary&gt;
		/// &lt;param name="artistName"&gt;The name of the artist to use for the request.&lt;/param&gt;
		/// &lt;returns&gt;DataTable with artist names.&lt;/returns&gt;
		public DataTable GetSimilarArtists(string artistName) {

			string requestUrl = "http://us.music.yahooapis.com/artist/v1/list/search/artist/"
				+ System.Web.HttpUtility.UrlEncode(artistName.Trim())
				+ "?appid=" + AppId + "&amp;response=topsimilar";

			string serviceResponse = GetServiceResponse(requestUrl);

			var xmlResponse = XElement.Parse(serviceResponse);

			var artistsCount = from Artists in xmlResponse.Descendants("TopSimilarArtists").Descendants("Artist")
							   select new {
								   name = Artists.Attribute("name").Value
							   };

			DataTable similarArtists = new DataTable();
			similarArtists.Columns.Add("Artist");

			if (artistsCount.Count() &gt; 0) {
				DataRow artistsRow;

				foreach (var artist in artistsCount) {
					artistsRow = similarArtists.NewRow();
					artistsRow["Artist"] = artist.name;
					similarArtists.Rows.Add(artistsRow);
				}
			}

			return similarArtists;
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
<p>One issue I do have is that I can't figure out how to get the count attribute off the root element that's returned. Try and search as I might, I can't figure it out.</p>
