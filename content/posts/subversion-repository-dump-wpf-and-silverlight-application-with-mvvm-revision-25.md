+++
title = "Subversion repository dump: WPF and Silverlight application, with MVVM (revision 25)"
summary = "Subversion repository dump and export with code for a Visual Studio 2010 solution with WPF and Silverlight clients, using the sample Northwind database, and the MVVM pattern."
draft = false
comments = true
date = "2010-10-24T15:00:00-05:00"
modified = "2010-10-28T07:54:16-05:00"
slug = "Subversion-repository-dump-WPF-and-Silverlight-application-with-MVVM-revision-25"
blogengine = "90f89531-052b-4e49-b443-c0aa67319990"
categories = ["tutorials / guides"]
tags = ["mvvm", "visual studio", "subversion", "silverlight", "wpf", "resume"]
+++

<p>As&nbsp;alluded to&nbsp;in a previous post, <a href="http://strivinglife.com/words/post/Excellent-Silverlight-WPF-MVVM-video-series.aspx">in regards to an excellent Silverlight/WPF with MVVM tutorial</a>, I've begun looking into the MVVM pattern, as I begin moving towards WPF and Silverlight for applications.</p>
<p>Having fully watched the series twice, and begun a third watch working through the example, albeit with the Northwind sample database, I decided to share my labor with others.</p>
<p>To that end I present a Subversion repository dump with a fairly step-by-step look at how to go from nothing to a simple application with WPF and Silverlight support. Built in Visual Studio 2010, against .NET 4.</p>
<p>Download the Subversion (version 1.6.13) repository dump: <a rel="external download" href="http://media.jamesrskemp.com/download6s/NorthwindExamplesDump_rev25.zip">NorthwindExamples dump</a>.</p>
<p>The repository currently consists of 25 revisions, and does not <em>yet</em> include unit testing. (I need to re-watch those particular videos before I implement.) I also made one mistake with the ViewModel class not being public, but ... otherwise it's not too bad.</p>
<p>You can also download an export of the repository, again through revision 25: <a rel="external download" href="http://media.jamesrskemp.com/download6s/NorthwindExamplesExport_rev25.zip">NorthwindExamples export</a>.</p>
<p>Note that you'll want to set either Northwind.Service or Northwind.WpfClient as the startup projects. If the former, set Northwind.SilverlightTestPage.html as the startup page.</p>
