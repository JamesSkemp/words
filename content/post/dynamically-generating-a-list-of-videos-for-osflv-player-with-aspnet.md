+++
title = "Dynamically generating a list of videos for OSFLV Player with ASP.NET"
description = "Sample code to use ASP.NET and OSFLV Player version 3 to dynamically pull a listing of Flash videos from a directory, and allow Web viewing."
draft = false
comments = true
date = "2010-04-13T08:20:00-05:00"
modified = "2010-04-13T08:35:37-05:00"
slug = "Dynamically-generating-a-list-of-videos-for-OSFLV-Player-with-ASPNET"
blogengine = "7e3c7822-ea19-4097-839c-8d40d45e8bc3"
categories = ["tutorials / guides"]
tags = ["asp.net", "flash"]
+++

<p>I've had this code for a while, but here's some simple code to pull a listing of Flash videos (FLV) from a directory, display them in a drop down, and have a video player dynamically generated based on what's picked.</p>
<p>This uses OSFLV Player, version 3 specifically, but can be tweaked for the current (as of this post) version 4.0.</p>
<h3>Default.aspx</h3>
<pre class="code"><code class="html">&lt;%@ Page Language="C#" AutoEventWireup="true"  CodeFile="Default.aspx.cs" Inherits="_Default" %&gt;

&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head runat="server"&gt;
    &lt;title&gt;FLV video player&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;form id="form1" runat="server"&gt;
    &lt;div&gt;
		&lt;a href="Default.aspx"&gt;Refresh listing&lt;/a&gt;&lt;br/&gt;
		&lt;asp:DropDownList ID="DropDownList1" runat="server"&gt;
		&lt;/asp:DropDownList&gt;
		&lt;asp:Button ID="Button1" runat="server" Text="View" onclick="Button1_Click" /&gt;
    &lt;/div&gt;
    &lt;div id="videoPlayer" runat="server"&gt;&lt;/div&gt;
    &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
<h3>Default.aspx.cs</h3>
<pre class="code"><code class="csharp">using System;
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
using System.IO;

public partial class _Default : System.Web.UI.Page {

	int videoWidth = 1000; // = 200/170 ratio
	int videoHeight = 680; // 400x340 = default

	string playerLocation = "osflv_player_v3/player.swf";

	protected void Page_Load(object sender, EventArgs e) {

		if (!IsPostBack) {
			DirectoryInfo directory = new DirectoryInfo(Server.MapPath("/videos"));

			FileInfo[] files = directory.GetFiles();

			foreach (FileInfo file in files) {
				if (file.Extension == ".flv") {
					DropDownList1.Items.Add(file.Name.Remove(file.Name.Length - 4));
				}
			}
		}

	}
	protected void Button1_Click(object sender, EventArgs e) {
		string video = "/videos/" + DropDownList1.SelectedItem.Text + ".flv";

		videoPlayer.InnerHtml = "&lt;object width='" + videoWidth.ToString() + "' height='" + videoHeight.ToString() + "' id='flvPlayer2'&gt;";
		videoPlayer.InnerHtml += "&lt;param name='allowFullScreen' value='true'&gt;";
		videoPlayer.InnerHtml += "&lt;param name='movie' value='" + playerLocation + "?movie=" + video + "&amp;fgcolor=0x0b7ba4&amp;bgcolor=0x333333&amp;autoload=on&amp;autorewind=on&amp;autoplay=on&amp;volume=5'&gt;";
		videoPlayer.InnerHtml += "";
		videoPlayer.InnerHtml += "&lt;embed src='" + playerLocation + "?movie=" + video + "&amp;fgcolor=0x0b7ba4&amp;bgcolor=0x333333&amp;autoload=on&amp;autorewind=on&amp;autoplay=on&amp;volume=5' width='" + videoWidth.ToString() + "' height='" + videoHeight.ToString() + "' allowFullScreen='true' type='application/x-shockwave-flash'&gt;";
		videoPlayer.InnerHtml += "&lt;/object&gt;";
		videoPlayer.InnerHtml += "&lt;br/&gt;&lt;span style='color:#ccc;'&gt;" + video + "&lt;/span&gt;";
	}
}</code></pre>
<p>A default Web.config file can be created and used, and a <strong>videos</strong> directory is checked for the listing of videos.</p>
<p>For ease, I recommend using <a href="http://strivinglife.com/words/post/Cassini-3502-built-and-ready-to-go.aspx">Cassini</a> to run the Web site on your own computer (creating a batch file similar to what is noted there).</p>
