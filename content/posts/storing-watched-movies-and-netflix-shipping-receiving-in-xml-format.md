+++
title = "Storing watched movies and Netflix shipping/receiving in XML format"
summary = "Thoughts on tracking movies and Netflix shipping/receiving information."
draft = false
comments = true
date = "2011-03-06T13:21:00-06:00"
modified = "2011-03-06T13:48:50-06:00"
slug = "Storing-watched-movies-and-Netflix-shipping-receiving-in-XML-format"
blogengine = "f364dcb5-aaa1-47a3-82d2-8c8a415c1b17"
categories = ["dvd / movie"]
tags = ["netflix", "movies", "xml"]
+++

<p>Ever since I started <a href="http://strivinglife.com/words/post/Netflix-shipping-for-Madison-WI.aspx">my Netflix subscription in September 2006</a> I've been keeping track of what movies I receive and when.</p>
<p>Unfortunately, as the years have gone by I've found it more and more difficult to easily look through the listings to see when I last watched a movie. Additionally, I've no longer been keeping track of what ratings I give movies, and why.</p>
<p>The initial goal was really to track when Netflix shipped and received movies, as well as when I mailed and received. This would suggest a pretty easy XML schema, since the key parts are as follows.</p>
<p>
<ul>
<li>Date</li>
<li>Type of update (Netflix shipped/received, I mailed/received, I streamed)</li>
<li>Name of movie/disc</li>
<li>Year of movie/series</li>
<li>Location mailed to (if I'm mailing)</li>
<li>Notes</li>
</ul>
</p>
<p>However, if I wish also to be able to store ratings, this format doesn't necessarily work, as multi-disc episodes, or re-watching a movie/show, would require the rating be placed multiple times.</p>
<p>Yet one might wonder if that's really that big of a deal, since we could always just pull the last rating, or rating could be optional to use whatever rating was given before.</p>
<p>Of course, if I make the listing Netflix centric then I always tie it to that service. While I have no plans on dropping my subscription (completely - I've been tempted to go streaming only for a couple of months), it also means I can't track movies that I own.</p>
<p>Which then suggests we make the XML schema movie-focused.</p>
<p>Our list of Movies would consist of Movie objects, which have a Title, Year, and Rating. Then within that would be a list of times I've watched the movie. Which might then really mean we do have two different XML files, since it doesn't necessarily make sense to keep track of that as part of the Movies XML.</p>
<p>For Netflix we could focus on Dates. We'd also want to keep track of the type of media (physical or streaming), and if physical, whether it was coming or going.</p>
<p>What mailers they send out is also important, so we can determine whether there's a method to what mailers are shipped. For example, is it always the location you receive a disc from, or are different mailing locations used?</p>
