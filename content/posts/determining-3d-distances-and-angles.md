+++
title = "Determining 3D Distances and Angles"
summary = "Mathematical formulas for determining three dimensional distances as well as angles. Helpful for 'camera to object' and 'light to object' distances (for POV-Ray&trade;)."
draft = false
comments = true
date = "2006-09-04T13:17:00-05:00"
slug = "Determining-3D-Distances-and-Angles"
blogengine = "581c99f0-9b98-421a-9ce3-ac04ef854b01"
categories = ["article"]
tags = []
+++

<p>
Near the top of one of the sections in the POV-Ray&trade; 3.5 manual there is a quote about wishing that past mathematical formulas were remembered, or something to that effect. I too wish I had remembered what I had learned in some of my past math classes, but after a bit of research, I have begun to work on some of the information that I have forgotten. Here is one of those areas.
</p>
<h3>Determining 3D Distances:</h3>
<p>
Given two points, point A (located at &lt;x<sub>A</sub>, y<sub>A</sub>, z<sub>A</sub>&gt;) and point B (located at &lt;x<sub>B</sub>, y<sub>B</sub>, z<sub>B</sub>&gt;), the distance between these two points (AB) can be determined by the formula:<!--adsense-->
</p>
<p align="center">
|AB| = &radic;[(x<sub>B</sub> - x<sub>A</sub>)<sup>2</sup> + (y<sub>B</sub> - y<sub>A</sub>)<sup>2</sup> + (z<sub>B</sub> - z<sub>A</sub>)<sup>2</sup>]
</p>
<p>
In other words, take each x/y/z coordinate and subtract it from the other (remembering that if you take B-A you must continue to do so in that order). Then, square the value for each coordinate and add them all together. Taking the square root of that sum will give you the distance from the second point to the first. Simply take the absolute value of the square root to get the absolute distance.
</p>
<p>
For example:
</p>
<p>
<strong>Example One:</strong> Given point A &lt;5, 0, 0&gt; and point B &lt;6, 7, 0&gt;, what is the distance between these two points?
</p>
<p>
How to do it: First, we take 5 from 6, 0 from 7, and 0 from 0. (6-5) = 1, (7-0) = 7, (0-0) = 0
</p>
<p>
Square each term and add them together: 1<sup>2</sup> + 7<sup>2</sup> + 0<sup>2</sup> = 1 + 49 + 0 = 50
</p>
<p>
Take the square root of the resulting term: &radic;(50) = 7.071 or &radic;(5 * 5 * 2) = 5&radic;(2)
</p>
<p>
<strong>Example Two:</strong> Given point A &lt;1, 7, -3&gt; and point B &lt;-5, 4, -2&gt;, what is the distance between these two points?
</p>
<p>
How to do it: First, we take 1 from -5, 7 from 4, and -3 from -2. (-5-1) = -6, (4-7) = -3, (-2--3) = (-2 + 3) = 1
</p>
<p>
Square each term and add them together: -6<sup>2</sup> + -3<sup>2</sup> + 1<sup>2</sup> = 36 + 9 + 1 = 46
</p>
<p>
Take the square root of the resulting term: &radic;(46) = 6.782
</p>
<p>
Knowing how to determine the distance between two three-dimensional points is 
necessary to determine 3D angles ...
</p>
<h3>Determining 3D Angles:</h3>
<p>
Determining 3D angles can be helpful in POV-Ray<font>&trade;</font>, if, for instance, you would 
like to view the scene from a certain angle and would also like to know the 
respective distances. It would be a good idea to know how to determine 3D 
distance in order to get all that you can from this...
</p>
<p>
First of all, it is important that you remember, or have knowledge of 
soh-cah-toa. Id est:
</p>
<p align="center">
sin(<em>angle</em>) = [(opposite length) / (hypotenuse length)]<br />
cos(<em>angle</em>) = [(adjacent length) / (hypotenuse length)]<br />
tan<em>(angle</em>) = [(opposite length) / (adjacent length)]
</p>
<p>
So, given two points, one could make a box from those two points (even if the box has 0 length/width/depth). Any box can be split into two triangles of the same basic shape. A triangle has three angles and three sides. Using the formulas above, if given one angle and one side, we could determine all other angles and sides. So, if we have one corner (which is the look at point for instance) and another corner (which is the camera for instance) we could easily determine the angle(s) between them. How about an example:
</p>
<ol>
	<li>A camera situated at &lt;5, 5, -5&gt; is looking at the origin &lt;0, 0, 0&gt;. What is the angle that the camera is looking at the origin?
	<ol>
		<li>There are two ways to go about solving this problem, however, for this page I will stick with one way.</li>
		<li>Already we have one side of the triangle. The camera is located &#39;up&#39; 5 points from the origin. Therefore, one side of the triangle has a length of 5.</li>
		<li>By determining the distance from the camera to the origin, which is 5&radic;(3), we have yet another length. This length is the hypotenuse length, since it is the side opposite of the 90&deg; angle.</li>
		<li>Now, it is easiest to use the angle at the origin (in this case, it is an angle that opens above the positive x-plane, negative z-plane, and into the positive y-plane. Right, up, and back...</li>
		<li>The opposite side would be the y-coordinate that we determined in #2, which is 5. The hypotenuse length is what we determined in #3, which is 5&radic;(3). Since we have the opposite length and hypotenuse length, we would take the inverse-cos to determine the angle.</li>
		<li>So, cos<sup>-1</sup>{(5)/[5&radic;(3)]} = cos<sup>-1</sup>{(1)/[1&radic;(3)]} = cos<sup>-1</sup>(0.5774) = 54.73561&deg;.</li>
		<li>However, this is the angle from the origin to the camera, so if we wanted to determine it from the other way, we would simply take the angle * -1, or switch the sign in the front of the angle.</li>
		<li>We could also determine #6 from the camera. However, the opposite length would become the adjacent length and the hypotenuse length would stay the same. We would also have to take the inverse-sin of the value.</li>
		<li>So, sin<sup>-1</sup>{(5)/[5&radic;(3)]} = sin<sup>-1</sup>{(1)/[1&radic;(3)]} = sin<sup>-1</sup>(0.5774) = 35.26439&deg;. Taking this from 90 (as this value is the angle from the y to the xz, instead of the xz to the y, which is what we really want) we get our correct value of 54.73561&deg;.</li>
		<li>In other words and using the image below, &quot;look at pt&quot; is the origin, &quot;look from pt&quot; is the camera, &quot;h&quot; is the distance determined in #3, &quot;o or a&quot; was not determined in this example, and &quot;a or o&quot; was the distance determined in #2. The angle determined in #6 would be the angle at &quot;look at pt&quot;, while that determined in #9 would be the angle <u>inside</u> the triangle at &quot;look from pt&quot;, followed by the angle <u>outside</u> the triangle at &quot;look from pt&quot;.</li>
	</ol>
	</li>
</ol>
<p style="text-align: center">
<img style="width: 209px; height: 113px" src="/files/2006/09/triangle.jpg" alt="Triangle with appropriate adjacent, hypotenuse and opposite lengths" /><br />
From look at pt, (a or o) would be opposite and (o or a) adjacent.<br />
From look from pt, (a or o) would be adjacent and (o or a) would be opposite.
</p>
<hr />
<p>
<strong>Primarily Written/Added:</strong> August 14th 2002/October 17th 2002<br />
<strong>
Edited/Updated:</strong> November 21st 2002; March 6th 2003; November 5th 2003; September 4 2006.
</p>
<p>
Thanks to Dave Cousineau for pointing out a mistake that stuck around for over 4 years :D
</p>

