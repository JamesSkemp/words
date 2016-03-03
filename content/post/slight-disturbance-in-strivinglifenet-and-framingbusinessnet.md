+++
title = "Slight disturbance in StrivingLife.net and FramingBusiness.net"
summary = "Slight disturbance on the site for the last two days. Yikes."
draft = false
comments = true
date = "2006-11-11T20:30:00-06:00"
slug = "Slight-disturbance-in-StrivingLifenet-and-FramingBusinessnet"
blogengine = "46675345-4444-4410-9dc9-0f35f8e0127d"
categories = ["StrivingLife"]
tags = []
+++

<p>
Due to a MySQL server going down, much of the content on StrivingLife.net and The Framing Business was unavailable yesterday and today.
</p>
<p>
What saved me was this little command, since one of my tables was locked (Gavin got off lucky).
</p>
<blockquote>
	REPAIR TABLE wp_posts use_frm
</blockquote>

