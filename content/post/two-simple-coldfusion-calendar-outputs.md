+++
title = "Two simple ColdFusion calendar outputs"
description = "Two simple ways in ColdFusion to output calendars."
draft = false
comments = true
date = "2009-10-26T21:28:00-05:00"
modified = "2009-12-21T09:51:19-06:00"
slug = "Two-simple-ColdFusion-calendar-outputs"
blogengine = "f7f2f42d-6a8c-42ec-b55f-eb552552c5bf"
categories = ["article"]
tags = ["coldfusion", "css"]
+++

<p>Here's&nbsp;two rough drafts of calendars created via ColdFusion (7, but I believe 6.1 would have the same functionality).</p>
<h3>Tables-based</h3>
<pre class="code"><code class="html">&lt;cfparam name="URL.CalendarMonth" default="#Month(now())#" type="integer" /&gt;
&lt;cfparam name="URL.CalendarYear" default="#Year(now())#" type="integer" /&gt;

&lt;cfif URL.CalendarMonth LT 1 OR URL.CalendarMonth GT 12&gt;
	&lt;cfset URL.CalendarMonth = Month(now()) /&gt;
&lt;/cfif&gt;

&lt;cfset VARIABLES.Calendar.StartDate = CreateDate(URL.CalendarYear, URL.CalendarMonth, 1) /&gt;

&lt;table style="width:375px;" summary="Calendar of events for &lt;cfoutput&gt;#DateFormat(VARIABLES.Calendar.StartDate, 'mmmm yyyy')#&lt;/cfoutput&gt;."&gt;
	&lt;thead&gt;
		&lt;tr&gt;
			&lt;th colspan="7"&gt;&lt;cfoutput&gt;#DateFormat(VARIABLES.Calendar.StartDate, "mmmm yyyy")#&lt;/cfoutput&gt;&lt;/th&gt;
		&lt;/tr&gt;
		&lt;tr&gt;
			&lt;th&gt;S&lt;/th&gt;
			&lt;th&gt;M&lt;/th&gt;
			&lt;th&gt;T&lt;/th&gt;
			&lt;th&gt;W&lt;/th&gt;
			&lt;th&gt;Th&lt;/th&gt;
			&lt;th&gt;F&lt;/th&gt;
			&lt;th&gt;S&lt;/th&gt;
		&lt;/tr&gt;
	&lt;/thead&gt;
	&lt;tbody&gt;
		&lt;cfloop from="1" to="#DaysInMonth(VARIABLES.Calendar.StartDate)#" index="iDay"&gt;
			&lt;cfset VARIABLES.Calendar.CurrentDate = CreateDate(URL.CalendarYear, URL.CalendarMonth, iDay) /&gt;
			&lt;cfif DayOfWeek(VARIABLES.Calendar.CurrentDate) EQ 1 OR iDay EQ 1&gt;&lt;!--- This is Sunday, or the first day. ---&gt;
				&lt;tr&gt;
			&lt;/cfif&gt;
			&lt;cfif iDay EQ 1&gt;&lt;!--- If it's the first day, determine how many empty cells we need. ---&gt;
				&lt;cfoutput&gt;#RepeatString("&lt;td&gt;&lt;/td&gt;", DayOfWeek(VARIABLES.Calendar.StartDate) - 1)#&lt;/cfoutput&gt;
			&lt;/cfif&gt;
				&lt;cfoutput&gt;&lt;td&gt;&lt;span title="#DateFormat(VARIABLES.Calendar.CurrentDate, 'mmmm d, yyyy')#"&gt;#iDay#&lt;/span&gt;&lt;/td&gt;&lt;/cfoutput&gt;
			&lt;cfif iDay EQ DaysInMonth(VARIABLES.Calendar.StartDate)&gt;
				&lt;cfoutput&gt;#RepeatString("&lt;td&gt;&lt;/td&gt;", 7 - DayOfWeek(VARIABLES.Calendar.CurrentDate))#&lt;/cfoutput&gt;
			&lt;/cfif&gt;
			&lt;cfif DayOfWeek(VARIABLES.Calendar.CurrentDate) EQ 7 OR iDay EQ DaysInMonth(VARIABLES.Calendar.StartDate)&gt;&lt;!--- This is Saturday, or the last day. ---&gt;
				&lt;/tr&gt;
			&lt;/cfif&gt;
		&lt;/cfloop&gt;
	&lt;/tbody&gt;
&lt;/table&gt;</code></pre>
<h3>Ordered list and CSS</h3>
<p>The following is a rough version of an ordered list and CSS-based calendar.</p>
<pre class="code"><code class="html">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" /&gt;
&lt;title&gt;&lt;/title&gt;
	&lt;style type="text/css"&gt;
	.olCalendar {
		width:375px;
	}
	.olCalendar ol li {
		display:block;
		float:left;
		list-style-position:inside;
		margin:0;
		width:45px;
	}
	.olCalendar li.noDate {
		list-style-image:none;
	}
	&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;cfparam name="URL.CalendarMonth" default="#Month(now())#" type="integer" /&gt;
&lt;cfparam name="URL.CalendarYear" default="#Year(now())#" type="integer" /&gt;

&lt;cfif URL.CalendarMonth LT 1 OR URL.CalendarMonth GT 12&gt;
	&lt;cfset URL.CalendarMonth = Month(now()) /&gt;
&lt;/cfif&gt;

&lt;cfset VARIABLES.Calendar.StartDate = CreateDate(URL.CalendarYear, URL.CalendarMonth, 1) /&gt;
&lt;div class="olCalendar"&gt;
	&lt;ol start="&lt;cfoutput&gt;#2 - DayOfWeek(VARIABLES.Calendar.StartDate)#&lt;/cfoutput&gt;"&gt;
		&lt;cfloop from="1" to="#DaysInMonth(VARIABLES.Calendar.StartDate)#" index="iDay"&gt;
			&lt;cfset VARIABLES.Calendar.CurrentDate = CreateDate(URL.CalendarYear, URL.CalendarMonth, iDay) /&gt;
			&lt;cfif iDay EQ 1&gt;&lt;!--- If it's the first day, determine how many empty cells we need. ---&gt;
				&lt;cfoutput&gt;#RepeatString('&lt;li class="noDate"&gt;&nbsp;&lt;/li&gt;', DayOfWeek(VARIABLES.Calendar.StartDate) - 1)#&lt;/cfoutput&gt;
			&lt;/cfif&gt;
				&lt;cfoutput&gt;&lt;li class="#LCase(DayOfWeekAsString(DayOfWeek(VARIABLES.Calendar.CurrentDate)))#"&gt;&lt;span title="#DateFormat(VARIABLES.Calendar.CurrentDate, 'mmmm d, yyyy')#"&gt;#iDay#&lt;/span&gt;&lt;/li&gt;&lt;/cfoutput&gt;
			&lt;cfif iDay EQ DaysInMonth(VARIABLES.Calendar.StartDate)&gt;
				&lt;cfoutput&gt;#RepeatString('&lt;li class="noDate"&gt;&nbsp;&lt;/li&gt;', 7 - DayOfWeek(VARIABLES.Calendar.CurrentDate))#&lt;/cfoutput&gt;
			&lt;/cfif&gt;
		&lt;/cfloop&gt;
	&lt;/ol&gt;
&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;</code></pre>
<p>But, let's be honest, this version sucks. I think tables are a necessary evil in this regard.</p>
<p><strong>EDIT 12/21/2009</strong>: Corrected StartDate/CurrentDate mistake with repeating td elements.</p>
