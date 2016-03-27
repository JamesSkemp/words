+++
title = "Connecting to a WRT54G with a HP iPAQ 110"
description = "After playing around with settings, I was finally able to access my wireless network with my HP iPAQ 110."
draft = false
comments = true
date = "2008-10-04T11:50:00-05:00"
modified = "2008-10-04T11:49:50-05:00"
slug = "Connecting-to-a-WRT54G-with-a-HP-iPAQ-110"
blogengine = "b206f6c9-4db7-4828-a314-543302ba5c92"
categories = ["article", "tutorials / guides"]
tags = ["hp"]
+++

<p>
After playing around with settings, I was finally able to access my wireless network with my HP iPAQ 110. Here&#39;s what I did. 
</p>
<ol>
	<li>Under Wireless &gt; Wireless Security, set the model to WEP, setting a passphrase and generating keys.</li>
	<li>Make sure your wireless is enabled.</li>
	<li>Once the network shows in your iPAQ, set the Authentication to Shared and the Data Encryption to WEP.</li>
	<li>Select the key index and enter the key equal to the Default Transmit Key from the WRT54G.</li>
	<li>Check &quot;Use IEEE 802.1x network access control&quot;, and an EAP type of PEAP.</li>
</ol>
<p>
That&#39;s it - you should be able to connect now. 
</p>

