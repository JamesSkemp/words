+++
title = "iTunes Track class in C# and PHP"
description = "An iTunes music track class written in C# and PHP."
draft = false
comments = true
date = "2010-09-08T22:25:00-05:00"
modified = "2010-09-25T20:15:43-05:00"
slug = "iTunes-Track-class-in-C-sharp-and-PHP"
blogengine = "414ad7b2-c10f-48d6-85c0-efcc2d71de55"
categories = ["article"]
tags = ["c#", "php", "itunes playlists to xml", "resume"]
+++

<p>I've recently begun reading up on PHP again. As I'm most fond of my iTunes Playlists to Xml application, I thought I'd work with that application's output - XML files with playlist data - as I continued to dig into PHP (instead of stopping now that I know enough to tweak existing code and create new functionality).</p>
<p>Here's a basic Track object in C# and PHP. I'll of course be elaborating on these as time goes by (and already have code for the C# implementation).</p>
<h3>Track class in C#</h3>
<pre class="code"><code class="csharp">/// &lt;summary&gt;
/// Music track object.
/// &lt;/summary&gt;
public class Track {
	#region Properties
	/// &lt;summary&gt;
	/// How long the track is.
	/// &lt;/summary&gt;
	public String Time { get; set; }
	/// &lt;summary&gt;
	/// Name or title of the track.
	/// &lt;/summary&gt;
	public String Name { get; set; }
	/// &lt;summary&gt;
	/// Name of the artist.
	/// &lt;/summary&gt;
	public String Artist { get; set; }
	/// &lt;summary&gt;
	/// Rating assigned to the track by the playlist's owner.
	/// &lt;/summary&gt;
	public int Rating { get; set; }
	/// &lt;summary&gt;
	/// Number of times the track has been played.
	/// &lt;/summary&gt;
	public int PlayCount { get; set; }
	/// &lt;summary&gt;
	/// Date and time the track was last played (and finished).
	/// &lt;/summary&gt;
	public DateTime LastPlayed { get; set; }
	/// &lt;summary&gt;
	/// Name of the album the track is from.
	/// &lt;/summary&gt;
	public String Album { get; set; }
	/// &lt;summary&gt;
	/// True if the album the track is on is a compilation, false otherwise.
	/// &lt;/summary&gt;
	public Boolean Compilation { get; set; }
	/// &lt;summary&gt;
	/// Order this track is on the album.
	/// &lt;/summary&gt;
	public int TrackNumber { get; set; }
	/// &lt;summary&gt;
	/// Total number of tracks on the album.
	/// &lt;/summary&gt;
	public int TrackCount { get; set; }
	/// &lt;summary&gt;
	/// The album disc the track is on.
	/// &lt;/summary&gt;
	public int DiscNumber { get; set; }
	/// &lt;summary&gt;
	/// Total number of discs in the album.
	/// &lt;/summary&gt;
	public int DiscCount { get; set; }
	/// &lt;summary&gt;
	/// Year the track/album was released/published.
	/// &lt;/summary&gt;
	public int Year { get; set; }
	/// &lt;summary&gt;
	/// Genre of music the track falls into.
	/// &lt;/summary&gt;
	public String Genre { get; set; }
	/// &lt;summary&gt;
	/// Date and time the track was added.
	/// &lt;/summary&gt;
	public DateTime DateAdded { get; set; }
	#endregion
}</code></pre>
<h3>Track class in PHP</h3>
<pre class="code"><code class="php">&lt;?php
/**
 * Music track object.
 *
 * @author James Skemp
 */
class Track {
	/**
	 * How long the track is.
	 * @var string
	 */
	var $Time;
	/**
	 * Name or title of the track.
	 * @var string
	 */
	var $Name;
	/**
	 * Name of the artist.
	 * @var string
	 */
	var $Artist;
	/**
	 * Rating assigned to the track by the playlist's owner.
	 * @var int
	 */
	var $Rating;
	/**
	 * Number of times the track has been played.
	 * @var int
	 */
	var $PlayCount;
	/**
	 * Date and time the track was last played (and finished).
	 */
	var $LastPlayed;
	/**
	 * Name of the album the track is from.
	 * @var string
	 */
	var $Album;
	/**
	 * True if the album the track is on is a compilation, false otherwise.
	 * @var bool
	 */
	var $Compilation;
	/**
	 * Order this track is on the album.
	 * @var int
	 */
	var $TrackNumber;
	/**
	 * Total number of tracks on the album.
	 * @var int
	 */
	var $TrackCount;
	/**
	 * The album disc the track is on.
	 * @var int
	 */
	var $DiscNumber;
	/**
	 * Total number of discs in the album.
	 * @var int
	 */
	var $DiscCount;
	/**
	 * Year the track/album was released/published.
	 * @var int
	 */
	var $Year;
	/**
	 * Genre of music the track falls into.
	 * @var string
	 */
	var $Genre;
	/**
	 * Date and time the track was added.
	 */
	var $DateAdded;
	
    //todo
}
?&gt;</code></pre>
<p>Comments appreciated.</p>
