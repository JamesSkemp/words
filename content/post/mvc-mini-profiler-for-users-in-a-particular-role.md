+++
title = "mvc-mini-profiler for users in a particular role"
description = "mvc-mini-profiler is pretty slick, and extremely easy to add."
draft = false
comments = true
date = "2011-06-24T23:30:00-05:00"
modified = "2011-06-24T23:43:52-05:00"
slug = "mvc-mini-profiler-for-users-in-a-particular-role"
blogengine = "a930c728-6c17-4f86-b8e2-4468a3c1988b"
categories = ["tutorials / guides"]
tags = ["asp.net mvc", "log parser plus"]
+++

<p>When Jeff Atwood announced the release of the&nbsp;<a rel="external" href="http://code.google.com/p/mvc-mini-profiler/">mvc-mini-profiler</a> for ASP.NET MVC Web sites I was intrigued. Just the other day he wrote an article <a rel="external" href="http://www.codinghorror.com/blog/2011/06/performance-is-a-feature.html">Performance is a Feature</a> and I decided I could hold off no longer.</p>
<p>Tonight (for better or worse) I finally got this up and running on <a rel="external" href="http://logparserplus.com/">one of my sites</a>, and fully intend on adding it to at least one more.</p>
<p>To install it I naturally used NuGet, but note that it's called MiniProfiler there.</p>
<p>Next, I had to add the necessary code to my _layout.cshtml, which also required that I move my jQuery include to the head element. Unfortunate, but ... that's how it is.</p>
<p>Finally, since I only wanted this to show for users in a particular role I added the below to the global.asax.cs:</p>
<pre class="code"><code class="csharp">protected void Application_BeginRequest()
{
	MiniProfiler.Start();
}

protected void Application_AuthorizeRequest(Object sender, EventArgs e)
{
	if (!User.IsInRole("Administrator"))
	{
		MvcMiniProfiler.MiniProfiler.Stop(discardResults: true);
	}
}

protected void Application_EndRequest()
{
	MiniProfiler.Stop();
}</code></pre>
<p>And with that done, I can see that my pages load extremely quick (after the first time of course).</p>
<p>I definitely need to do some research to see if I can display the total time for all users, albeit in a slightly different position (footer of the page), as that's something I wouldn't mind showing to users.</p>
