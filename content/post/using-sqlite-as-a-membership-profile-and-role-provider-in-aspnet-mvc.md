+++
title = "Using SQLite as a membership, profile, and role provider in ASP.NET MVC"
description = "How I was able to get SQLite working as a membership/profile/role provider in ASP.NET MVC."
draft = false
comments = true
date = "2009-10-25T08:20:00-05:00"
modified = "2009-10-25T08:25:03-05:00"
slug = "Using-SQLite-as-a-membership-profile-and-role-provider-in-ASPNET-MVC"
blogengine = "e4994a15-c5da-411a-a9c8-d00a93374d2f"
categories = ["tutorials / guides"]
tags = ["asp.net", "asp.net mvc", "sqlite", "windows server 2003"]
+++

<p>I'd really like to implement membership providers in my Web applications, but just don't have the user-base that requires SQL Server (Express), nor the memory on my production server.</p>
<p>Having looked at SQLite before, I figured it would be exactly what I'd need, without going to the alternative of XML.</p>
<p>After some research I found Roger Martin's <a rel="external" href="http://www.codeproject.com/KB/aspnet/SQLite-Providers.aspx">SQLite Membership, Role, and Profile Providers</a>, and finally decided yesterday to implement these on a dummy MVC site.</p>
<p>However, when attempting to add this to my MVC site I kept running into issues, the last of which was an "Unable to open the database file."</p>
<p>The first issue was with the type declared in the examples on the page above; <strong>TechInfoSystems.Data.SQLiteProvider</strong> should be removed completely, as he suggests just&nbsp;adding the three classes to your site.</p>
<p>The second and last issue was that pesky database issue. At first I didn't think the app_data directory was getting pushed over, so I verified that I was pushing that as part of the Publish process (how they recommend you push a MVC site to production).</p>
<p>Upon further review it looks like the App_Data directory was placed inside the Bin directory. Google didn't help me much on whether that was the expected behavior, but it consistently did that. I added a ton of permissions to NETWORK SERVICE on the bin\app_data directory, but still the same pesky error.</p>
<p>So I commented out the membership, profile, and role items completely from web.config and added the following code to the Index view.</p>
<pre class="code"><code class="csharp">&lt;%= AppDomain.CurrentDomain.GetData("DataDirectory").ToString() %&gt;</code></pre>
<p>Lo and behold, it was looking for it in the root of the site, exactly where I was expecting the App_Data directory to publish to.</p>
<p>Move the App_Data folder and sure enough, the site works (after uncommenting the Web.config provider information, of course) and I'm able to create a new user.</p>
<p>So, why does the publish process require me to move the App_Data directory?</p>
<h3>The fix</h3>
<p>In order to get the database pushing correctly I changed Copy to Output from Do not copy to Copy always. However, what really needed to happen was the Build Action needed to be changed to Content.</p>
<p>An App_Data directory is now created correctly, and the SQLite database is correctly placed in the directory.</p>
<h3>Another gotcha</h3>
<p>If you want troubles, change the applicationName in the Web.config for all three items. If you do this, you'll run into errors like "Attempt to write a read-only database attempt to write a readonly database" with a line reference suggesting there's an issue with roleManager. Comment that out, or that and membership and&nbsp;profile, and things will seem okay.</p>
<p>The issue is that the applicationName (SQLite ASP.NET Provider) is baked into the sample SQLite database. Durr.</p>
