+++
title = "Installing Eclipse 3.2 to a Windows XP SP2 machine"
description = "In this guide, we'll be installing Eclipse 3.2 on a Windows XP SP2 machine."
draft = false
comments = true
date = "2006-08-19T08:10:00-05:00"
slug = "Installing-Eclipse-32-to-a-Windows-XP-SP2-machine"
blogengine = "b7a91c08-c753-4da4-ba26-1a2f77d36f66"
categories = ["software", "tutorials / guides"]
tags = ["eclipse"]
+++

<p>
In this guide, we&#39;ll be installing Eclipse 3.2. The environment I&#39;ll be using is as follows.
</p>
<p>
HP Pavilion a620n<br />
2.20 Ghz, 960 MB (1 GB) of RAM<br />
Windows XP Home, SP2
</p>
<h4>What is Eclipse?</h4>
<p>
&ldquo;Eclipse is an open source community whose projects are focused on providing a vendor-neutral open development platform and application frameworks for building software.&rdquo; (From the Eclipse.org Web site.) In other words, Eclipse is an open source editor capable of helping you write the necessary code for a number of programming languages. Some level of support exists for Web languages like PHP and ColdFusion, but Eclipse was primarily for Java-based programming.
</p>
<h4>Why use Eclipse?</h4>
<p>
If you use Dreamweaver, Eclipse could be a good alternative to paying the high costs associated with DW. Being an open source program, the chance of another language, additional functionality, or bug-fixes being incorporated into code is higher than with the closed source DW.
</p>
<p>
Of course, Dreamweaver is a very fine product (the one I recommend if you can afford it, along with some of Adobe&#39;s other great products), so if you&#39;ve already bought Dreamweaver, don&#39;t instantly be sad and/or angry.
</p>
<h4>Downloading and Installing Eclipse</h4>
<p>
Downloading Eclipse is pretty straight-forward. Simply head over to <a href="http://www.eclipse.org/">http://www.eclipse.org/</a>, select Downloads, and download the Eclipse SDK (at this time, version 3.2). It&#39;s a fairly large download at 120 MB, but torrents are available (P2P really can be used for legit purposes). If you just download the file, you&#39;ll need to pick a mirror, so pick one close to you, if you can. Unfortunately, there&#39;s no city/state information for North America, so you&#39;ll have to work by name, intuition, or experience.
</p>
<p>
If you&#39;ve followed any of my previous guides, you know how I&#39;ve setup a directory just for my Web server downloads. I&#39;d recommend throwing this file into that folder as well, perhaps as a sub-folder, if necessary.
</p>
<p>
In order to run Eclipse, you&#39;ll also need a Java runtime environment (JRE). If you&#39;re not sure whether you have this or not, just keep an open window pointed to the Eclipse downloads page (since there&#39;s a link to download a JRE in the first paragraph) and we&#39;ll just start Eclipse to see how it functions. A readme file within the zip also details some environments that Eclipse has been known to run on.
</p>
<p>
Once the download has finished, extract the eclipse directory anywhere you&#39;d like, for now. When the extraction has completed, navigate to the eclipse.exe program, immediately within the eclipse folder. Run this program to start Eclipse.
</p>
<p>
You&#39;ll first have to select a workspace. If you&#39;ve got one area where you store your Web site folders, than point this to a subdirectory within it. For example, c:\home\ is where I store my sites, so I&#39;ll change this to c:\home\eclipse\workspace For now, I&#39;m not going to use this as my default.
</p>
<p>
If you have the necessary JRE, you should now be able to see a welcome screen. Otherwise, at some point you&#39;ve probably gotten an error message. Go back to the Eclipse downloads page and grab a JRE for your platform. Windows only has one choice (and Sun is a good choice) so go download and install the necessary JRE.
</p>
<p>
Otherwise, you&#39;re ready to start using Eclipse. Samples are available within the program, and further documentation is also available from the Eclipse.org Web site.
</p>
<h4>Next steps</h4>
<p>
You&#39;ll first want to determine where you want to run Eclipse from. I decided to create a new folder called &#39;software&#39; in my home folder and store Eclipse there. However, you can choose whatever you&#39;d like. Perhaps it makes more sense to you to put the eclipse directory in Program Files, and create the necessary shortcuts.
</p>
<p>
Next, you may want to take a look at the Web Tools Platform (WTP) project, at <a href="http://www.eclipse.org/webtools/">http://www.eclipse.org/webtools/</a>. &ldquo;The WTP project includes the following tools: source editors for HTML, Javascript, CSS, JSP, SQL, XML, DTD, XSD, and WSDL; graphical editors for XSD and WSDL; J2EE project natures, builders, and models and a J2EE navigator; a Web service wizard and explorer, and WS-I Test Tools; and database access and query tools and models.&rdquo; Definitely one of the must-haves if you&#39;ll be using Eclipse in place of, or in addition to, Dreamweaver.
</p>
<p>
To install this, you can do it straight from Eclipse using their handy Install/Update feature. Note that unlike the WTP site seems to suggest, I had to actually use the Callisto Discovery Site first, to get the files necessary to install this Platform (instead of their update site).
</p>
<p>
Select and open the Callisto Discovery Site, then open Web and J2EE Development. I only selected the Web Standard Tools (WST) Project, then hit the Select Required button (wow, why isn&#39;t this feature used more often ...). Checking this should force the download of the entire Graphical Editors and Frameworks item.
</p>
<p>
If you download this, keep in mind that it may take a very long time. A very long time. Even on my relatively fast connection, it took a handful of minutes to download all the necessary files. You may want to download the GEF directory first, then download the WST later, as time permits. If you have the time, however, go ahead and download and install it all (even though they are unsigned, you&#39;ll be fine).
</p>
<p>
Once the install has completed, you may as well just Restart, instead of simply Applying. (Again, another feature I&#39;d like to see more often.)
</p>
<p>
Now you can open an existing HTML to see just what kind of formatting you&#39;ll get. If you try dynamic languages, like ColdFusion and PHP, however, you&#39;ll see that formatting is not applied, and help text is not available. However, other projects do exist to extend how Eclipse handles these files.
</p>
<h4>Conclusion</h4>
<p>
And with that, you&#39;ve successfully installed Eclipse. Take a look at the numerous areas available from the welcome page, see just what Eclipse can do.
</p>
<p>
<a href="/local-apache-server/">View all of the steps to creating a local Web server, for development</a>.
</p>

