+++
title = "StrivingLife.net network popularity"
description = ""
draft = false
comments = true
date = "2005-10-07T20:41:00-05:00"
slug = "StrivingLifenet-network-popularity"
blogengine = "c9f2fc6e-88ea-4944-9492-4a40317cf99b"
categories = ["software", "Internet", "tutorials / guides"]
tags = ["analytics"]
+++

<p>
As I said this morning, site popularity can be determined by how many people are viewing the content, and how many people are using the content.<!--more--><!--adsense-->
</p>
<p>
With e-commerce sites, this is fairly easy to determine.  Tracking programs can be used to count the number of unique visitors to the site, as well as how many products are bought and sold.  The best e-commerce site will have a 1:1 ratio - every unique visitor will make a purchase.
</p>
<p>
Tracking a site that offers a free download is very similar.  However, we also have to throw in the possibility of support forums.  While support provides a service, it&#39;s more difficult to determine whether the visitors needs have been met.  If you view some sites, like HP, you&#39;ll notice that they actually ask you if they can send you an email to see how your visit went.  Assuming the visitor actually responds to the email and completes the entire survey, the visit to the site can be adequately tracked.  If everyone that visits the site gets an email, and everyone responds to it by saying that they are satisifed, then the 1:1 ratio has been met.
</p>
<p>
Now let&#39;s take away the download aspect and just look at a site that provides information.  How do you track popularity on such a site?  Let&#39;s take StrivingLife.net&#39;s stats to come up with some possible ways.
</p>
<p>
First, you could simply go by the numbers.  Most stats track <strong>Unique visitors</strong>, <strong>Number of visits</strong>, <strong>Pages</strong>, <strong>Hits</strong>, and sometimes even <strong>Bandwidth</strong>.  They may use different names, but what it boils down to is unique people visiting the site, the total number of visits to the site, the number of pages viewed, and the number of items viewed.  Bandwidth is basically how much of the files were used.  Unless you&#39;ve got a number of downloads, or you need to track this, it&#39;s not worth looking at too carefully, so we won&#39;t any further.
</p>
<blockquote>
	Note that there are a number of different explanations for what the various terms mean.  Here, since I&#39;m using AWStats, I&#39;ll be using their terminology.  See <a href="http://awstats.sourceforge.net/docs/awstats_glossary.html" title="AWStats Glossary">http://awstats.sourceforge.net/docs/awstats_glossary.html</a> for what this information.
</blockquote>
<p>
Going back, we can couple the four remaining items.  <strong>Unique visitors</strong> goes with <strong>Number of visits</strong>, while <strong>Pages</strong> goes with <strong>Hits</strong>.  For each couple, the first will be less than the second.  After all, a person can visit the site many times, but will be &#39;unique&#39; only the first visit.  Equally, a single page will consist of many hits.  For example, if you load a simple HTML page with two images, that counts as 3 hits - 1 page and 2 images.
</p>
<p>
For each of these, there are a number of caveats.  At which point is a person no longer unique?  Daily?  Monthly?  Hourly?  Equally, how long after the first visit do we consider a second visit?  30 minutes?  An hour?  A day?  Obviously, the answer to the second question depends upon the answer to the first.  Also, what is included in hits can differ by quite a lot.  Due to caching, or storing, of files, the hits could be much smaller than the actual value.
</p>
<p>
But, let&#39;s look at the last three months (July to September 2005) according to StrivingLife.net&#39;s stats, provided by AWStats 6.4:
</p>
<ol style="list-style-type: none">
	<li>July 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 4781</li>
		<li><strong>Number of visits</strong>: 5610</li>
		<li><strong>Pages</strong>: 12987</li>
		<li><strong>Hits</strong>: 39208</li>
	</ul>
	</li>
	<li>August 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 3834</li>
		<li><strong>Number of visits</strong>: 4703</li>
		<li><strong>Pages</strong>: 11104</li>
		<li><strong>Hits</strong>: 38536</li>
	</ul>
	</li>
	<li>September 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 3615</li>
		<li><strong>Number of visits</strong>: 4908</li>
		<li><strong>Pages</strong>: 10750</li>
		<li><strong>Hits</strong>: 31994</li>
	</ul>
	</li>
</ol>
<p>
Now, what can this tell us?  First, that unique visitors are going down, while number of visits went down and is now going back up.  Pages are going down, and so are hits.
</p>
<p>
But wait, what about search engines?  Are the bots that move across the Web, searching for new and updated content included in these numbers?  If they are, we might be adding artificial visitors and hits to our counts.  Fortunately, AWStats strips these out.  However, not all stat programs will do this, so make sure you check whether the stats include robots or not.
</p>
<p>
Getting back, without having more information, we can&#39;t really be sure what this data means.  Why are less people viewing the site, but visiting more?  Why did pages decrease slightly, but hits jump down so much?
</p>
<p>
But, why assume that July 2005 is normal?  What if June 2005 had a unique number in the 3000s?  Then we&#39;re looking at an abnormally high value for July.<!--adsense-->
</p>
<p>
So, let&#39;s look at just the unique visitors for the last six months.
</p>
<ol style="list-style-type: none">
	<li>April 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 3528</li>
	</ul>
	</li>
	<li>May 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 3967</li>
	</ul>
	</li>
	<li>June 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 4940</li>
	</ul>
	</li>
	<li>July 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 4781</li>
	</ul>
	</li>
	<li>August 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 3834</li>
	</ul>
	</li>
	<li>September 2005
	<ul style="list-style-type: none">
		<li><strong>Unique visitors</strong>: 3615</li>
	</ul>
	</li>
</ol>
<p>
Perhaps visitors are, in fact, getting back to normal?  Since I can look at all four numbers for those six months, I can tell you that numbers were in fact overally high across the board for those two months.  Perhaps the audience is busier and no longer able to check the site as much as they were before?
</p>
<p>
There&#39;s a number of other things we could check to determine why these numbers are so high for June and July.  But to do so would be to move off the topic at hand - popularity.  We&#39;ve got the numbers that we&#39;re looking for, but it&#39;s important to point out at the same time that popularity has to be looked at from a longer aspect.  For example, an average of three, six, and twelve month periods, would give a pretty good sample what traffic is really like.  This will allow major spikes to avoid overally complicating things.
</p>
<p>
Now, we&#39;ve got our second item - remember our second item?  The usefulness of the content being provided - is the content on the StrivingLife.net network useful?  Since I don&#39;t provide just a couple downloads, and I don&#39;t sell items, how do we determine the usefulness of the site?
</p>
<p>
Since we&#39;re dealing with information, we can ask a couple of questions.  First, how long are people on the site?  One might think that the longer people are on a site the better.  Second, how are people coming to the site?  If people are coming directly to the site, it&#39;s more likely that they&#39;ve bookmarked or memorized your site.  On another (not the other) hand, if people are following links to your site, maybe people are posting your site as a resource.  Finally, what are people viewing when they visit the site?  What pages are drawing the views, and what file types (images or text)?
</p>
<p>
We&#39;ll look at the time issue first.  AWStats is nice enough to have this information displayed.  Some other programs will, some won&#39;t.  AWStats breaks it up into seven different time periods, displayed below for the last three months.  Keep in mind that the total number and percentage is taken from the number of visits for that month.
</p>
<ol style="list-style-type: none">
	<li>July 2005
	<ul style="list-style-type: none">
		<li><strong>0s-30s</strong>: 4488, 80%</li>
		<li><strong>30s-2mn</strong>: 488, 8.6%</li>
		<li><strong>2mn-5mn</strong>: 258, 4.5%</li>
		<li><strong>5mn-15mn</strong>: 213, 3.7%</li>
		<li><strong>15mn-30mn</strong>: 84, 1.4%</li>
		<li><strong>30mn-1h</strong>: 63, 1.1%</li>
		<li><strong>1h+</strong>: 16, 0.2%</li>
	</ul>
	</li>
	<li>August 2005
	<ul style="list-style-type: none">
		<li><strong>0s-30s</strong>: 3693, 78.5%</li>
		<li><strong>30s-2mn</strong>: 465, 9.8%</li>
		<li><strong>2mn-5mn</strong>: 188, 3.9%</li>
		<li><strong>5mn-15mn</strong>: 178, 3.7%</li>
		<li><strong>15mn-30mn</strong>: 78, 1.6%</li>
		<li><strong>30mn-1h</strong>: 75, 1.5%</li>
		<li><strong>1h+</strong>: 26, 0.5%</li>
	</ul>
	</li>
	<li>September 2005
	<ul style="list-style-type: none">
		<li><strong>0s-30s</strong>: 3807, 77.5%</li>
		<li><strong>30s-2mn</strong>: 424, 8.6%</li>
		<li><strong>2mn-5mn</strong>: 200, 4%</li>
		<li><strong>5mn-15mn</strong>: 178, 3.6%</li>
		<li><strong>15mn-30mn</strong>: 74, 1.5%</li>
		<li><strong>30mn-1h</strong>: 130, 2.6%</li>
		<li><strong>1h+</strong>: 95, 1.9%</li>
	</ul>
	</li>
</ol>
<p>
Now the interesting thing about time is that it&#39;s hard to really get good information for this.  For example, someone could visit a page, spend two hours reading the content, and then close the browser.  This would count under 0s-30s, unless something was automatically reloaded on the page (for example, a small portion of the page could refresh every minute - this might give a little better information) or they moved around the site.  AWStats ends a session after an hour of inactivity, so, if after an their two-hours of reading they visited another page on the site, it then count as another session altogether.  Another two-hours of reading?  Another visit under 0s-30s.
</p>
<p>
However, we can still use time statistics, if we multiple pages of content, and especially if single pieces of content span multiple pages.  Perhaps this is why we have to click a &#39;next&#39; link on a number of news sites.  Perhaps also we should take this suggestion.
</p>
<p>
Now, let&#39;s look at the second item of how people are coming to the site.  There are two major ways people can get to sites.  First, people can click on a link.  This is one of the most common ways.  Second, people can type in your site&#39;s URL, or domain, and view your content.  This is typically uncommon.  In fact, interestingly, people will sometimes even type a domain name into a search engine instead of typing it into the address bar.  Yes, I am guilty of doing that too.
</p>
<p>
But wait, what about bookmarks?  Here, I&#39;ll be including them with links.  The reason I&#39;ll be doing this is because I&#39;m going to break-up the two major ways into a couple smaller groups.  Namely, bookmarks, internal links, search engines, and non-search external links.
</p>
<p>
<strong>Bookmarks</strong>.  First, the obvious - if people are visiting you from bookmarks, you&#39;ve successfully gotten onto the visitor&#39;s computer.  Second, just because you&#39;ve landed in their bookmarks doesn&#39;t mean that they&#39;ll ever visit you again.  Why?  Ask yourself how many bookmarks you have, and how many you visit on a regular basis.
</p>
<p>
<strong>Internal links</strong> are links from within your site.  So, these won&#39;t help all that much.  However, it&#39;s important to point out that this is the only real way to determine how many people are viewing more than one page on your site.  After all, a single unique visitor could view the same page in multiple visits.
</p>
<p>
Typically, these two are grouped together, and that&#39;s also the case with AWStats.
</p>
<p>
<strong>Search engines</strong> and other external sites are the final two sources of visitors.  The first is pretty open to who it will send your way.  As long as you have the content that the potential visitor is looking for, the search engine will link to your page - if you mention Charlize Theron enough times chances are someone will come to your site looking for a picture of her.
</p>
<p>
<strong>External sites</strong>, on the other hand, are typically a little more picky.  Typically, again - typically, external sites will only link to your site if they (the site owner) finds something worthwhile or interesting on your site.  Sometimes sites try and act like a search engine, or a portal, in which case they&#39;ll just grab what they can find.  However, that&#39;s why it&#39;s always important to follow links to determine what the site is talking about, and why they are linking to your site :)
</p>
<p>
Looking at these four ways, the more visitors coming to your site from non-search engine external sites, typically the better.  In turn, more people will come to your site via search, which may in turn mean more people will link to you, and etcetara.  However, getting on search is the primary goal (unless you can get your link on a popular site, in which case everything else will usually follow).
</p>
<p>
That said, we&#39;re at the third way to check possible information popularity - what are people viewing?  What resources are being used?  Many times, one particular resource will stand above all the rest.  This, along with a high number of one-time visits, could mean that your site has one thing to offer, which may or may not be beneficial.  Your site may be popular, but perhaps for all the wrong reasons.
</p>
<p>
So, let&#39;s look at the top ten resources from the StrivingLife.net network for September of 2005.
</p>
<p>
From left-to-right, we have the <strong>path to the file</strong>, the number of <strong>views</strong>, how many people viewed this as their <strong>first file</strong>, followed by how many viewed this <strong>file last</strong>.
</p>
<ol>
	<li>/articles/rss/wakinglife.rss - 1049 - 637 - 652</li>
	<li>/index.shtml - 564 - 23 - 317</li>
	<li>/articles/wakinglifescript.shtml - 529 - 405 - 121</li>
	<li>/articles/pdf/wakinglifescript.pdf - 496 - 135 - 357</li>
	<li>/ - 334 - 256 - 162</li>
	<li>/jamesrskemp/html/jmsnavigationtoc.htm - 330 - 298 - 42</li>
	<li>/articles/index.shtml - 199 - 72 - 76</li>
	<li>/discussions/viewtopic.php - 198 - 9 - 16</li>
	<li>/articles/crosssumsnumbers.shtml - 196 - 138 - 55</li>
	<li>/jamesrskemp/html/jms2/jms2beautifulwomenaccordingtojamesskemp.h...	169 - 158 - 155</li>
</ol>
<p>
First, we notice that one file has significantly more views than the other files.  However, notice that there is not a 1 view : 1 entry : 1 exit ratio for this file.  What this suggests, and what two other resources on this list also support, is that while people are using one resource more than any other, they are not viewing the single resource and leaving.  Rather, they are using it to move onto other items.
</p>
<p>
Knowing something about the content, I know that the RSS feed in the first slot links to the HTML file in the 3rd slot, which in turn links to the PDF in the fourth slot.  While not everyone is moving from RSS to HTML to PDF, there looks to be a few that are.
</p>
<p>
The question now becomes, is this the trait that I expect?  Or, is there another section that I would rather see in the top five, or top ten, that isn&#39;t there?  Since my site focuses on articles, and since this is an article, that&#39;s one thing suggesting that my site is a source of information.  Next, the seventh slot is filled by my articles&#39; main page - I&#39;m pretty happy that that page is showing up in the top ten.  Finally, there&#39;s another article in the top ten, which means I&#39;m not a one-hit wonder site.
</p>
<br />
<p>
So now we&#39;ve gotten to the point we set out to get to in the very beginning.  The question is, have we determined whether the network is popular.  Looking at previous numbers, I see growth, which I consider to be a good thing.  Looking at what is getting used, I&#39;m also happy, as I believe the information I provide is being used.  Is the StrivingLife.net network popular?  Some things could certainly be more popular (looking at a complete list of URLs that were accessed shows me under-used content), but a number of my articles <strong>are</strong> popular.  Without looking at other sites that provide the same information, and getting a look at their stats, I suppose I just can&#39;t know for sure.
</p>
<p>
And therein lies the message: make a site for you, and strive for what you deem to be popular.  One million unique visitors a month?  A day?  Maybe one day, but growth is definitely a good thing, and you&#39;ve got to start somewhere.
</p>

