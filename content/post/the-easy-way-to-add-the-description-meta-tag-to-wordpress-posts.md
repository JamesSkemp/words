+++
title = "The 'easy' way to add the description meta tag to WordPress posts"
description = "An easy way to add descriptions to WordPress posts without the use of excessive plugins."
draft = false
comments = true
date = "2006-04-29T11:37:00-05:00"
slug = "The-easy-way-to-add-the-description-meta-tag-to-WordPress-posts"
blogengine = "37b1470d-6eda-4543-9073-7563080b3e89"
categories = ["software"]
tags = ["wordpress"]
+++

<p>
According to some people, the keywords meta tag has more relevancy/use than the description meta tag. Unfortunately, this is dead wrong. As I&#39;ve been able to prove (for myself, at least) this last month, the meta description is quite alive and well. Why people think it&#39;s not only dead, but surpassed by the meta keywords (!!!), I&#39;ll never understand.
</p>
<p>
 (And, by the way, these were August &#39;05, January &#39;06 articles/posts.)
</p>
<p>
 After looking for a good plug-in, I decided to work on something that was a) easier and b) easier. To that end, I present the following code. This code uses some hard-coded descriptions for the home page, archive/category pages, and the 404 page. For individual posts, it uses the post&#39;s &quot;Optional Excerpt&quot;.
</p>
<p>
 Note that the WordPress plugin Tags in the Head came the closest to what I was looking for, but was undesireable since it a) required installation of just one more plugin, and b) required another plugin to function. Also, it&#39;s focus is on keywords, which, again, I find to be near useless; they are merely more characters that must be read by bots, but which present no real gain.
</p>
<blockquote>
	&lt;?php<br />
	if (is_single()){<br />
	&nbsp;if (have_posts()) {<br />
	&nbsp;echo &quot;&lt;meta name=\&quot;description\&quot; content=\&quot;&quot;.htmlentities(get_the_excerpt()).&quot;\&quot; /&gt;&quot;;<br />
	&nbsp;}<br />
	} else if (is_home()) {<br />
	&nbsp;echo &quot;&lt;meta name=\&quot;description\&quot; content=\&quot;&quot;;<br />
	&nbsp;bloginfo(&#39;description&#39;);<br />
	&nbsp;echo &quot;\&quot; /&gt;&quot;;<br />
	} else if (is_archive()) {<br />
	&nbsp;echo &quot;&lt;meta name=\&quot;description\&quot; content=\&quot;Posts on StrivingLife.net for a specific category or time frame.\&quot; /&gt;&quot;;<br />
	} else if (is_404()) {<br />
	&nbsp;echo &quot;&lt;meta name=\&quot;description\&quot; content=\&quot;The content you have requested is not available at this address.\&quot; /&gt;&quot;;<br />
	} else {<br />
	&nbsp;echo &quot;&lt;meta name=\&quot;description\&quot; content=\&quot;&quot;.htmlentities(get_the_excerpt()).&quot;\&quot; /&gt;&quot;;<br />
	}<br />
	?&gt;
</blockquote>
<p>
This should be put into the header.php file for your current theme(s), after the line:
</p>
<blockquote>
	&lt;meta name=&quot;generator&quot; content=&quot;WordPress &lt;?php bloginfo(&#39;version&#39;); ?&gt;&quot; /&gt;
</blockquote>
<p>
Note that the home page description comes from the blog&#39;s description. Also note that an echo call does <em>not</em> proceed that line. Unfortunately, the bloginfo() function contains an echo statement. Durr. This description, as well as individual post descriptions, should be around 150 characters. 
</p>
<p>
Comments welcome and appreciated.
</p>

