+++
title = "Using Xml4Ssp 1.3 Rev 1"
summary = "Quick guide on how to use Xml4Ssp to generate a gallery for SlideShowPro. [slnet0514:e9cc4dbe-87a8-492d-9806-00dedba6f961]"
draft = false
comments = true
date = "2008-02-24T08:50:00-06:00"
modified = "2008-02-24T08:48:55-06:00"
slug = "Using-Xml4Ssp-13-Rev-1"
blogengine = "e9cc4dbe-87a8-492d-9806-00dedba6f961"
categories = ["photography", "software", "tutorials / guides"]
tags = ["slideshowpro"]
+++

<p>
<a href="http://www.locandadelborgo.com/download/index.asp" target="_blank">Xml4Ssp</a> is a Windows XML generator for <a href="http://slideshowpro.net/" target="_blank">SlideShowPro</a>. While the program still needs some work, it&#39;s pretty usable as it is. 
</p>
<p>
Since there&#39;s no real documentation, I&#39;ll be covering how I ended up using it to generate my latest <a href="/gallery/" target="_blank">gallery</a>. 
</p>
<h3>Starting folder structure</h3>
<p>
I began with the following folder structure: 
</p>
<ul>
	<li>
	<div>
	casio_images 
	</div>
	<ul>
		<li>
		<div>
		&nbsp;Pearl 
		</div>
		<ul>
			<li>
			<div>
			FullsizeImage 
			</div>
			</li>
			<li>
			<div>
			Images 
			</div>
			</li>
			<li>
			<div>
			Thumb 
			</div>
			</li>
		</ul>
		</li>
	</ul>
	</li>
</ul>
<p>
The only folder that contained content was the FullsizeImage directory, in which I dumped my JPG originals. 
</p>
<h3>Xml4Ssp setup</h3>
<p>
Assuming it&#39;s already installed and started, I created a New gallery. 
</p>
<p>
Next, I browsed to the gallery folder, and began filling out the rest as follows. 
</p>
<blockquote>
	<p>
	<strong>Browse gallery folder</strong>:<strong> </strong>C:\Documents and Settings\Owner\Desktop\temp\casio_images 
	</p>
	<p>
	Album options 
	</p>
	<blockquote>
		<p>
		<strong>Images folder name:</strong> FullsizeImag<br />
		<strong>Album Title/Description:</strong> Use Foldername<br />
		<strong>Use Permalinks:</strong> None 
		</p>
	</blockquote>
	<p>
	Image options 
	</p>
	<blockquote>
		<p>
		<strong>Search for:</strong> JPG<br />
		<strong>Images caption:</strong> Use Filename<br />
		<strong>Use Hyperlink:</strong> None<br />
		<strong>Larger Image Folder:</strong> FullsizeImage 
		</p>
	</blockquote>
	<p>
	Thumb Options 
	</p>
	<blockquote>
		<p>
		<strong>Thumb folder name:</strong> Thumb<br />
		<strong>Create Thumbnails</strong> (checked)<br />
		<strong>Width:</strong> 100<br />
		<strong>Height:</strong> 75<br />
		Constrain proportion by Width<br />
		<strong>Resize method:</strong> nearest neighbor (Default)<br />
		<strong>Quality:</strong> 50 
		</p>
	</blockquote>
</blockquote>
<h3>Cleanup</h3>
<p>
Once I generated, it successfully created the thumbnails, but did not create the resized images. This leads me to believe that the FullsizeImage directory is not resized at all. 
</p>
<p>
On the one hand this is good, on the other, it would be nice if it did. You can fix this by saving the generated XML file and changing the Thumb folder name to another directory. Next, change the width/height/constrains/quality accordingly. 
</p>
<p>
And with that, you&#39;ve generated a gallery, with the necessary XML file, in less than usual time! 
</p>

