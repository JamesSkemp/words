+++
title = "Basic .NET (C#) Traceroute library"
summary = "A slightly enhanced version of Jim Scott's C# Traceroute."
draft = false
comments = true
date = "2010-05-09T16:35:00-05:00"
modified = "2010-05-09T16:41:39-05:00"
slug = "Basic-NET-C-Sharp-Traceroute-library"
blogengine = "a081b412-d972-4a86-b74f-c53f1b8f6e1b"
categories = ["tutorials / guides"]
tags = [".net", "c#"]
+++

<p>Spending the day researching all things DNS, I eventually came upon Jim Scott's post on <a rel="external" href="http://coding.infoconex.com/post/C-Traceroute-using-net-framework.aspx">C# Traceroute using .net framework</a>. After a bit of tweaking, I've got something that I like a bit more, because I really want to know what the IP address means.</p>
<p>The code for the assembly and console application are included below. Written against <a rel="external" href="http://smallestdotnet.com/">.NET Framework</a> 4 (in Visual Studio 2010), but if you change the String.IsNullOrWhiteSpace() reference, you should be able to compile this in 3.5.</p>
<h3>Trace.cs</h3>
<pre class="code"><code class="csharp">using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;
using System.Net.NetworkInformation;
using System.Diagnostics;

namespace JamesRSkemp.Traceroute {
	public class TraceLocation {
		/// &lt;summary&gt;
		/// Hop number in a particular trace.
		/// &lt;/summary&gt;
		public int Hop { get; set; }
		/// &lt;summary&gt;
		/// Time in milliseconds.
		/// &lt;/summary&gt;
		public long Time { get; set; }
		/// &lt;summary&gt;
		/// IP address returned.
		/// &lt;/summary&gt;
		public String IpAddress { get; set; }
	}

	public class Trace {
		/// &lt;summary&gt;
		/// Given an ip address or domain name, follow the trace path.
		/// 
		/// Idea and majority of the code from Jim Scott - http://coding.infoconex.com/post/C-Traceroute-using-net-framework.aspx
		/// &lt;/summary&gt;
		/// &lt;param name="ipAddressOrHostName"&gt;IP address or domain name to trace.&lt;/param&gt;
		/// &lt;param name="maximumHops"&gt;Maximum number of hops before quitting.&lt;/param&gt;
		/// &lt;returns&gt;List of TraceLocation.&lt;/returns&gt;
		public static List&lt;TraceLocation&gt; Traceroute(string ipAddressOrHostName, int maximumHops) {
			if (maximumHops &lt; 1 || maximumHops &gt; 100) {
				maximumHops = 30;
			}

			IPAddress ipAddress = Dns.GetHostEntry(ipAddressOrHostName).AddressList[0];

			List&lt;TraceLocation&gt; traceLocations = new List&lt;TraceLocation&gt;();

			using (Ping pingSender = new Ping()) {
				PingOptions pingOptions = new PingOptions();
				Stopwatch stopWatch = new Stopwatch();
				byte[] bytes = new byte[32];
				pingOptions.DontFragment = true;
				pingOptions.Ttl = 1;

				for (int i = 1; i &lt; maximumHops + 1; i++) {
					TraceLocation traceLocation = new TraceLocation();

					stopWatch.Reset();
					stopWatch.Start();
					PingReply pingReply = pingSender.Send(
						ipAddress,
						5000,
						new byte[32], pingOptions);
					stopWatch.Stop();

					traceLocation.Hop = i;
					traceLocation.Time = stopWatch.ElapsedMilliseconds;
					if (pingReply.Address != null) {
						traceLocation.IpAddress = pingReply.Address.ToString();
					}

					traceLocations.Add(traceLocation);
					traceLocation = null;

					if (pingReply.Status == IPStatus.Success) {
						break;
					}
					pingOptions.Ttl++;
				}
			}
			return traceLocations;
		}
	}
}</code></pre>
<h3>Program.cs</h3>
<pre class="code"><code class="csharp">using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;
using System.Net.NetworkInformation;
using System.Diagnostics;

namespace DnsConsoleApp {
	class Program {
		static void Main(string[] args) {
			List domainNames = new List();
			domainNames.Add("strivinglife.com");

			foreach (String domainName in domainNames) {
				Console.WriteLine("***" + domainName + "***");

				foreach (JamesRSkemp.Traceroute.TraceLocation traceLocation in JamesRSkemp.Traceroute.Trace.Traceroute(domainName)) {
					Console.Write(traceLocation.Hop + "	");
					Console.Write(traceLocation.Time + "ms	");
					Console.Write(traceLocation.IpAddress + "	");
					if (!String.IsNullOrWhiteSpace(traceLocation.IpAddress) &amp;&amp; !traceLocation.IpAddress.StartsWith("10.") &amp;&amp; !traceLocation.IpAddress.StartsWith("192.")) {
						try {
							Console.WriteLine(Dns.GetHostEntry(traceLocation.IpAddress).HostName.ToString());
						} catch (Exception ex) {
							Console.WriteLine(ex.Message);
						}
					} else {
						Console.WriteLine();
					}
				}
				Console.ReadKey();
			}
		}
	}
}</code></pre>
<h3>Next steps</h3>
<p>It would probably make sense to allow the application to accept domain names/IPs on the fly, and what an IP resolves to could be cached.</p>
<p>Comments and etcetera welcome.</p>
