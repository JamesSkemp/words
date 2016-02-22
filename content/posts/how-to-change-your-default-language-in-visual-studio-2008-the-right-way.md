+++
title = "How to change your default language in Visual Studio 2008 (the right way)"
summary = "There's an easy way to change your default language in Visual Studio - just update the settings file. [slnet0514:7a51d2f8-db57-4755-95f5-5042232ec3c3]"
draft = false
comments = true
date = "2008-07-02T19:40:00-05:00"
modified = "2010-02-14T12:05:41-06:00"
slug = "How-to-change-your-default-language-in-Visual-Studio-2008-the-right-way"
blogengine = "7a51d2f8-db57-4755-95f5-5042232ec3c3"
categories = ["software", "tutorials / guides"]
tags = ["microsoft", "visual studio", "c#", ".net"]
+++

<p>There's a number of resources online on how to change the default language in Visual Studio. However, none of them are correct.</p>
<p>They all state that you should reset your settings to default and then re-setup your settings. Huh?</p>
<p>Instead, if you modify the CurrentSettings.vssettings file, you can keep all your other settings, without the pain of having to re-import everything else.</p>
<p>First, find your settings file, which appears to default to the My Documents\Visual Studio <em>x</em>\Settings\ directory.</p>
<p>Open CurrentSettings.vssettings in a text or XML editor, and search for DefaultProjectLanguage.</p>
<p>You can then change the value accordingly. Here are the two options for VB or C#.</p>
<pre class="code"><code class="xml">&lt;PropertyValue name="DefaultProjectLanguage"&gt;VB&lt;/PropertyValue&gt;</code></pre>
<pre class="code"><code class="xml">&lt;PropertyValue name="DefaultProjectLanguage"&gt;CSharp&lt;/PropertyValue&gt;</code></pre>
<p>Save the file, and once you open Visual Studio, you're set.</p>
<p>Now isn't that easier?</p>
