+++
title = "Logical coding"
description = "When it comes to proper coding, you should know the most important rule of all; LIFO. However, not even LIFO nor the W3C can really tell you which order to put certain elements. In the nature of Web 2.0, I'll discuss some of the standards I've been bouncing around for HTML text markup when the same text is given multiple attributes."
draft = false
comments = true
date = "2006-05-28T08:49:00-05:00"
slug = "Logical-coding"
blogengine = "eb2709fa-2aa6-4bf5-8df6-1fa4c78dc39c"
categories = ["article", "general programming"]
tags = []
+++

<p>
When it comes to proper coding, you should know the most important rule of all; LIFO. However, not even LIFO nor the W3C can really tell you which order to put certain elements. In the nature of Web 2.0, I&#39;ll discuss some of the standards I&#39;ve been bouncing around for HTML text markup when the same text is given multiple attributes.
</p>
<!--more--><!--adsense-->
<p>
<strong>LIFO</strong>
</p>
<p>
LIFO - or last in, first out - states that that which is last stated is dismissed first. So, to take some empty ColdFusion code;
</p>
<blockquote>
	<p>
	&lt;cfif x = y&gt;<br />
	&nbsp;&nbsp;&lt;cfif y LTE z&gt;<br />
	&nbsp;&nbsp;&lt;/cfif&gt;<br />
	&nbsp;&nbsp;&lt;cfif y GT z&gt;<br />
	&nbsp;&nbsp;&lt;/cfif&gt;<br />
	&lt;/cfif&gt;
	</p>
</blockquote>
<p>
Here, we have opened an if-statement. We then opened another if-statement within our first, closed the second, opened a third, closed the third, and closed the first.
</p>
<p>
We also do LIFO in simple code. For example, to create text like <strong><em>this</em></strong>,
</p>
<blockquote>
	<p>
	&lt;strong&gt;&lt;em&gt;this&lt;/em&gt;&lt;/strong&gt;
	</p>
</blockquote>
<p>
To be proper, we must close the emphasis before we close the strong tag. If we did the following, we&#39;d be wrong. 
</p>
<blockquote>
	<p>
	&lt;strong&gt;&lt;em&gt;this&lt;/strong&gt;&lt;/em&gt;
	</p>
</blockquote>
<p>
<strong>Applying multiple attributes to the same block of stuff</strong>
</p>
<p>
In our previous example, where we place both emphasis and bold on the same group of text, we run into a bit of a question; which comes first? Do we place emphasis on the fact that the text is bold, or bold the emphasis on the text? I argue that we do the latter. 
</p>
<p>
Before we tackle this one, let&#39;s tackle an easier one; a bold link.
</p>
<p>
In such a case we would have an &lt;a&gt; and a &lt;strong&gt;. Does one preempt the other when they apply to the same thing?
</p>
<p>
<strong>If we have a paragraph that has bolded, with a <a href="#">link</a> within it, then the ordering is natural.</strong>
</p>
<p>
<a href="#">The question is, is there any case where a word would be <strong>bold</strong>, but the entire paragraph would be a link?</a>
</p>
<p>
Since we can apply a style on a link, namely font-weight:bold, it&#39;s possible that bold text within a link could not be seen. By doing so, we risk the chance that the link would be lost. Logically, we can also ask whether we are linking the bold text, or just the text. In some cases, we may want to bold a particular word. For example;
</p>
<blockquote>
	<p>
	<a href="#">Download the <strong>PDF</strong> version of the document.</a><br />
	<a href="#">Download the <strong>Word</strong> version of the document.</a>
	</p>
</blockquote>
<p>
Yet, that is not within the scope of what we&#39;ve asked.
</p>
<blockquote>
	<p>
	<strong><a href="#">Download the PDF.</a></strong>
	</p>
</blockquote>
<p>
In such a case, we are calling attention to the fact that there is a link where you can download the PDF. Therefore, when we code this, we do it as follows.
</p>
<blockquote>
	<p>
	&lt;p&gt;&lt;strong&gt;&lt;a href=&quot;#&quot;&gt;Download the PDF.&lt;/a&gt;&lt;/strong&gt;&lt;/p&gt;
	</p>
</blockquote>
<p>
We&#39;re not giving emphasis to some text within the link, we&#39;re giving emphasis to the fact that there is a link. So, if we were to look at &lt;a&gt; and &lt;em&gt;, we would thereby put the &lt;em&gt; surrounding the &lt;a&gt;. 
</p>
<p>
Going back to our emphasis / strong question, on which do we apply which? For both, we can use styles to remove the usage of &lt;strong&gt; and &lt;em&gt; altogether. However, if we do use both, in which order? As I stated above, I argue that we bold the emphasis.
</p>
<blockquote>
	<p>
	<strong>Deadline ends August 2006.</strong>
	</p>
	<p>
	<em>Deadline ends August 2006.</em>
	</p>
	<p>
	<strong><em>Deadline ends August 2006.</em></strong>
	</p>
</blockquote>
<p>
Really, though, it depends upon which of the first two we would do if we could only do one or the other. Do we give it emphasis, or do we bold it? In both cases, we&#39;re giving the text emphasis. As I see it, by using &lt;em&gt; we&#39;re using emphasis within the text, while using a &lt;strong&gt; gives a style emphasis. That is, in most paperbacks, &lt;em&gt; is used. It&#39;s rare to see bolded text. However, bold text is used for layout emphasis; to call attention to something outside of where one would look in the natural course of affairs (so to speak).
</p>
<p>
Given that view, we &lt;strong&gt; the &lt;em&gt;, or bold the emphasis. 
</p>
<blockquote>
	<p>
	&lt;strong&gt;&lt;em&gt;Deadline ends August 2006.&lt;/em&gt;&lt;/strong&gt;
	</p>
</blockquote>
<p>
Obviously, if we&#39;re only bolding a portion of the emphasis, or giving emphasis to a portion of bold text, then we would follow LIFO.
</p>
<p>
<strong>Conclusion</strong>
</p>
<p>
Given the above, I&#39;ve now argued that when it comes to &lt;strong&gt;, &lt;em&gt;, and &lt;a&gt; surrounding exactly the same text, the order of placement should be as follows;
</p>
<blockquote>
	<p>
	&lt;strong&gt; &lt;em&gt; &lt;a&gt;
	</p>
</blockquote>
<p>
Otherwise, LIFO always gets priority. 
</p>
<p>
Comments on this conclusion are indeed welcome.
</p>

