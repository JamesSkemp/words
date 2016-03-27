+++
title = "Configuring a libGDX project to run as a desktop application in Android Studio"
description = "The following will quickly cover how to setup a newly imported libGDX project to run a desktop application, via Android Studio 1.1.0."
draft = false
comments = true
date = "2015-03-13T19:02:56-05:00"
slug = "Configuring-a-libGDX-project-to-run-as-a-desktop-application-in-Android-Studio"
blogengine = ""
categories = ["tutorials / guides"]
tags = ["android", "libgdx", "android studio"]
+++

<p>The following will quickly cover how to setup a newly imported libGDX project to run a desktop application, via Android Studio 1.1.0.</p>

<p>This assumes that you have already created a new libGDX project and have already imported it into Android Studio. If you have not, please review <a href="/words/Post/Creating-your-first-libgdx-project-with-Android-Studio-1-1-0">Creating your first libgdx project with Android Studio 1.1.0</a>.</p>

<p>With the project imported, select the configurations drop-down, or navigate to Run > Edit Configurations...` in the menu.</p>

<p>Next click the green plus sign in the top left corner and select 'Application.'</p>

<p>There are now four fields you need to populate to complete this step.</p>

<p><strong>Name</strong>: Enter whatever you'd like. I like using 'Desktop' to be obvious.</p>

<p><strong>Main class</strong>: com.<em>xxx</em>.desktop.DesktopLauncher</p>

<p><strong>Working directory</strong>: C:\Path\to\project\android\assets</p>

<p><strong>Use classpath of mod</strong>: select the <em>desktop</em> module</p>

<p>And that's it. You should be able to select and run the configuration.</p>

<p>If you work on multiple machines, note that by default this configuration change will mostly likely <em>not</em> be checked into source control. The file that contains this configuration is located in your project directory under <code>\.idea\workspace.xml</code>.</p>
