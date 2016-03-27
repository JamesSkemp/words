+++
title = "The major failing of Akismet ..."
description = "What's the one major failing of Akismet?  No information about what IPs were used to deliver that spam."
draft = false
comments = true
date = "2007-02-25T08:57:00-06:00"
modified = "2009-10-15T07:54:00-05:00"
slug = "The-major-failing-of-Akismet"
blogengine = "07e25f53-08d2-4255-b341-f56e5c39d033"
categories = ["software"]
tags = ["wordpress", "mysql"]
+++

<p>The major failing of the Akismet plug-in is that you can't determine which IPs, if any, are spamming your site the most.</p>
<p>Akismet needs to have the ability to group by IP, as well as show counts for each IP.<!--more--></p>
<p>In place of that, you can run the following query to get this information.</p>
<pre class="code"><code class="sql">select comment_author_ip, count(comment_author_ip) count from wp_comments where comment_approved = 'spam' group by comment_author_ip order by count desc</code></pre>
<p>This query will display the IP of the user who posted a message flagged as spam, and will also display the number of times a user with that IP posted a spam message. Of course, since Akismet deletes comments marked as spam after a certain amount of time, you'll need to run this on a semi-regular basis.</p>
<p>After you have this list, check out where the IP address points to, and if you don't see your users coming from that IP, block it through htaccess. I recommend you also add the date you did this in the comments, so you're aware of why you added the IP. In three months, you may also want to unblock the IP and see what happens.</p>
<p>Of course, you can also use another plug-in to automate this, but after hearing bad stories about the plug-in - Bad Behaviour - I'm not quite willing to go that route yet. Maybe in a couple of months I'll give it a shot.</p>
