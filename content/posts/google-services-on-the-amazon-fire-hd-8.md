+++
title = "Google Services on the Amazon Fire HD 8"
summary = "For my future reference, information on how to install Google services (Google Play and associated services) on an Amazon Fire HD 8."
draft = false
comments = true
date = "2015-12-13T14:35:42-06:00"
slug = "Google-Services-on-the-Amazon-Fire-HD-8"
blogengine = ""
categories = ["technology", "tutorials / guides"]
tags = ["amazon fire", "android"]
+++

<p>xda-developers has a post, <a href="http://forum.xda-developers.com/amazon-fire/general/installing-google-framework-playstore-t3216122" rel="external">Installing Google Framework/Playstore without Root (5th Gen Amazon Fire 2015)</a>, that includes a couple different sets of instructions.</p>

<p>What worked for me was grabbing the mega.nz zip download and then:</p>

<ol>
<li>Make sure you're a developer and you allow apps from unknown sources.</li>
<li>Install ES File Explorer via the Amazon Appstore. It's something I install on all my Android devices.</li>
<li>Extract the contents of the zip you downloaded from Mega somewhere.</li>
<li>Connect your Fire tablet to your computer via a USB cable.</li>
<li>Copy all the files to the Download directory on your tablet.</li>
<li>In ES File Explorer navigate to the Download directory.</li>
<li>Install com.android.vending-5.9-12*.apk</li>
<li>Install com.google.android.gms-6.6.03*.apk</li>
<li>Install GoogleLoginService.apk</li>
<li>Install GoogleServicesFramework.apk</li>
<li>Turn off and then turn back on the device.</li>
<li>You can try opening Google Play. If it automatically closes (it did for me), install com.android.vending-5.9.12*.apk again. When I did so it asked me if I wanted to install the update, and referenced one of the other services.</li>
<li>You should be able to run the Google Play application now.</li>
<li>When prompted, you can safely update the Google services.</li>
</ol>

<p>With Google Play installed I was able to login to Google, as well as install YouTube and Chrome to my Fire HD 8.</p>
