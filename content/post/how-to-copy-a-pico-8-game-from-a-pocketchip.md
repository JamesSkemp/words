+++
description = "Information on how to copy a PICO-8 game from a PocketCHIP."
author = "James Skemp"
tags = [
  "pico-8",
  "mac os x",
]
date = "2016-11-19T19:43:54-06:00"
title = "How to Copy a PICO-8 Game From a PocketCHIP"
categories = [
  "gaming",
  "technology",
  "tutorials / guides",
]
draft = false

+++

Having recently received my [PocketCHIP][pocketchip] I decided to start going through [PICO-8 Zine #1][picozine1] and its first tutorial.

However, being the person I am, I hadn't written too many lines before I started wondering how I could source control the games I work on on my new PocketCHIP.

Since I'm using a MacBook Pro, here's how I was able to copy my games off of my PocketCHIP and get them into git.

## Finding the PocketCHIP

We'll assume that the PocketCHIP has already been connected to your wireless network.

Next we'll need to find the IP of the PocketCHIP on the server.

There are two ways to determine the IP.

1. `sudo ifconfig` entering **chip** as the password when prompted.
2. `ip addr show wlan0` will also return the IP address, without the extra information that the first option does.

Make note of the IP as we'll need it later to connect into the PocketCHIP.

## Setting up the PocketCHIP

For ease we're going to SSH into the PocketCHIP, since it's relatively easy to get it setup, and it's supported by Mac OS X.

Newer iterations of the PocketCHIP don't have SSH support enabled, so we'll start by updating packages on the PocketCHIP.

	sudo apt-get update

Next we'll install OpenSSH so we can SSH into the PocketCHIP.

	sudo apt-get install openssh-server

We should be able to see that the process is running, without having to restart the device.

	prep -l sshd

> You can also run this to see if your PocketCHIP already has SSH support.

## Creating a Git Repo

Since I want to be able to version control my games, I'll need to create a git repo to store them.

While I could create one locally, I decided to create a remote repo on GitHub for [my PICO-8 projects](https://github.com/JamesSkemp/pico-8-projects) and clone it.

	git clone git@github.com:JamesSkemp/pico-8-projects.git

## Connecting to the PocketCHIP

Now that we have SSH installed and the IP of the device, we can connect in from a MacBook Pro, or the like.

We can SSH in, but in this case I'm going to show how to copy a specific game from the PocketCHIP.

In my case I opted to create a new **projects** directory within the PICO-8 games directory for my games. On the PocketCHIP the games directory is actually a hidden directory, located at **.lexaloffle/pico-8/carts**.

	scp chip@192.168.XXX.YYY:/home/chip/.lexaloffle/pico-8/carts/projects/squashy.p8 pico-8-projects/squashy.p8

With the command above I'm copying the saved game from the PocketCHIP to my copy of the projects repo locally.

[pocketchip]: https://getchip.com/pages/pocketchip
[picozine1]: https://sectordub.itch.io/pico-8-fanzine-1
