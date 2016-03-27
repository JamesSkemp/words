+++
title = "Extended iTunes Track class for PHP"
description = "Having created a base class in PHP for an iTunes track, here's an extended class, with sample code."
draft = false
comments = true
date = "2010-09-26T20:15:00-05:00"
modified = "2010-09-25T20:15:28-05:00"
slug = "Extended-iTunes-Track-class-for-PHP"
blogengine = "2aee5b73-ff11-49c8-8500-d922e2ad1017"
categories = ["article"]
tags = ["php", "xml", "itunes playlists to xml", "resume"]
+++

<p>In a previous article, I had outlined&nbsp;<a href="http://strivinglife.com/words/post/iTunes-Track-class-in-C-sharp-and-PHP.aspx">classes in C# and PHP to handle&nbsp;iTunes Playlists to Xml outputs</a>.</p>
<p>Having let it sit on the back burner for long enough, I finally went back to the PHP class and finalized the constructor. I also added two functions for sorting.</p>
<p>Below I have the current code for the class (a <a rel="external download" href="http://media.jamesrskemp.com/articles/Track.php.txt">current version of the Track class for PHP</a> will always be available elsewhere) and then an example implementation.</p>
<h3>Track class for PHP, version 1.0</h3>
<pre class="code"><code class="php">&lt;?php
/**
 * Music track object.
 *
 * @author James Skemp - http://jamesrskemp.com
 * @license http://creativecommons.org/licenses/by/3.0/us/
 * @version 1.0
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

	public function  __get($name) {
		return $this-&gt;$name;
	}

	public function  __set($name, $value) {
		$this-&gt;$name = $value;
	}

	/**
	 * Constructs a Track object from an iTunes Playlists to Xml XML output file.
	 *
	 * @param object $xml
	 */
	function __construct($xml) {
		$this-&gt;Name = (string)$xml-&gt;name;
		$this-&gt;Album = (string)$xml-&gt;album;
		$this-&gt;Artist = (string)$xml-&gt;artist;
		$this-&gt;Time = (string)$xml['time'];
		$this-&gt;Rating = (int)$xml-&gt;rating;
		$this-&gt;PlayCount = (int)$xml-&gt;playCount;
		$this-&gt;LastPlayed = (string)$xml-&gt;lastPlayed;
		$this-&gt;Compilation = (bool)$xml-&gt;compilation;
		$this-&gt;TrackNumber = (int)$xml-&gt;trackNumber;
		$this-&gt;TrackCount = (int)$xml-&gt;trackCount;
		$this-&gt;DiscNumber = (int)$xml-&gt;discNumber;
		$this-&gt;DiscCount = (int)$xml-&gt;discCount;
		$this-&gt;Year = (int)$xml-&gt;year;
		$this-&gt;Genre = (string)$xml-&gt;genre;
		$this-&gt;DateAdded = (string)$xml-&gt;dateAdded;
	}

	/**
	 * Function for sorting Track objects by PlayCount, ascending. Uses LastPlayed for ties.
	 *
	 * @access public
	 * @param Track $x First object to compare.
	 * @param Track $y Second object to compare.
	 * @return integer Standard sorting returns.
	 */
	public function SortPlayCountAsc($x, $y) {
		if ($x-&gt;PlayCount == $y-&gt;PlayCount) {
			if ($x-&gt;LastPlayed == $y-&gt;LastPlayed) {
				return 0;
			} else if ($x-&gt;LastPlayed &lt; $y-&gt;LastPlayed) {
				return -1;
			} else {
				return 1;
			}
		} else if ($x-&gt;PlayCount &lt; $y-&gt;PlayCount) {
			return -1;
		} else {
			return 1;
		}
	}

	/**
	 * Function for sorting Track objects by PlayCount, descending. Uses LastPlayed for ties.
	 *
	 * @access public
	 * @param Track $x First object to compare.
	 * @param Track $y Second object to compare.
	 * @return integer Standard sorting returns.
	 */
	public function SortPlayCountDesc($x, $y) {
		if ($x-&gt;PlayCount == $y-&gt;PlayCount) {
			if ($x-&gt;LastPlayed == $y-&gt;LastPlayed) {
				return 0;
			} else if ($x-&gt;LastPlayed &gt; $y-&gt;LastPlayed) {
				return -1;
			} else {
				return 1;
			}
		} else if ($x-&gt;PlayCount &lt; $y-&gt;PlayCount) {
			return 1;
		} else {
			return -1;
		}
	}
}
?&gt;</code></pre>
<h3>Usage example</h3>
<p>Update XML file location as necessary. Note also I'm using the <a rel="external" href="http://www.iis.net/download/wincacheforphp">Windows Cache Extension for PHP</a>. Modify the initial if statement accordingly if running in an environment that does not have this enabled.</p>
<pre class="code"><code class="php">&lt;?php include_once 'Track.php'; ?&gt;
&lt;!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"&gt;
&lt;html&gt;
    &lt;head&gt;
        &lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8"&gt;
        &lt;title&gt;Track class example&lt;/title&gt;
		&lt;style type="text/css"&gt;
			.error {
				color:red;
			}
		&lt;/style&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;?php
			$tracks = array();

			// Determine if we've already grabbed this for the user and either pull or populate their cache.
			if (!wincache_ucache_exists('tracksData')) {
				$xml = @simplexml_load_file('playlistXml-2010-09-25T15-26-50.xml');

				if (!$xml) {
					echo '&lt;p class="error"&gt;Could not load XML data.&lt;/p&gt;';
				} else {
					echo "Start creating array of tracks.&lt;br /&gt;";

					foreach($xml-&gt;track as $trackXml) {
						$tracks[] = new Track($trackXml);
					}
					unset($trackXml);

					echo "Finished creating array of tracks.&lt;br /&gt;";

					wincache_ucache_set('tracksData', $tracks);
				}
				unset($xml);
			} else {
				$tracks = wincache_ucache_get('tracksData');
			}

			echo "Count = ".count($tracks)."&lt;br /&gt;";

			usort($tracks, array('Track', 'SortPlayCountDesc'));

			echo "&lt;pre&gt;";
			//var_dump($tracks[2]);
			echo "&lt;/pre&gt;";

			echo "&lt;pre&gt;";
			for ($i = 0; $i &lt; 10; $i++) {
				var_dump($tracks[$i]);
			}
			unset($i);

			unset($tracks);
        ?&gt;
    &lt;/body&gt;
&lt;/html&gt;</code></pre>
<p>Memory usage seems a bit high at the end of this script, but ... at this point I'm not sure what the fix is.</p>
<p>The fact that PHP doesn't have an easy way to&nbsp;store data in an&nbsp;application cache (in memory) is rather disappointing, so other than fixing minor bugs, I don't expect I'll expand too much on this implementation.</p>
