+++
title = "XML creation: Part 1"
description = "In this guide, I'll be creating an XML file to store the Playstation games I own, and ultimately make the XML file 'pretty' for Web browsers. In part one, I'll be going over the idea and a layout that I think will work. [slnet0514:1ccd5b25-444f-4cd9-bcb8-17c1de673d17]"
draft = false
comments = true
date = "2007-12-25T21:00:00-06:00"
modified = "2007-12-25T21:14:14-06:00"
slug = "XML-creation-Part-01"
blogengine = "1ccd5b25-444f-4cd9-bcb8-17c1de673d17"
categories = ["tutorials / guides"]
tags = ["xml"]
+++

<p>
In this guide, I&#39;ll be creating an XML file to store the Playstation games I own, and ultimately make the XML file &#39;pretty&#39; for Web browsers. I&#39;ve done this in the past, with my <a href="http://jamesrskemp.net/vehicle_gas.xml" target="_blank">vehicle gas XML document</a>. 
</p>
<div class="note">
<p>
In part one, I&#39;ll be going over the idea and a layout that I think will work. 
</p>
</div>
<h3>The idea</h3>
<p>
The XML file that I want to create should be able to store all of my Playstation games. Since I own games for multiple generations of the Playstation, I&#39;ll want to be able to distinguish between them. 
</p>
<p>
I also want to continue to store the information that I&#39;m storing elsewhere, namely, the date I purchased the game, where I purchased it and for how much, as well as whether I sold the game, and, ultimately, whether I still own it. 
</p>
<h3>The structure</h3>
<p>
Now that I have an idea of what I&#39;ll want to store, I can start digging into how the XML file should be structured. 
</p>
<p>
First, since I&#39;ll be storing a number of games, I&#39;ll want to wrap them all. 
</p>
<p>
Under that, I&#39;ll have each individual game. 
</p>
<p>
For each game, there will be a title, as well as a system, purchase and sell information, including date and price, information about whether I still own it, and any notes. 
</p>
<p>
We then have a basic structure something like the following. 
</p>
<ul>
	<li>games 
	<ul>
		<li>game 
		<ul>
			<li>
			<div>
			title 
			</div>
			</li>
			<li>
			<div>
			system 
			</div>
			<ul>
				<li>
				<div>
				console 
				</div>
				</li>
				<li>
				<div>
				version 
				</div>
				</li>
			</ul>
			</li>
			<li>
			<div>
			purchase 
			</div>
			<ul>
				<li>date</li>
				<li>
				<div>
				price 
				</div>
				</li>
				<li>
				<div>
				place 
				</div>
				</li>
			</ul>
			</li>
			<li>
			<div>
			sell 
			</div>
			<ul>
				<li>
				<div>
				date 
				</div>
				</li>
				<li>
				<div>
				price 
				</div>
				</li>
			</ul>
			</li>
			<li>
			<div>
			own 
			</div>
			</li>
			<li>
			<div>
			notes 
			</div>
			</li>
		</ul>
		</li>
		<li>game ...</li>
		<li>game ...</li>
	</ul>
	</li>
</ul>
<p>
We&#39;ll start with this structure and start adding data, to see if it still makes sense. 
</p>

