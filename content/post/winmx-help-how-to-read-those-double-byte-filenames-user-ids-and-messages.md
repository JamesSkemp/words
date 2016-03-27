+++
title = "WinMX Help: How to read those Double-Byte filenames, User ID's and Messages"
description = "Guide by Byte_Bucket on how to setup WinMX to display Japanese fonts for filenames, user IDs, and messages."
draft = false
comments = false
date = "2003-08-20T00:00:00-05:00"
modified = "2007-07-14T10:59:03-05:00"
slug = "WinMX-Help-How-to-read-those-Double-Byte-filenames-User-IDs-and-Messages"
blogengine = "46edca16-14ba-42dd-a300-4fccc781cf07"
categories = ["software"]
tags = ["winmx"]
+++

<p>
This content is copyright Byte_Bucket(AT)hotmail(DOT)com.
</p>
<p>
Created:  20-Aug-2003
</p>
<blockquote>
	Revisions/Corrections to: Byte_Bucket(AT)hotmail(DOT)com<br />
	Please take your questions to Google.com and Windows online help.
</blockquote>
<p style="text-align: center">
WinMX Help
</p>
<p>
How to read those Double-Byte filenames, User ID&#39;s and Messages
</p>
<!--more-->
<hr />
<p>
PURPOSE: you are interested in, say, Japanese language titles but you can&#39;t read the file names - or user ID&#39;s for that matter.
</p>
<p>
SCOPE:  Verified only on WinXP Pro with WinMX v 3.31<br />
This works for Japanese fonts. If it does not work for other langauge fonts then follow the same approach but experiment with other fonts.
</p>
<p>
WHO IS THIS FOR:<br />
Only users who are literate in the target foreign language will find this helpful as no translation-to-english solution is described here.
</p>
<!--adsense-->
<p>
Users not literate in the target foreign language but who really want to be international about their sharing habits may take these steps and be pleasantly surprised when you discover that many (but not all) of those double-byte filenames are actually typed by the non-english user in ENGLISH/ROMAN characters but are encoded as a double-byte font. This was a surprise for me.
</p>
<p>
IGNORE/CLEAR if you MUST but REMEMBER...<br />
It seems common practice for people literate in only the english language to clear/ignore users with multi-byte characters in their user ID or in their filenames.  This is as unfortunate to the international file sharing community as it would be if the United Nations or other diplomatic circles were to choose to NOT invest in interpreters or translators.
</p>
<p>
So long as you are using &quot;Find Alternates&quot; or something similar to search for files based on the target file HASH CODE then it should always be safe (and time-saving) for an english-only user to leverage the available bandwidth of an East Asian, Eastern European or Arabic source. If I were a Japanese user looking for alternates of the same file I&#39;d sure be using this technique to leverage the available bandwidth of non-Japanese users. Of course I&#39;d also make an effort to message english users with english as best I could but that is a much longer and more prickly story to tell !
</p>
<p>
OVERVIEW:<br />
The double-byte fonts are required to encode the thousands of characters that make up such font sets as those used for various East Asian, East &amp; West European, Arabic, Hebrew and maybe some other langauges that I don&#39;t know of.  The key to making these legible is to choose the correct font on YOUR SYSTEM to view these filenames. You can only choose the correct font if you have it installed and so if you are using an English-only OS build with no special action taken to view foreign language fonts then you will first need to:
</p>
<blockquote>
	Open Regional and Language Options in Control Panel.<br />
	{use Windows help for detail instructions}
</blockquote>
<p>
In WinXP&#39;s &quot;Regional and Language Options&quot; there is a simple check box to
</p>
<blockquote>
	[ ] Install files for East Asian languages
</blockquote>
<p>
METHOD:<br />
I&#39;m going to assume that you have taken steps above to install whatever language it is you are interested in and that you can at least view that language font in some window such as Internet Explorer or even MS-Word.
</p>
<p>
Select the font in such a window as above and query the font format to see which font is being used. Chances are this is what you will want to assign from within WinMX settings dialog window. In my case this was &quot;MS UI Gothic&quot;  Note also that (within WinXP at least) there is a script box that alows you to select from among {Western, Japanese, Greek, Turkish, Baltic, central European, Cyrillic. etc.}  Be sure to select Japanese or whatever is relevant for your target language.  Don&#39;t worry the foreign language font set will still allow you to see the standard english ASCII characters - they may simply be in a less than familiar font than you are accustomed to. Often ASCII/english characters (romaji) will be spaced differently than you are accustomed to.
</p>
<p>
OK having noted this font down go to WinMX settings window and open to the Appearance page. You should find the folowing buttons at the bottom of the list of buttons:
</p>
<blockquote>
	[Change Normal Font...]<br />
	[Change Dynamic Font...]<br />
	[Change Large Font...]<br />
	[Load Language from File...] **<br />
	[Reset Language to English]<br />
	&lt;bottom of list&gt;
</blockquote>
<p>
**NOTE: Don&#39;t play with the Load Language button without first memorizing how to navigate back to the [Reset Language to English] button. You may need that when you can no longer read your WinMX menu bars and buttons!
</p>
<p>
I needed to change  Normal Font, Dynamic Font and Large Font to make filenames, user ID&#39;s, message text and window headers all legible in the target foreign (Japanese) font. For the 1280x1024 screen resolution that I use I found the following recipe:
</p>
<blockquote>
	Normal Font = Arial Unicode MS + Regular + 8pt<br />
	Dynamic Font = Arial Unicode MS + Regular + 10pt<br />
	Large Font = Arial Unicode MS + Bold + 12pt
</blockquote>
<p>
was a reasonable font set to use to view both Japanese and English filenames. In my experience for Japanese any of
</p>
<blockquote>
	MS Gothic,<br />
	MS Mincho,<br />
	MS PGothic,<br />
	MS PMincho,<br />
	MS UI Gothic,<br />
	Arial Unicode MS
</blockquote>
<p>
will work fine so long as you specify the Japanese script. Also be aware of the same named fonts preceded by the @ character. These will appear rotated 90 degrees and is not what you want in WinMX.
</p>
<p>
Just click the button and select the Font type and Script type that you noted down earlier and then close the window.
</p>
<p>
WinMX requires that you close(Exit) and restart the application before the change will take effect. Yeah a bit of a pain when you&#39;ve finally made headway in someone&#39;s queue, right!  **** Just be sure that when you close WinMX that you are truly exiting the application and not just allowing it to minimize to the Systray. **** If the latter then right click on the systray icon and click &quot;Exit&quot; and then &quot;Exit now&quot; from to truly close the WinMX application.
</p>
<p>
When WinMX restarts you&#39;ll go through the rigmarole of scanning your library and connecting to the P2P network and as you do so you will probably notice that the text in all your menu bars and buttons are now using a different (hopefully english!) font than before. If you don&#39;t like the size of the new english fonts then repeat the process above but pay attention to the font size this time. If you don&#39;t like the font (period) then try another from the set above. Be aware that size is important when it comes to squeezing the right numberof lines of text into a dialog box or an instant message window or a menu bar button. Too large a font will appear truncated. 
</p>
<p>
Test this new font in your Shared Files view if you already have files downloaded with double-byte fonts in the file names.  If you use what I have then you&#39;ll notice the Yen currency-sign is used wherever backslash woud otherwise appear in folder pathnames. If you are familiar wit the foreign laguage fonts then this will be no surprise to you. Just accept it!
</p>
<p>
So now that you&#39;ve gone through all this you can see the Japanese kanji/kana (or whatever) characters in the filenames - if you can&#39;t read the target language then you&#39;ll need help with one of the many translation web sites available. Google is always your best friend but for the Japanese language the site that I recommend is http://www.rikai.com  (read at that site for instructions in english)   Just select the file name and use whatever your favorite trick is for copying it to the clip board. (I use rename file then a Ctl-C keyboard shortcut.) Open up the rikai.com web page and paste the clipboard contents into the input window and click go or whatever and voila/naruhodo or whatever there is your same foreign font but as you hover your mouse over it then you&#39;ll see English traslations of the words that it recognizes. Hiragana and Katakana words are not always recognizable and especially propoer nouns (names) printed in Katakana cannot be interpretted - you need to learn the 50 sounds of the kana alphabet for that!
</p>
<p>
KNOWN LIMITATIONS:<br />
As best as I can tell after a day of testing, this method works for INCOMING double byte fonts for the Japanese language. So I can read User IDs, filenames, chat channel titles and topics and even user messages that have been sent using the double-byte fonts required for Japanese language. The one inbound text traffic that it _does_not_work_ for is the Chat Channel dialog which continues to be mojibake/gibberish.
</p>
<p>
Also this does not work for outbound text traffic that the user types using such tools as the IME (Input Method Emulator).
</p>
<p>
Japanese characters that you type into a message using IME appears legible while IME is active on the current text selection but once you advance to the next word or sentence the font becomes mojibake/gibberish. When sent to a Chat channel or to an individual user via the instant message tool it is seen by the recipient as mojibake/gibberish also.
</p>
<p>
If anyone reading this far has a solution for this outbound multi-byte scenario then I&#39;d appreciate being contacted at the email address at the top of this memo.
</p>
<p style="text-align: center">
---    enjoy !    ---
</p>
<p>
This content is copyright Byte_Bucket(AT)hotmail(DOT)com.
</p>
<p>
If you have any corrections for this article, please send them to <strong>Byte_Bucket(AT)hotmail(DOT)com</strong> and <strong>strivinglife[AT]gmail[DOT]com</strong> (or leave a comment below).
</p>

