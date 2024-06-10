+++
title = "Basic .NET (C#) Traceroute library"
description = "A slightly enhanced version of Jim Scott's C# Traceroute."
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
<p>The code for the assembly and console application are included below. Written against <a rel="external" href="https://smallestdotnet.com/">.NET Framework</a> 4 (in Visual Studio 2010), but if you change the String.IsNullOrWhiteSpace() reference, you should be able to compile this in 3.5.</p>
<h3>Trace.cs</h3>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;
using System.Net.NetworkInformation;
using System.Diagnostics;

namespace JamesRSkemp.Traceroute {
	public class TraceLocation {
		/// <summary>
		/// Hop number in a particular trace.
		/// </summary>
		public int Hop { get; set; }
		/// <summary>
		/// Time in milliseconds.
		/// </summary>
		public long Time { get; set; }
		/// <summary>
		/// IP address returned.
		/// </summary>
		public String IpAddress { get; set; }
	}

	public class Trace {
		/// <summary>
		/// Given an ip address or domain name, follow the trace path.
		///
		/// Idea and majority of the code from Jim Scott - http://coding.infoconex.com/post/C-Traceroute-using-net-framework.aspx
		/// </summary>
		/// <param name="ipAddressOrHostName">IP address or domain name to trace.</param>
		/// <param name="maximumHops">Maximum number of hops before quitting.</param>
		/// <returns>List of TraceLocation.</returns>
		public static List<TraceLocation> Traceroute(string ipAddressOrHostName, int maximumHops) {
			if (maximumHops < 1 || maximumHops > 100) {
				maximumHops = 30;
			}

			IPAddress ipAddress = Dns.GetHostEntry(ipAddressOrHostName).AddressList[0];

			List<TraceLocation> traceLocations = new List<TraceLocation>();

			using (Ping pingSender = new Ping()) {
				PingOptions pingOptions = new PingOptions();
				Stopwatch stopWatch = new Stopwatch();
				byte[] bytes = new byte[32];
				pingOptions.DontFragment = true;
				pingOptions.Ttl = 1;

				for (int i = 1; i < maximumHops + 1; i++) {
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
}
```

<h3>Program.cs</h3>

```csharp
using System;
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
}
```

<h3>Next steps</h3>
<p>It would probably make sense to allow the application to accept domain names/IPs on the fly, and what an IP resolves to could be cached.</p>
<p>Comments and etcetera welcome.</p>
