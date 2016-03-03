+++
title = "Multiple network adapters in VirtualBox, for Windows guests"
summary = "Setting up a second adapter for Windows guests in VirtualBox is easy, and seemingly safe."
draft = false
comments = true
date = "2009-07-02T14:59:00-05:00"
modified = "2009-07-02T15:51:59-05:00"
slug = "Multiple-network-adapters-in-VirtualBox-for-Windows-guests"
blogengine = "9eb7c605-221f-41b0-8265-f4d40543a968"
categories = ["tutorials / guides"]
tags = ["virtualization", "virtualbox"]
+++

<p>Having just upgraded to VirtualBox 3.0.0, I was running into an issue with being able to access a Windows Server 2003 guest from my Windows Vista host machine.</p>
<p>By default, when creating a Windows Server 2003 guest machine the Network settings are set such that Adapter 1 is PCnet-FAST III, attached to NAT. This allows the virtual machine to get outside, but not in.</p>
<p>However, it's possible to add a second adapter, attached to the host-only adapter. In this way you can access the outside world, as well as allow your host machine to access the guest via it's host-only ip (192.168.56.x, for example).</p>
<p>Unfortunately, there seems to be no way to set this on all future machines you create.</p>
<h3>Windows Server 2008</h3>
<p>The same, with a different adapter (use the default), is possible on Windows Server 2008, as well. If you're testing via ping-only (you've just set it up, for example) then you can temporarily disable the firewall for the specific adapter you setup&nbsp;as&nbsp;using the&nbsp;host-only adapter. Pinging the ip (from ipconfig) should then work, and provide the correct ip.</p>
<h3>Windows 7 RC</h3>
<p>As with Windows Server 2008, you'll need to turn off the firewall to allow pings by ip or computer name. Unfortunately, unlike Windows Server 2008, individual adapters do not seem to be listed in 7, so you'll either need to play with it, or just turn off the firewall for each network listed.</p>
<h3>For future use ...</h3>
<p>In the VirtualBox documentation, they have a pretty nice example of a network setup.</p>
<p>In this example there is a Web server and a database server. Both are setup as a host-only network. The Web server has an additional, bridged, network. This nicely cuts off the database server from the outside world.</p>
<p>Along these same lines, instead of using NAT for the first adapter, and having to create a second adapter, we could always just change to a bridged network. However, for my development needs, I don't see a reason to do so.</p>
