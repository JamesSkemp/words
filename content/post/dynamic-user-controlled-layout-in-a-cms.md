+++
title = "Dynamic user-controlled layout in a CMS"
description = "Thoughts on a way to create a layout, in a vein similar to the W3C's template-based positioning draft specification, but easier, in my opinion. [slnet0514:bb48c7ca-03dc-4d43-b35f-abcfa32b40be]"
draft = false
comments = true
date = "2008-05-25T15:00:00-05:00"
modified = "2009-10-31T19:09:58-05:00"
slug = "Dynamic-user-controlled-layout-in-a-CMS"
blogengine = "bb48c7ca-03dc-4d43-b35f-abcfa32b40be"
categories = ["article", "Internet", "software", "technology"]
tags = ["css"]
+++

<p>This article is meant to hold some of the thoughts that I've been having about allowing a user to control the layout of a page, in particular for use within a content management system (CMS). The system would need to be able to support a user creating templates easily, but hopefully without the use of tables.</p>
<p>In the <a rel="external" href="http://www.w3.org/TR/css3-layout/">CSS Advanced Layout Module</a>, there is a draft specification for Template-based positioning.</p>
<p>This uses @, . and letters to specify not only how the content is to appear, but also where the content appears. That is,&nbsp;.&nbsp;are used for whitespace and letters and @ are used for content placeholders.</p>
<p>For example, a first page of a newspaper might have the following&nbsp;template (bottom of <a rel="nofollow" href="http://www.w3.org/TR/css3-layout/#templates">3.7</a>):</p>
<blockquote>
<p>display: "A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A" / 5cm<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ".&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; ." / 0.25cm<br />&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; E&nbsp; E&nbsp; E&nbsp; .&nbsp; F&nbsp; F&nbsp; F"<br />&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; E&nbsp; E&nbsp; E&nbsp; .&nbsp; F&nbsp; F&nbsp; F"<br />&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; E&nbsp; E&nbsp; E&nbsp; .&nbsp; F&nbsp; F&nbsp; F"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; * 3em * 3em * 3em * 3em *</p>
</blockquote>
<p>This would give a header (A), an article&nbsp;spanning the full&nbsp;left-side of the page (B), two main stories (C and D), and two smaller stories (E and F). The specification also has information about sizing, which you see at the far right and bottom.</p>
<p>While I like this, ultimately for the Web you'll have content that fills it's slots, usually. So, we could simplify this, I think, by making it as follows:</p>
<blockquote>
<p>display: "A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A&nbsp; A"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ".&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; .&nbsp; ."<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C&nbsp; C"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D&nbsp; D"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; .&nbsp; E&nbsp; E&nbsp; E&nbsp; .&nbsp; F&nbsp; F&nbsp; F"</p>
</blockquote>
<p>In addition to dropping the sizing information, I've removed any duplicate row. While it doesn't immediately give us an indication of what the page will look like, as the first case does, it's actually pretty close - we still can determine what the content is, and how it spans.</p>
<p>However, I'm not sure that this adequately states the layout that is desired. If you examine the image that was used, copied below, you'll notice something.</p>
<p style="text-align: center"><img title="W3C example newspaper layout" src="http://media.jamesrskemp.com/graphics/w3c_newspaper.png" alt="W3C example newspaper layout" width="512" height="724" /></p>
<p>First, using the far left-side column as our guide, we've actually got five columns on this page (look at the very last 'line' on the page). In other words, the following line is incorrect.</p>
<blockquote>
<p>"B&nbsp; .&nbsp; E&nbsp; E&nbsp; E&nbsp; .&nbsp; F&nbsp; F&nbsp; F"</p>
</blockquote>
<p>Instead, this should actually be as follows.</p>
<blockquote>
<p>"B&nbsp; .&nbsp; E&nbsp; E&nbsp; .&nbsp; F&nbsp; F"&nbsp;&nbsp;</p>
</blockquote>
<p>Obviously, this would continue on up through all the lines.</p>
<p>Also, spacing can be determined via other CSS methods, and should not be a part of the template itself. It seems unnecessary to using periods for spacing, when we've already defined content areas.</p>
<p>Therefore, I believe we could end up with something like the following, using this system.</p>
<blockquote>
<p>display: "A&nbsp; A&nbsp; A&nbsp; A&nbsp; A"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; C&nbsp; C&nbsp; C&nbsp; C"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp; D&nbsp; D&nbsp; D&nbsp; D"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "B&nbsp;&nbsp;E&nbsp; E&nbsp; F&nbsp; F"</p>
</blockquote>
<p>This states the following:</p>
<blockquote>
<p>Content&nbsp;A should span the entire top of the page.&nbsp;Below this, content B should span the entire left-side of the page, with content C, D, E and F on the right. Content C is displayed first, on its own row, followed by content D, with the same behaviour. Finally, content E and F are displayed, to the left and right, respectively, of the other. Content C and D should be twice as wide as content E and F. Likewise, content E/F should be twice as wide as content B.</p>
</blockquote>
<p>To continue, what would need to be parsed is the content within the quotes, and whitespace doesn't really matter. Therefore, we have the following as the core 'code.'</p>
<blockquote>
<p>A&nbsp;A&nbsp;A&nbsp;A&nbsp;A<br />B&nbsp;C&nbsp;C&nbsp;C&nbsp;C<br />B&nbsp;D&nbsp;D&nbsp;D&nbsp;D<br />B&nbsp;E&nbsp;E F F</p>
</blockquote>
<p>To the computer, assuming no more than 26 elements on a page (or 52 if lowercase characters were determined to be different than uppercase), this would be the same:</p>
<blockquote>
<p>AAAAA<br />BCCCC<br />BDDDD<br />BEEFF</p>
</blockquote>
<p>However, since spacing helps us, and to allow for the most content, we'll leave spaces in. (This could also allow a greater number of 'blocks' to be added to a page, even excluding allowing uppercase to be different than lowercase. For example, allowing&nbsp;AA and AB to be used.)</p>
<p>Getting back on track, I believe there's a different, and better, way to call out this content.</p>
<p>As stated above, we basically have a 5-column layout, of <em>x</em> width. The layout contains six elements of variable height.</p>
<p>The first row consists of one block spanning all five columns.</p>
<p>The second row consists of two blocks, one spanning one column, another spanning four.</p>
<p>The third row also consists of two blocks, one continuing to span one column, another spanning four.</p>
<p>Finally, the fourth row consists of three elements. The first column continues the element from the previous two rows, while the next, and last, two span two columns each.</p>
<p>Using only numbers, we have a layout something like the following.</p>
<blockquote>
<p>5<br />1 4<br />1 4<br />1 2 2</p>
</blockquote>
<p>However, based upon this layout alone, we don't know what content belongs where. Also, we can't clearly see that there is a left-side column that spans three rows. Using the following, however, might suggest that.</p>
<blockquote>
<p>5<br />1 4<br />0 4<br />0 2 2&nbsp;</p>
</blockquote>
<p>I use a 0 here because while there is an element there, it is not the first instance, or primary location, of that element. This system instantly gives us access to not only the placement of elements, in a general way, but also how many 'blocks' the content consists of.</p>
<p>If we&nbsp;were to&nbsp;create a layout for the standard three-column template, with a full header and footer, we'd have something like the following:</p>
<blockquote>
<p>3<br />1 1 1<br />3&nbsp;</p>
</blockquote>
<p>Here,&nbsp;while the blocks are designed by the template to be the same size, we could use CSS to&nbsp;effectively make the middle column much larger,&nbsp;instead of using the following:</p>
<blockquote>
<p>5<br />1 3 1<br />5&nbsp;</p>
</blockquote>
<p>Using these same CSS techniques,&nbsp;a standard two-column interface:</p>
<blockquote>
<p>2<br />1 1<br />2&nbsp;</p>
</blockquote>
<p>Perhaps in the three-column interface we no longer want the footer to display under the left-side column?</p>
<blockquote>
<p>3<br />1 1 1<br />0 2</p>
</blockquote>
<p>Don't display it under the right column either?</p>
<blockquote>
<p>3<br />1 1 1<br />0 1 0</p>
</blockquote>
<p>Now what if we want to put the left-side column up within the header, and put back our footer to span the full length of the bottom of the page?</p>
<blockquote>
<p>1 2<br />0 1 1<br />3</p>
</blockquote>
<p>How about on the right-side instead?</p>
<blockquote>
<p>2 1<br />1 1 0<br />3&nbsp;</p>
</blockquote>
<p>Since the first row would always contain the number of columns, we could simply do the necessary math to determine the number of core columns. If there is more than one number, you simply add all numbers together.</p>
<p>This also allows you to put&nbsp;the entire&nbsp;layouts information in one string. Using our last example, we&nbsp;could have something like "2 1; 1 1 0; 3;"&nbsp;(adding semi-colons at the end of every line, even the ending one). Or, "2 1, 1 1 0, 3," or any other character we may desire as a standard.</p>
<p>However, there's one thing that we may have missed.</p>
<blockquote>
<p>AAAAA<br />BCCCC<br />BDDDD<br />BEEFF</p>
</blockquote>
<blockquote>
<p>5<br />1 4<br />0 4<br />0 2 2&nbsp;</p>
</blockquote>
<p>As you can see, there's no easy way to link elements up with the content that they contain. What if we wanted to switch the second and third rows? With the first instance, that would be done, while in the second, it would need to be done outside of the core template.</p>
<p>On the one hand, the 'separate content from display' hand, that's okay. On the other hand, there's something to be said about keeping these things together.</p>
<p>Using the W3C proposal as a guideline, we could solve this by adding characters to our numbers.</p>
<blockquote>
<p>5:A<br />1:B 4:C<br />0:B 4:D<br />0:B 2:E 2:F</p>
<p>5:A&nbsp;, 1:B 4:C&nbsp;,&nbsp;0:B 4:D , 0:B 2:E 2:F ,</p>
</blockquote>
<p>It's questionable whether it's necessary to have 0:B instead of 0. However this would make it easier to add CSS without the use of another parser, such as a CMS (which would read/write this, as well as allow classes and ids to be assigned to the elements).</p>
<p>Also, the colons could change to something more applicable, such as a . or # (# would be similar to the existing CSS practice of using this for id declarations in CSS).</p>
<p>Thoughts? Are there instances where this wouldn't work? Would this be a suitable way for someone to learn how to create a layout, or is it at least easier than the W3C proposal ( :) )?</p>
<p>My next step with this will be to determine if&nbsp;a solution could be created that would read a string formatted like this, and then create a page based upon it, probably using tables before moving onto CSS.</p>
