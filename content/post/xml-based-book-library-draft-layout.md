+++
title = "XML-based book library: Draft layout"
description = "Draft design of an xml for keeping track of a collection of books."
draft = false
comments = true
date = "2009-01-03T08:28:00-06:00"
modified = "2009-01-03T11:39:58-06:00"
slug = "XML-based-book-library-Draft-layout"
blogengine = "84fb1873-9e70-418c-9e76-33fa209bae3c"
categories = ["article", "StrivingLife"]
tags = ["xml"]
+++

<div class="note">
<p>
01/03/2009 @ 10:39 CT: The&nbsp;current&nbsp;version of the XML Schema I came up with is available for public use at <a href="http://media.jamesrskemp.com/xsd/MyBooks.xsd">http://media.jamesrskemp.com/xsd/MyBooks.xsd</a> 
</p>
</div>
<p>
Currently I have a SQL database (converted from an Access database) of all of the books that I own, as well as when I read them, how much I paid, etcetera. 
</p>
<p>
Since I&#39;m moving a good deal of information into XML, I figured I&#39;d attempt to move this into XML as well. 
</p>
<p>
Here&#39;s my draft: 
</p>
<ul>
	<li>
	<div>
	books 
	</div>
	<ul>
		<li>
		<div>
		book id=&quot;&quot; 
		</div>
		<ul>
			<li>
			<div>
			title 
			</div>
			</li>
			<li>
			<div>
			<em>author</em> 
			</div>
			</li>
			<li>
			<div>
			<em>editor</em> 
			</div>
			</li>
			<li>
			<div>
			purchase 
			</div>
			<ul>
				<li>
				<div>
				<em>date</em> 
				</div>
				</li>
				<li>
				<div>
				<em>place</em> 
				</div>
				</li>
				<li>
				<div>
				<em>price</em> 
				</div>
				</li>
			</ul>
			</li>
			<li>
			<div>
			pages 
			</div>
			</li>
			<li>
			<div>
			<em>sell</em> 
			</div>
			<ul>
				<li>
				<div>
				<em>date</em> 
				</div>
				</li>
				<li>
				<div>
				<em>price</em> 
				</div>
				</li>
			</ul>
			</li>
			<li>
			<div>
			<em>isbn10</em> 
			</div>
			</li>
			<li>
			<div>
			<em>isbn13</em> 
			</div>
			</li>
			<li>
			<div>
			readings read=&quot;&quot; 
			</div>
			<ul>
				<li>
				<div>
				read (unbound) 
				</div>
				<ul>
					<li>
					<div>
					<em>start</em> 
					</div>
					</li>
					<li>
					<div>
					<em>end</em> 
					</div>
					</li>
				</ul>
				</li>
			</ul>
			</li>
			<li>
			<div>
			notes&nbsp; 
			</div>
			</li>
			<li>
			<div>
			<em>keywords</em> 
			</div>
			<ul>
				<li>
				<div>
				<em>keyword</em> (unbound) 
				</div>
				</li>
			</ul>
			</li>
		</ul>
		</li>
	</ul>
	</li>
</ul>
<p>
Items in <em>italic</em> are optional. 
</p>
<h3>Reasoning</h3>
<p>
Currently I allow for or use&nbsp;the following data: 
</p>
<ul>
	<li>
	<div>
	id 
	</div>
	</li>
	<li>
	<div>
	title 
	</div>
	</li>
	<li>
	<div>
	author 
	</div>
	</li>
	<li>
	<div>
	editor 
	</div>
	</li>
	<li>
	<div>
	bought 
	</div>
	</li>
	<li>
	<div>
	start 
	</div>
	</li>
	<li>
	<div>
	finish 
	</div>
	</li>
	<li>
	<div>
	paid 
	</div>
	</li>
	<li>
	<div>
	store 
	</div>
	</li>
	<li>
	<div>
	info 
	</div>
	</li>
	<li>
	<div>
	pages 
	</div>
	</li>
	<li>
	<div>
	story 
	</div>
	</li>
	<li>
	<div>
	read 
	</div>
	</li>
	<li>
	<div>
	sort 
	</div>
	</li>
	<li>
	<div>
	philosophy 
	</div>
	</li>
	<li>
	<div>
	sold 
	</div>
	</li>
	<li>
	<div>
	sold price&nbsp; 
	</div>
	</li>
</ul>
<p>
Fortunately, I read my books multiple times, but that also causes issues with a single field for a start and end date. To work against this a delimited the field with a semi-colon. 
</p>
<p>
I never really used story much, and there must be a better way to sort my books, especially since it allows one option to be selected. The philosophy field is nice, but I don&#39;t know that that&#39;s applicable to a larger audience. To fight against this I&#39;ve instead added a keywords element, which allows for multiple sub-elements. 
</p>
<p>
I wanted to add ISBN so that I could better track which books I have, as well as potentially join this to Amazon (Associates). 
</p>
<h3>Problems</h3>
<p>
There are a couple of issues with this design. 
</p>
<p>
First, I have books that I have read, but I have no start or end date. I&#39;ve made the elements optional, but if I have neither then I have nothing but an empty read element. 
</p>
<p>
Should ISBN-10/13 be elements, or attributes of the title? 
</p>
<p>
Should the purchase elements&#39; children be elements or attributes? 
</p>
<p>
Should pages be an element or attribute? 
</p>
<p>
Unfortunately, there isn&#39;t already an XML example available that covers all of this additional information. So, I&#39;m building on virgin ground (at least as far as what others make available to the world, and what Google finds in the first part of their results). 
</p>
<p>
I realize that this isn&#39;t the best place to post if I want answers soon, but, am I missing anything? 
</p>

