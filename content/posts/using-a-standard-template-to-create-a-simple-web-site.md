+++
title = "Using a standard template to create a simple Web site"
summary = "As stated in a previous article, there's a site, http://blog.html.it/layoutgala/, that offers free templates.  Using these templates, you can easily create a site, so long as you have the content you need to fill the pages.

 In this article, we'll be putting some content into one of these templates, Layout 34, but we can use the methods we discuss here on any of the templates."
draft = false
comments = true
date = "2006-04-02T19:33:00-05:00"
slug = "Using-a-standard-template-to-create-a-simple-Web-site"
blogengine = "0e2d53d6-21e0-4127-a19c-a8704db4deb4"
categories = ["tutorials / guides"]
tags = ["html"]
+++

<p>
As stated in a previous article, there&#39;s a site, <a href="http://blog.html.it/layoutgala/">http://blog.html.it/layoutgala/</a>, that offers free templates.  Using these templates, you can easily create a site, so long as you have the content you need to fill the pages.
</p>
<p>
In this article, we&#39;ll be putting some content into one of these templates, Layout 34, but we can use the methods we discuss here on any of the templates.
</p>
<!--more-->
<p>
First, you&#39;ll need <a href="http://strivinglife.net/wordpress/2006/03/25/74/web-site-development-content-and-audience/">content</a>.  If you don&#39;t have content, then you&#39;ve got a bit of a problem :)
</p>
<!--adsense-->
<p>
Second, you&#39;ll want to have an idea of what sections you&#39;ll need.  If you&#39;ve followed the above guide, then you probably have a really good indication of what sections you&#39;ll have.  To these sections, you&#39;ll need to add a home page, a contact page, and possibly a site map, or search feature.
</p>
<p>
The home page should have links to all of your main areas, should discuss what the purpose of your site is, and etcetera.  On the one hand, you&#39;ll want to make it both informational enough for people who have visited your site, but not a one-time read, since people may use it to get to your site in the future.  A short number of &#39;news&#39; items, for example, is definitely a plus.
</p>
<p>
Your contact page should contain whatever information you&#39;d like to provide regarding how people can contact you, as well as information about who you are (to a lesser extent - a bio / about us page can be another page all-together).
</p>
<p>
The site map, or search page, should contain a way for people to find any content on your site.  At the lowest level, the page should list the major areas and subareas of your site.  Working towards more complexity, the site map can contain every page on your site, and finally the ability to search your content.  For search, Google offers a free site search.
</p>
<p>
Getting back to Layout 34, make sure you&#39;ve got a copy on your computer.  You can save the html file to your desktop (Layout34.html is what I&#39;ll be using for a name), and open it using your favourite browser.  Since the page is using very simple HTML, anyone can open the file up using only a browser.
</p>
<p>
Of course, if you&#39;ve setup Apache or the like on your computer, than you can certainly put this HTML file in your Web folder - and, with more advanced techniques, you would have to.
</p>
<p>
Now that you&#39;ve saved the file and opened it up using your browser, you can see what the template looks like with the basic text they&#39;ve provided.  We&#39;re going to clean that up by adding our own items.
</p>
<p>
First, open Notepad.  Now, use Notepad to open up Layout34.html.  If Word Wrap is on (under Format), turn it off.
</p>
<p>
You can now see the source of this page, which consists solely of HTML.  If you&#39;re familiar with HTML, or you&#39;ve read through <a href="http://strivinglife.net/wordpress/2006/03/27/75/just-enough-html-to-be-dangerous/"><cite>&quot;Just enough HTML to be dangerous&quot;</cite></a>, then at least some of this code is going to make sense.  You see some &lt;p&gt; tags looking a number of lines down.
</p>
<p>
There&#39;s also a number of &lt;div&gt; tags, which are basically blocked containers for content.  These have id attributes, which are basically unique identifiers.  The id values are picked so as to provide the most information possible about what these &#39;containers&#39; hold.
</p>
<p>
Starting off, the only thing we&#39;re going to worry about is the content within a couple of divs (&lt;div&gt;s).
</p>
<p>
First, we&#39;re going to find the footer div (&lt;div id=&quot;footer&quot;&gt; ... &lt;/div&gt;).
</p>
<p>
We&#39;re now going to replace the text within this with a short bit of contact information.
</p>
&lt;p&gt;Copyright 2006, &lt;a href=&quot;mailto:our_email@domain.ext&quot;&gt;Our Name&lt;/a&gt;.&lt;/p&gt;
<p>
Save the file, and reload the file in your browser.  You&#39;ll notice that your text is now in the footer.
</p>
<p>
Now, we&#39;re going to remove the content from the &#39;extra&#39; div (&lt;div id=&quot;extra&quot;&gt; ... &lt;/div&gt;).  Just remove everything between the two divs (including the paragraph, &lt;p&gt;, tags).  Save, and again refresh your browser.  If you&#39;re using Internet Explorer you&#39;ll still see the block.  We&#39;ll get rid of the block (since we don&#39;t want to use it, quite yet), by commenting it out.
</p>
<p>
To do this, you&#39;ll need to add &lt;!-- before the div, and --&gt; after the div.
</p>
<blockquote>
	&lt;!--&lt;div id=&quot;extra&quot;&gt;&lt;/div&gt;--&gt;
</blockquote>
<p>
You can use this technique for other things as well.  Anything you comment out will not be rendered (typically), but will display in the source (which you can see by right clicking within your browser and selecting the appropriate menu item).
</p>
<p>
Now, we&#39;ll create our base navigation items, by finding the &#39;navigation&#39; div.  Remove everything within it and fill in your navigation structure.  For example, if you wanted a navigation with the following items - About me, Contact me, My cat, My favourite books - you could do something like this;
</p>
<blockquote>
	&lt;div id=&quot;navigation&quot;&gt;<br />
	&lt;p&gt;About me&lt;/p&gt;<br />
	&lt;p&gt;Contact me&lt;/p&gt;<br />
	&lt;p&gt;My cat&lt;/p&gt;<br />
	&lt;p&gt;My favourite books&lt;/p&gt;<br />
	&lt;/div&gt;
</blockquote>
<p>
Again, save and refresh.
</p>
<p>
Now, we&#39;re going to change the header, by changing the content inside &lt;h1&gt; ... &lt;/h1&gt; (Heading 1). Put whatever (&#39;My site&#39; for example). This should be unique to each page, unless you&#39;ll be placing your logo in this place.
</p>
<p>
Save and refresh.
</p>
<p>
Finally, clear out &#39;content&#39; div, and fill in some new information. For this page, you could fill out whatever you wanted to display on your main page.
</p>
<p>
Now, find the title tag (&lt;title&gt; ... &lt;/title&gt;) and put a unique title in this area. It should probably match your main heading. You cannot use any HTML within these tags - just plain text.
</p>
<p>
With that, you&#39;ve successfully created your first page. All you need to do now is create additional pages (the other items in your navigation) by making a copy of this page, and changing the heading and title. You&#39;ll also need to add links to the navigation (see <a href="http://strivinglife.net/wordpress/2006/03/27/75/just-enough-html-to-be-dangerous/"><cite>&quot;Just enough HTML to be dangerous&quot;</cite></a>) so that all of your pages link up correctly.
</p>

