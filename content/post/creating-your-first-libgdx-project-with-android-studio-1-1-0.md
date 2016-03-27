+++
title = "Creating your first libGDX project with Android Studio 1.1.0"
description = "How to start using libGDX with Android Studio 1.1.0."
draft = false
comments = true
date = "2015-02-28T21:22:16-06:00"
modified = "2015-07-18T12:03:11-05:00"
slug = "Creating-your-first-libgdx-project-with-Android-Studio-1-1-0"
blogengine = ""
categories = ["tutorials / guides"]
tags = ["android", "libgdx"]
+++

<p>This is a quick 'tutorial' on how to get started with libGDX with Android Studio 1.1.0.</p>

<p>Unfortunately while libGDX can be used with Android Studio 1.x, documentation regarding it is sparse.</p>

<p>I'll assume that you have Android Studio 1.1.0 (1.x generally) installed and properly running.</p>

<p>If you haven't already, <a href="http://libgdx.badlogicgames.com/download.html">download libgdx</a> from the official site. The file name should be <em>gdx-setup.jar</em>, and will be run whenever you need to create a new project.</p>

<p>Start <em>gdx-setup.jar</em> and complete the Name, Package, Game class, and Destination as you wish.</p>

<p>For Android Studio 1.x the SDK is located in <code>%localappdata%\Android\sdk</code> and for beta versions was located in the Android Studio program files directory.</p>

<p>Sadly these values aren't tracked across runs of the jar, and will therefore need to be entered every time you run the tool.</p>

<p>Go ahead and Generate the project and after a short time you'll have a project created.</p>

<p>At the time of this writing you'll be prompted twice regarding different versions.</p>

<p>The first time will be the following:</p>

<blockquote>
  <p>You have a more recent version of android build tools than the recommended.</p>

  <p>Do you want to use this version?</p>
</blockquote>

<p>The second time is the following:</p>

<blockquote>
  <p>You have a more recent Android API than the recommended.</p>

  <p>Do you want to use this version?</p>
</blockquote>

<p>Select Yes for both options.</p>

<p>Once the tool has finished switch over to Android Studio and select <em>Import Project (Eclipse ADT, Gradle, etc.)</em> from the menu. Then browse to the directory created by the jar (Destination) and open the <code>build.gradle</code> file.</p>

<p>After some time you should be able to test a deployment of the Android version as you normally would. You may also be interested in <a href="/words/Post/Configuring-a-libGDX-project-to-run-as-a-desktop-application-in-Android-Studio">running your project as a Desktop application</a>.</p>
