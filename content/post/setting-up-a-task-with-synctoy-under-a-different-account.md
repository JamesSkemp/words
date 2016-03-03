+++
title = "Setting up a task with SyncToy under a different account?"
summary = "When setting up SyncToy, setup pairs using the account you'll be running the task under."
draft = false
comments = true
date = "2010-07-17T12:19:00-05:00"
modified = "2010-07-17T12:23:52-05:00"
slug = "Setting-up-a-task-with-SyncToy-under-a-different-account"
blogengine = "ea9128b6-cf0b-4673-be00-5c2793132312"
categories = ["software"]
tags = ["synctoy"]
+++

<p>Every time I setup SyncToy I always, <em>always</em>, forget to setup the folder pairs correctly.</p>
<p>SyncToy uses per-user folder pairs, which means that if you'll be running a scheduled task using a different user, you'll want to login as that user, setup the folder pairs in SyncToy, run the sync via SyncToy's interface, and then setup the task.</p>
<p>If you don't do this you'll just end up with a 0x1 return code.</p>
<p>As far as I can tell, there's no way to have users share folder pairs, or use one set for all users (current version is 2.1).</p>
