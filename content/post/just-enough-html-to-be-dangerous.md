+++
title = "'Just enough HTML to be dangerous'"
summary = "This time, we'll be covering the minimum HTML knowledge required to be truly dangerous.  While an expanded understanding of HTML is not, per se, required, having at least some understanding will help in a number of ways.  Of course, the more HTML you know, the less you rely on tools to do the work (which is a good thing, since we're not always able to use the tools that we're familiar with)."
draft = false
comments = true
date = "2006-03-27T20:26:00-06:00"
slug = "Just-enough-HTML-to-be-dangerous"
blogengine = "ad83a47c-3da0-42ee-8ea5-8ace0f492c76"
categories = ["tutorials / guides"]
tags = ["html"]
+++

<p>
This time, we&#39;ll be covering the minimum HTML knowledge required to be truly dangerous. While an expanded understanding of HTML is not, per se, required, having at least some understanding will help in a number of ways. Of course, the more HTML you know, the less you rely on tools to do the work (which is a good thing, since we&#39;re not always able to use the tools that we&#39;re familar with).<!--more--><!--adsense-->
</p>
<p>
The first thing we&#39;ll be discussing is how to apply formatting to text. <strong>Bold</strong>, <em>italics</em> or <em>emphasis</em>, and <u>underline</u>.
</p>
<p>
To make text <strong>bold</strong>, we&#39;ll use the &lt;strong&gt;&lt;/strong&gt; tags. If we want some text to be bold, we simply need to put it within these tags. For example, &lt;strong&gt;bold text &lt;/strong&gt;, would display as <strong>bold text</strong>.
</p>
<p>
In HTML, and most Web-based programming languages, many items, in this case text, are defined by elements which contain either opened or closed tags. A closed tag is one that has a / within it. So, in the previous example we write an opening strong tag, some text, and then a closing strong tag. As we&#39;ll see later, some elements only consist of one closed tag.
</p>
<p>
For <em>italics</em>, we&#39;ll use the &lt;em&gt;&lt;/em&gt; tags. So, &lt;em&gt;italic text&lt;/em&gt; displays as <em>italic text</em>.
</p>
<p>
For an <span style="text-decoration: underline">underline</span>, we use &lt;u&gt;&lt;/u&gt; tags. &lt;u&gt;underlined text&lt;/u&gt; displays as <span style="text-decoration: underline">underlined text</span>. However, there&#39;s a very important point about underlined text. For the most part, you should stay away from using this element / these tags. Most of the newer Web standards do not allow the use of these tags, typically because underlined text should be used only for hyperlinks (or the appropriate citations). However, we won&#39;t go into the discussion of the correct way to show underlined text, at this point.
</p>
<p>
What if we want some text to be both <em><strong>bold and italic</strong></em>? We would simply place the text within both elements; &lt;strong&gt;&lt;em&gt;bold and italic&lt;/em&gt;&lt;/strong&gt;. Note that you should close inner elements before you close outer ones. So, &lt;strong&gt;&lt;em&gt;bold and italic&lt;/strong&gt;&lt;/em&gt; would not be correct. So, if you wanted to display the text as <em>bold <strong>and</strong> italic</em>, you would do: &lt;em&gt;bold &lt;strong&gt;and&lt;/strong&gt; italic&lt;/em&gt;. 
</p>
<p>
The next thing to cover is paragraphs. To define a block of text as a paragraph, you simply need to place it within &lt;p&gt;&lt;/p&gt;. So, &lt;p&gt;This is one paragraph.&lt;/p&gt; would display as:
</p>
<p>
This is one paragraph.
</p>
<p>
Next, we&#39;ve got the backbone of the Internet, the hyperlink, or anchor. This element has an additional kink, in that it requires a couple of attributes. The element is defined by the &lt;a&gt;&lt;/a&gt; tags, but doing &lt;a&gt;http://strivinglife.net/&lt;/a&gt; just isn&#39;t enough. Rather, you have to use a href attribute. &lt;a href=&quot;http://strivinglife.net/&quot;&gt;http://strivinglife.net/&lt;/a&gt;. You can then change the text between the tags to be the clickable text. &lt;a href=&quot;http://strivinglife.net/&quot;&gt;StrivingLife.net&lt;/a&gt; displays as <a href="http://strivinglife.net/">StrivingLife.net</a>.
</p>
<p>
At this point, we&#39;re going to stop, because this is quite enough to make you quite dangerous. There&#39;s a number of additional elements that can expand upon these capabilities, but you should first be able to use the above before you go too much deeper.
</p>
<p>
Practice these elements now by taking some text and copying it into Notepad. Now, make some text bold, some italics, and throw in a couple of links. Save the file to your desktop with a .html extension (but don&#39;t close the file in Notepad). You may need surround the file name with double quotes in order to make this happen (otherwise, it may attempt to save as .html.txt). Browse to your desktop and open the file with the browser of your choice.
</p>
<p>
Now, go back to the file in Notepad and use the paragraph tags to make the appropriate paragraph breaks. Save the file again and refresh, or re-open the file in your browser. Tweak additional text as necessary.
</p>
<p>
With that, you&#39;ve got just enough HTML knowledge to be dangerous.
</p>

