+++
title = "Working with Virtual Hard Disks in Windows 7 and Server 2008 R2"
summary = "With the new versions of Windows, Virtual Hard Disks (VHDs) are no longer just for virtualized environments."
draft = false
comments = true
date = "2010-06-20T19:02:00-05:00"
modified = "2010-06-20T19:16:44-05:00"
slug = "Working-with-Virtual-Hard-Disks-in-Windows-7-and-Server-2008-R2"
blogengine = "03e430c1-376b-4470-b360-365e0bb6500f"
categories = ["software"]
tags = ["windows 7", "windows server 2008 r2", "virtualization"]
+++

<p>A new feature in Windows 7 and Windows Server 2008 R2 is the ability to work with Virtual Hard Disks (VHDs) directly within the OS, by booting from them or mounting them as additional drives.</p>
<p>While I've had a good deal of experience with using VHDs in virtual environments, being able to work with VHDs directly is fairly new, and leaves some question as to how useful it could potentially be, since I'm happy using VirtualBox to work with virtual machines when I need to do any testing.</p>
<h3>Creating a VHD</h3>
<p>It's extremely easy to create a new virtual hard disk.</p>
<p>Open the start menu and type "disk," then find "Create and format hard disk partitions" to open Disk Management. Under Action select Create VHD. Browse to or enter a location where to store the disk, what size to create,&nbsp;and select the format of disk to use (fixed size being universally recommended, from what I can).</p>
<p>An unallocated disk will be added to the bottom half of the Disk Management window, and will be noted as 'not initialized.' Right click on the left-side - not on the display of the disk - and select "Initialize Disk" from the menu.</p>
<p>Take note of the note, and either change the partitation style (seemingly more applicable for larger disks) and press OK.</p>
<p>Next right-click on the display of the disk and select "New Simple Volume..." from the menu. A wizard will start which will walk you through the process of specifying a volume size, assigning a drive letter, and formatting the volume.</p>
<p>After a format the disk will be attached and AutoPlay should trigger.</p>
<h3>Working with the VHD</h3>
<p>Now that you have a VHD created and attached you can add new files to the drive, as you would with any other. Once you're finished with the disk you can detach the VHD back in Disk Management. (You also have the ability to delete it after removing it, if you so desire.)</p>
<p>If you need to add it back on later you can select Action &gt; Attach VHD to browse to the location of the virtual hard disk, and can even make it read only if needed.</p>
<h3>Working with VHDs in VirtualBox</h3>
<p>Unfortunately it doesn't appear that detached VHDs can be used in Sun's VirtualBox as additional drives.</p>
<h3>Encryption and security considerations</h3>
<p>Short of a higher-end version of Windows 7, or a third-party application, it doesn't appear that any level of encryption is available on created VHDs, which limits their use as storing secured documents. However, excluding times when the VHD is attached, Windows (7) doesn't appear to search within them, which means they may still serve against non-technical users.</p>
<h3>Portability</h3>
<p>The fact that they can't be attached directly via VirtualBox is unfortunate, but doesn't mean that the VHDs couldn't serve to consolidate information into a single file, which could then be copied from computer to computer, as needed. While we lose out on compression, in the case of using some sort of compressed file format, we seemingly get faster access to the content.</p>
<p>Definitely further testing is required.</p>
<h3>Additional information</h3>
<p>Microsoft has a <a rel="external" href="http://www.microsoft.com/downloads/details.aspx?familyid=D2AFACBB-5AF6-45C2-B275-932116E27B0B&amp;displaylang=en">Virtual Hard Disk Getting Started Guide</a>, but it focuses more on the administrative benefits of using VHDs for building new PCs, or testing, as opposed to using them as virtual drives.</p>
