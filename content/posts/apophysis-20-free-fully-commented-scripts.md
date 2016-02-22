+++
title = "Apophysis 2.0: Free Fully Commented Scripts"
summary = "A selection of free scripts for Apophysis 2.0.  Fully commented so that users can learn from them."
draft = false
comments = false
date = "2004-12-16T00:00:00-06:00"
modified = "2007-07-04T15:05:32-05:00"
slug = "Apophysis-20-Free-Fully-Commented-Scripts"
blogengine = "90661094-2bb4-48b2-80dc-e342883266f9"
categories = ["article", "software"]
tags = []
+++

<p>
I offer the following, fully commented, scripts for use by the Apophysis (2.0) community. Feel free to copy the following scripts into the script editor for Apophysis 2.0 or download the script files from http://strivinglife.net/. Feel free to save the scripts on your own computers, but please do not share these scripts with others; rather, direct them to this article so they can be aware of my other scripts and any enhancements I release. Comments regarding these scripts are welcomed with open arms.<!--more--> Thanks, and enjoy J<!--adsense-->
</p>
<p>
Please note that these scripts all assume that you have a folder on your C drive called &lsquo;renders&rsquo;. If you do not, either change this directory in the scripts, or create a directory by this name in that location.
</p>
<p>
Full listing of available scripts:
</p>
<ol>
	<li><a href="/files/2004/ModBatchRen.zip">Modified Batch Render</a> (ModBatchRen.asc) &ndash; 3 KB</li>
	<li><a href="/files/2004/PreviewSweep1.zip">Preview Sweep - using &lsquo;for&rsquo;</a> &ndash; 1 KB</li>
	<li><a href="/files/2004/PreviewSweep2.zip">Preview Sweep - using &lsquo;repeat&rsquo;</a> &ndash; 1 KB</li>
	<li><a href="/files/2004/RenSingle.zip">Render Single Flame</a> (RenSingle.asc) &ndash; 2 KB</li>
</ol>
<p>
&nbsp;
</p>
<hr />
<h4>Modified Batch Render (download name: ModBatchRen.asc)</h4>
<blockquote>
	<p>
	{Modified Batch Render &ndash; Apophysis 2.0}<br />
	{Renders selected flames in the<br />
	&nbsp;current parameter file to disk.<br />
	&nbsp;Set the render settings to taste}<br />
	{http://jamesrskemp.net/} <br />
	p := 1; {sets primary number to 1}<br />
	f := FileCount; {sets final number to the file count}<br />
	Renderer.Width := 1280; {sets render width &ndash; change to taste}<br />
	Renderer.Height := 960; {sets render height &ndash; change to taste}<br />
	InputQuery(&#39;First Flame to render&#39;, &#39;Actual Position:&#39;, p);<br />
	&nbsp;{Prompts for the first flame to render &ndash; defaults to the very<br />
	&nbsp; first flame, set by p above} <br />
	InputQuery(&#39;Last Flame to render&#39;, &#39;Actual Position (default is last):&#39;, f);<br />
	&nbsp;{Prompts for last flame to render &ndash; defaults to the very last<br />
	&nbsp; flame, set by f above} <br />
	Print(&#39;Input done&#39;); {Prints to the editor window that values have been entered}<br />
	p := p - 1; {Since the first flame is really 0, not 1, you have to subtract one from the initial value}<br />
	f := f - 1; {You also have to subtract one from the final value}<br />
	Print(&#39;First actual: &#39;);<br />
	Print(p); {Outputs the actual position number for the first flame}<br />
	Print(&#39; and last actual: &#39;);<br />
	Print(f); {Outputs the actual position number for the last flame}<br />
	for i := p to f do { from the first to the last flame...}<br />
	begin {begin the following until the &lsquo;end&rsquo;}<br />
	&nbsp; LoadFlame(i); {load flame}<br />
	&nbsp; n := i+1 {add one to current flame position value}<br />
	&nbsp; Print(&#39;Loaded flame in position #&#39;);<br />
	&nbsp; Print(n); {Output this value so that the user knows what flame is rendering}<br />
	&nbsp; Flame.SampleDensity := 100; {best 200 - flame sample density &ndash; <strong>change to taste</strong>}<br />
	&nbsp; Flame.Oversample := 1; {best 2 - flame oversample &ndash; <strong>change to taste</strong>}<br />
	&nbsp; Flame.FilterRadius := 0.2; {best 0.4 - flame filter radius &ndash; <strong>change to taste</strong>}<br />
	&nbsp; Renderer.Filename :=&#39;C:\renders\&#39; + Flame.Name + &#39;.jpg&#39;; {render flame to this directory, in jpg format &ndash; <strong>change to taste</strong>}<br />
	&nbsp; SetRenderBounds; {sets render bounds}<br />
	&nbsp; Render; {renders the flame}<br />
	&nbsp; Print(&#39;Rendered flame #&#39;);<br />
	&nbsp; Print(n); {output that the flame has been rendered}<br />
	end; {end the for loop &ndash; if the &lsquo;for&rsquo; is not done, go back to &lsquo;begin&rsquo; and continue &ndash; automatically adds one to the &lsquo;i&rsquo; value}<br />
	UpdateFlame := False; {don&rsquo;t update the flame in the Apophysis window}
	</p>
</blockquote>
<p>
Sample output for entered values of &lsquo;1&rsquo; &amp; &lsquo;1&rsquo;
</p>
<p>
Input done<br />
First actual: <br />
0<br />
&nbsp;and last actual: <br />
0<br />
Loaded flame in position #<br />
1<br />
Rendered flame #<br />
1
</p>
<p>
Please note that you must have the script editor open in order to see the outputs.&nbsp; However, you can open the editor at any time (Ctrl + D) to check the progress of the script.
</p>
<hr />
<h4><u>Preview Sweep</u> &ndash; using &lsquo;for&rsquo; (download name: PreviewSweep1.asc)</h4>
<blockquote>
	<p>
	{Preview Sweep - Apophysis 2.0}<br />
	{Preview Flames, with information regarding the number down}<br />
	{http://jamesrskemp.net/} <br />
	UpdateFlame := false; {don&#39;t update the main display}<br />
	b := 0; {starting value &ndash; <strong>change if you&rsquo;d like</strong>}<br />
	e := FileCount - 1; {ending value - &#39;FileCount - 1&#39; (no quotes) for all - run as is to text SampleDensity &ndash; <strong>change after determining best sample density</strong>}<br />
	for i := b to e do {from b to e, do the following}<br />
	begin {begin &#39;for&#39; loop}<br />
	if Stopped then Break; {if the Stop button is pushed, stop the preview}<br />
	LoadFlame(i); {load flame}<br />
	Flame.SampleDensity := 30; {change this value to allow the image to have time to preview on your computer}<br />
	<strong>{increase on faster machines, decrease on slower ones}</strong><br />
	if (Transforms &gt; 1) then<br />
	Preview;<br />
	else<br />
	Print(&#39;Bad flame&#39;); {since only flames with more than one transform can be rendered, this checks for that}<br />
	print(i); {Print flame number from top - prints after showing the flame}<br />
	end; {end &#39;for&#39; loop - go back to the &#39;begin&#39; if the &#39;for&#39; is not done}
	</p>
</blockquote>
<p>
See also Preview Sweep &ndash; using &lsquo;repeat&rsquo; for an alternative method.
</p>
<hr />
<h4><u>Preview Sweep &ndash; using &lsquo;repeat&rsquo;</u> (download name: PreviewSweep2.asc)</h4>
<blockquote>
	<p>
	{Preview Sweep - Apophysis 2.0}<br />
	{Preview Flames, with information regarding the number down}<br />
	{http://jamesrskemp.net/} <br />
	UpdateFlame := false; {don&#39;t update the main display}<br />
	b := 0; {starting value &ndash; <strong>change if you&rsquo;d like</strong>}<br />
	e := FileCount - 1; {ending value - &#39;FileCount - 1&#39; (no quotes) for all - run as is to test SampleDensity &ndash; <strong>change after setting sample density to taste</strong>}<br />
	repeat {repeat the following until the below conditions are met}<br />
	LoadFlame(b); {load flame}<br />
	Flame.SampleDensity := 30; {change this value to allow the image to have time to preview on your computer}<br />
	<strong>{increase on faster machines, decrease on slower ones}</strong><br />
	if (Transforms &gt; 1) then<br />
	Preview;<br />
	else<br />
	Print(&#39;Bad flame&#39;); {since only flames with more than one transform can be rendered, this checks for that}<br />
	Print(b); {Print flame number from top - prints after showing the flame}<br />
	b := b + 1; {increase flame value by one}<br />
	until (b &gt;= e) or Stopped; {continue until the end value is reached}
	</p>
</blockquote>
<p>
See also Preview Sweep &ndash; using &lsquo;for&rsquo; for an alternative method.
</p>
<hr />
<h4><u>Render Single Flame</u> (download name: RenSingle.asc)</h4>
<blockquote>
	<p>
	{Render Single Flame - Apophysis 2.0}<br />
	{Renders single flame in the current parameter file to disk.}<br />
	{http://jamesrskemp.net/} <br />
	InputQuery(&#39;Input flame to render&#39;,&#39;Flame number to render (actual position):&#39;,f) {Prompt for flame to render where first flame = 1}<br />
	i := f-1; {Set value for flame to render, first = 0, last = total flames - 1}<br />
	Renderer.Width := 1280; {Set render width &ndash; <strong>change value to taste</strong>}<br />
	Renderer.Height := 960; {Set render height &ndash; <strong>change value to taste</strong>}<br />
	LoadFlame(i); {Load flame}<br />
	Flame.SampleDensity := 200; {best 200 - flame sample density &ndash; <strong>change to taste</strong>}<br />
	Flame.Oversample := 2; {best 2 - flame oversample &ndash; <strong>change to taste</strong>}<br />
	Flame.FilterRadius := 0.4; {best 0.4 - flame filter radius &ndash; <strong>change to taste</strong>}<br />
	SaveFlame(&#39;C:\renders\&#39; + &#39;singlerenders.flame&#39;); {save the flame parameters to this file &ndash; <strong>change to taste</strong>}<br />
	Renderer.Filename :=&#39;C:\renders\&#39; + Flame.Name + &#39;.jpg&#39;; {render flame to this directory, with &lsquo;jpg&rsquo; extension &ndash; <strong>change to taste</strong>}<br />
	SetRenderBounds;<br />
	Render; {set render bounds and render the image}<br />
	UpdateFlame := False; {don&rsquo;t update the flame when done}
	</p>
</blockquote>
<hr />
<p>
<strong>Created:</strong> February 13th 2004
</p>
<p>
<strong>Modified:</strong> March 9th 2004; March 12th 2004; September 13th 2004; November 25th 2004; December 16th 2004
</p>
<p>
<strong>Notes:</strong> Some of these scripts were originally developed during the beta stages of Apophysis 2.0, but they have all been run successfully on the final release and on 2.02 (the version current as of this update).
</p>

