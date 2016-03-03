+++
title = "Setting up a Raspberry Pi 2 Samba server (in early January 2016)"
summary = "Instructions on how to setup a Raspberry Pi 2 Samba server with a Seagate Backup Plus Slim 1TB."
draft = false
comments = true
date = "2016-01-09T12:17:57-06:00"
modified = "2016-01-09T12:29:18-06:00"
slug = "Setting-up-a-Raspberry-Pi-2-Samba-server-(in-early-January-2016)"
blogengine = ""
categories = ["technology", "tutorials / guides"]
tags = ["raspberry pi 2", "nas"]
+++

<p>The following is how I configured a Raspberry Pi 2 as a samba server, using a Seagate Backup Plus Slim, 1TB, drive.</p>

<p>For ease I purchased the <a href="http://amzn.to/1MZjXM0">CanaKit Raspberry Pi 2 Complete Starter Kit</a>. It runs about $70 and includes enough to get up and running with the Raspberry Pi 2, with the Pi itself, a nice case, power supply, HDMI cable, WiFi adapter, and SD card with NOOBS/Raspbian installer.</p>

<p>For the hard drive I opted to purchase a <a href="http://amzn.to/1MZkg9F">Seagate Backup Plus Slim 1TB Portable External Hard Drive</a>, since I've had good enough luck with Seagate in the past, and reviews are generally favorable. This ran me $60. I confirmed that it worked fine on my Windows 10 machine, and was already formatted to NTFS.</p>

<p>Unfortunately, once I received the Pi and drive I found that the power supply/Pi wasn't putting off enough power to keep the drive running. After looking at the options, including tweaking the Pi to pass through more power through the USB connector, I opted to pick up a powered USB hub instead (especially since I was considering setting up a camera at some point in the future).</p>

<p>For this I went with the <a href="http://amzn.to/1MZktd6">AmazonBasics 4 Port USB 3.0 Hub with 5V/2.5A power adapter</a> for about $17. Reviews are quite favorable, and I didn't see any indication that it wouldn't work. Once I received the included manual does note that Windows 2000 through 8 are required, or Mac OS X. However, as you'll see there were no issues.</p>

<p>Before powering my Raspberry Pi 2 up I went ahead and plugged the USB Hub into the Pi, and the Seagate Backup Plus into the HUB. I powered up the HUB first, and then powered up the Pi.</p>

<p>While it was a couple years old, <a href="http://www.howtogeek.com/139433/how-to-turn-a-raspberry-pi-into-a-low-power-network-storage-device/">How to Turn a Raspberry Pi into a Low-Power Network Storage Device</a> worked fairly well for the setup steps.</p>

<h2>Setup commands</h2>

<p>Unless otherwise noted, all commands were run on the Raspberry Pi 2 itself, at the command line, outside of Raspbian.</p>

<p>While the guide suggests installing <strong>ntfs-3g</strong>, this was already installed on my Pi.</p>

<pre><code>sudo apt-get install ntfs-3g
</code></pre>

<p>Getting a listing of the disks, <code>sudo fdisk -l</code>, returned /dev/sda1 for the name of the Seagate drive. So, despite a moment of worry, the Amazon USB Hub worked perfectly fine.</p>

<p>The next step was to setup the drive. I opted for all lowercase when doing so.</p>

<pre><code>sudo mkdir /media/usbhdd1
</code></pre>

<p>Next was the mounting of the drive.</p>

<pre><code>sudo mount -t auto /dev/sda1 /media/usbhdd1
</code></pre>

<p>Within the directory I setup a new shares directory.</p>

<pre><code>sudo mkdir /media/usbhdd1/shares
</code></pre>

<p>When I first tried to install Samba I received a number of errors. A quick update resolved the issues.</p>

<pre><code>sudo apt-get update
</code></pre>

<p>Then I was able to install Samba.</p>

<pre><code>sudo apt-get install samba samba-common-bin
</code></pre>

<p>Backup the Samba configuration, just in case, and then open the config in <strong>nano</strong>.</p>

<pre><code>sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.old
sudo nano /etc/samba/smb.conf
</code></pre>

<p>My Windows 10 machine was already on the WORKGROUP workgroup, so I didn't have to touch this, but verify <em>workgroup</em> is set as needed.</p>

<p>Contrary to the guide I was unable to find a security line in the Authenication section, so I skipped that for now, and promised to try to get in without authenticating before I went too far.</p>

<p>At the bottom of the config I added the following:</p>

<pre><code>[Backup1]
comment = Backup Folder
path = /media/usbhdd1/shares
valid users = @users
force group = users
create mask = 0660
directory mask = 0771
read only = no
</code></pre>

<p><code>CTRL+X</code> will exit, and allow you to save. Press <code>Enter</code> to just overwrite the existing file.</p>

<p>Restart the Samba service:</p>

<pre><code>sudo /etc/init.d/samba restart
</code></pre>

<p>Now setup a user account in UNIX and then for Samba. Yes, this means entering the password 4 times. Personally, I'm a fan of <a href="http://preshing.com/20110811/xkcd-password-generator/">Preshing's xkcd Password Generator</a> and storing the credentials in <a href="http://keepass.info/">KeePass</a>.</p>

<pre><code>sudo useradd backups -m -G users
sudo passwd backups
sudo smbpasswd -a backups
</code></pre>

<p>For ease I then determined the ip of the Raspberry Pi.</p>

<pre><code>ifconfig
</code></pre>

<p>And then I just browsed to that directly in Windows explorer (<code>\\192.168.x.x</code>). Thankfully I was prompted for credentials when I tried to access the <strong>Backup1</strong> directory. Entering the credentials I had created above worked great.</p>

<p>The next step was to put some data in the directory. Over my wireless network speeds weren't fantastic, but it worked fine.</p>

<p>I verified the files had been copied over:</p>

<pre><code>cd /media/usbhdd1/shares
ls
</code></pre>

<p>Next was a step I almost forgot, which was to have the Raspberry Pi automatically mount the drive after rebooting. The config first needed to be opened in nano, <code>sudo nano /etc/fstab</code>, and then I had to add the following, which I did so at the end of the file.</p>

<pre><code>/dev/sda1    /media/usbhdd1     auto    noatime     0       0
</code></pre>

<p><code>Ctrl + x</code> as usual to exit, save, and overwrite the existing file.</p>

<p>Finally, restart the Raspberry Pi itself to verify that I could still get to the share after it came back up.</p>

<pre><code>sudo reboot</code></pre>
