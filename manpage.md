# get_iplayer Manual

# Table of Contents

* [NAME](#name)

* [SYNOPSIS](#synopsis)

* [DESCRIPTION](#description)

* [OPTIONS](#options)

    * [Search Options](#search-options)

    * [Display Options](#display-options)

    * [Recording Options](#recording-options)

    * [Output Options](#output-options)

    * [PVR Options](#pvr-options)

    * [Config Options](#config-options)

    * [External Program Options](#external-program-options)

    * [Tagging Options](#tagging-options)

* [AUTHOR](#author)

* [COPYRIGHT NOTICE](#copyright-notice)

<a id="name"></a>

# NAME

get_iplayer - Stream Recording tool and PVR for BBC iPlayer, BBC Podcasts and more

<a id="synopsis"></a>

# SYNOPSIS

get_iplayer [&lt;options&gt;] [&lt;regex|index&gt; ...]

get_iplayer --get [&lt;options&gt;] &lt;regex|index&gt; ...

get_iplayer &lt;url&gt; --type=&lt;type&gt; [&lt;options&gt;]

get_iplayer &lt;pid|url&gt; [--type=&lt;type&gt; &lt;options&gt;]

get_iplayer --stream [&lt;options&gt;] &lt;regex|index&gt; | mplayer -cache 3072 -

get_iplayer --stream [&lt;options&gt;] --type=&lt;type&gt; &lt;pid|url&gt; | mplayer -cache 3072 -

get_iplayer --stream [&lt;options&gt;] --type=livetv,liveradio &lt;regex|index&gt; --player=&quot;mplayer -cache 128 -&quot;

get_iplayer --refresh

<a id="description"></a>

# DESCRIPTION

get_iplayer lists, searches and records BBC iPlayer TV/Radio, BBC Podcast programmes. Other 3rd-Party plugins may be available.

get_iplayer has three modes: recording a complete programme for later playback, streaming a programme
directly to a playback application, such as mplayer; and as a Personal Video Recorder (PVR), subscribing to
search terms and recording programmes automatically. It can also stream or record live BBC iPlayer output

If given no arguments, get_iplayer updates and displays the list of currently available programmes.
Each available programme has a numerical identifier, pid.
get_iplayer utilises the rtmpdump tool to record BBC iPlayer programmes from RTMP flash streams at various qualities.

In PVR mode, get_iplayer can be called from cron to record programmes to a schedule.

<a id="options"></a>

# OPTIONS


<a id="search-options"></a>

## Search Options


**--before**
: Limit search to programmes added to the cache before N hours ago

**--category &lt;string&gt;**
: Narrow search to matched categories (regex or comma separated values)

**--channel &lt;string&gt;**
: Narrow search to matched channel(s) (regex or comma separated values)

**--exclude &lt;string&gt;**
: Narrow search to exclude matched programme names (regex or comma separated values)

**--exclude-category &lt;string&gt;**
: Narrow search to exclude matched categories (regex or comma separated values)

**--exclude-channel &lt;string&gt;**
: Narrow search to exclude matched channel(s) (regex or comma separated values)

**--fields &lt;field1&gt;,&lt;field2&gt;,..**
: Searches only in the specified comma separated fields

**--future**
: Search future programme schedule if it has been indexed (refresh cache with: --refresh --refresh-future).

**--history**
: Search/show recordings history

**--long, -l**
: Additionally search in programme descriptions and episode names (same as --fields=name,episode,desc )

**--search &lt;search term&gt;**
: GetOpt compliant way of specifying search args

**--since**
: Limit search to programmes added to the cache in the last N hours

**--type &lt;type&gt;**
: Only search in these types of programmes: livetv,tv,liveradio,radio,all (tv is default)

**--versions &lt;versions&gt;**
: Version of programme to search or record.  List is processed from left to right and first version found is downloaded.  Example: &#39;--versions signed,audiodescribed,default&#39; will prefer signed and audiodescribed programmes if available.  Default: &#39;default&#39;

<a id="display-options"></a>

## Display Options


**--conditions**
: Shows GPLv3 conditions

**--debug**
: Debug output

**--dump-options**
: Dumps all options with their internal option key names

**--help, -h**
: Intermediate help text

**--helpbasic, --usage**
: Basic help text

**--helplong**
: Advanced help text

**--hide**
: Hide previously recorded programmes

**--info, -i**
: Show full programme metadata and availability of modes and subtitles (max 50 matches)

**--list &lt;categories|channel&gt;**
: Show a list of available categories/channels for the selected type and exit

**--listformat &lt;format&gt;**
: Display programme data based on a user-defined format string (such as &lt;pid&gt;, &lt;name&gt; etc)

**--listplugins**
: Display a list of currently available plugins or programme types

**--long, -l**
: Show long programme info

**--manpage &lt;file&gt;**
: Create man page based on current help text

**--nocopyright**
: Don&#39;t display copyright header

**--page &lt;number&gt;**
: Page number to display for multipage output

**--pagesize &lt;number&gt;**
: Number of matches displayed on a page for multipage output

**--quiet, -q**
: No logging output

**--series**
: Display Programme series names only with number of episodes

**--show-cache-age**
: Displays the age of the selected programme caches then exit

**--show-options**
: Shows options which are set and where they are defined

**--sort &lt;fieldname&gt;**
: Field to use to sort displayed matches

**--sortreverse**
: Reverse order of sorted matches

**--streaminfo**
: Returns all of the media stream urls of the programme(s)

**--terse**
: Only show terse programme info (does not affect searching)

**--tree**
: Display Programme listings in a tree view

**--verbose, -v**
: Verbose

**--warranty**
: Displays warranty section of GPLv3

**-V**
: Show get_iplayer version and exit.

<a id="recording-options"></a>

## Recording Options


**--aactomp3**
: Transcode AAC audio to MP3 with ffmpeg (CBR 128k unless --mp3vbr is specified)

**--attempts &lt;number&gt;**
: Number of attempts to make or resume a failed connection

**--bandwidth**
: In radio realaudio mode specify the link bandwidth in bps for rtsp streaming (default 512000)

**--force**
: Ignore programme history (unsets --hide option also). Forces a script update if used with -u

**--get, -g**
: Start recording matching programmes. Search terms required unless --pid specified. Use  --search=.* to force download of all available programmes.

**--hash**
: Show recording progress as hashes

**--liveradiomode &lt;mode&gt;,&lt;mode&gt;,..**
: Live Radio Recording modes: flashaac,realaudio,wma. Use --liveradiomode=best to automatically select highest quality available.

**--livetvmode &lt;mode&gt;,&lt;mode&gt;,...**
: Live TV Recoding modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal (default: flashhd,flashvhigh,flashhigh,flashstd,flashnormal). Use --livetvmode=best to automatically select highest quality available.

**--metadata-only**
: Create specified metadata info file without any recording or streaming (can also be used with thumbnail option).

**--mmsnothread**
: Disable parallel threaded recording for mms

**--modes &lt;mode&gt;,&lt;mode&gt;,...**
: Recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow,n95_wifi,flashaac,flashaachigh,flashaacstd,flashaaclow,flashaudio,realaudio,wma.  Use --modes=best to automatically select highest quality available.

**--mp3vbr**
: Set LAME VBR mode to N (0 to 9) for AAC transcoding. 0 = target bitrate 245 Kbit/s, 9 = target bitrate 65 Kbit/s (requires --aactomp3)

**--multimode**
: Allow the recording of more than one mode for the same programme - WARNING: will record all specified/default modes!!

**--overwrite**
: Overwrite recordings if they already exist

**--partial-proxy**
: Only uses web proxy where absolutely required (try this extra option if your proxy fails)

**--pid &lt;pid&gt;**
: Record an arbitrary pid that does not necessarily appear in the index.

**--pid-recursive**
: When used with --pid record all the embedded pids if the pid is a series or brand pid.

**--proxy, -p &lt;url&gt;**
: Web proxy URL e.g. &#39;http://USERNAME:PASSWORD@SERVER:PORT&#39; or &#39;http://SERVER:PORT&#39;

**--radiomode &lt;mode&gt;,&lt;mode&gt;,...**
: Radio Recording mode(s): flashaac,flashaachigh,flashaacstd,flashaaclow,flashaudio,realaudio,wma (default: flashaachigh,flashaacstd,flashaudio,realaudio,flashaaclow). Use --radiomode=best to automatically select highest quality available.

**--raw**
: Don&#39;t transcode or change the recording/stream in any way (i.e. radio/realaudio, rtmp/flv)

**--rtmp-liveradio-opts &lt;options&gt;**
: Add custom options to flvstreamer for liveradio

**--rtmp-livetv-opts &lt;options&gt;**
: Add custom options to flvstreamer for livetv

**--rtmp-radio-opts &lt;options&gt;**
: Add custom options to flvstreamer for radio

**--rtmp-tv-opts &lt;options&gt;**
: Add custom options to flvstreamer for tv

**--rtmpport &lt;port&gt;**
: Override the RTMP port (e.g. 443)

**--start &lt;secs&gt;**
: Recording/streaming start offset (rtmp and realaudio only)

**--stop &lt;secs&gt;**
: Recording/streaming stop offset (can be used to limit live rtmp recording length) rtmp and realaudio only

**--suboffset &lt;offset&gt;**
: Offset the subtitle timestamps by the specified number of milliseconds

**--subsraw**
: Additionally save the raw subtitles file

**--subtitles**
: Download subtitles into srt/SubRip format if available and supported

**--subtitles-only**
: Only download the subtitles, not the programme

**--tag-only**
: Only update the programme tag and not download the programme (can also be used with --history)

**--test, -t**
: Test only - no recording (will show programme type)

**--thumb**
: Download Thumbnail image if available

**--thumbnail-only**
: Only Download Thumbnail image if available, not the programme

**--tvmode &lt;mode&gt;,&lt;mode&gt;,...**
: TV Recoding modes: rtmp,flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow,n95_wifi (default: flashhigh,flashstd,flashnormal). Use --tvmode=best to automatically select highest quality available.

**--url &quot;&lt;url&gt;&quot;**
: Record the embedded media player in the specified URL. Use with --type=&lt;type&gt;.

**--wav**
: In radio realaudio mode output as wav and don&#39;t transcode to mp3

<a id="output-options"></a>

## Output Options


**--command, -c &lt;command&gt;**
: Run user command after successful recording using args such as &lt;pid&gt;, &lt;name&gt; etc

**--email &lt;address&gt;**
: Email HTML index of matching programmes to specified address

**--email-sender &lt;address&gt;**
: Optional email sender address

**--email-smtp &lt;hostname&gt;**
: SMTP server IP address to use to send email (default: localhost)

**--fatfilename**
: Omit characters forbidden by FAT filesystems from filenames but keep whitespace

**--file-prefix &lt;format&gt;**
: The filename prefix (excluding dir and extension) using formatting fields. e.g. &#39;&lt;name&gt;-&lt;episode&gt;-&lt;pid&gt;&#39;

**--fxd &lt;file&gt;**
: Create Freevo FXD XML of matching programmes in specified file

**--html &lt;file&gt;**
: Create basic HTML index of matching programmes in specified file

**--isodate**
: Use ISO8601 dates (YYYY-MM-DD) in filenames

**--metadata &lt;type&gt;**
: Create metadata info file after recording. Valid types are: xbmc, xbmc_movie, freevo, generic

**--mkv**
: Output video in MKV container instead of MP4. Currently no tagging supported from get_iplayer for MKV output

**--mythtv &lt;file&gt;**
: Create Mythtv streams XML of matching programmes in specified file

**--nowrite, -n**
: No writing of file to disk (use with -x to prevent a copy being stored on disk)

**--output, -o &lt;dir&gt;**
: Recording output directory

**--outputliveradio &lt;dir&gt;**
: Output directory for live radio recordings

**--outputlivetv &lt;dir&gt;**
: Output directory for live tv recordings

**--outputlocalfiles &lt;dir&gt;**
: Output directory for localfiles recordings

**--outputpodcast &lt;dir&gt;**
: Output directory for podcast recordings

**--outputradio &lt;dir&gt;**
: Output directory for radio recordings

**--outputtv &lt;dir&gt;**
: Output directory for tv recordings

**--player &#39;&lt;command&gt; &lt;options&gt;&#39;**
: Use specified command to directly play the stream

**--stdout, -x**
: Additionally stream to STDOUT (so you can pipe output to a player)

**--stream**
: Stream to STDOUT (so you can pipe output to a player)

**--subdir, -s**
: Put Recorded files into Programme name subdirectory

**--subdir-format &lt;format&gt;**
: The format to be used for the subdirectory naming using formatting fields. e.g. &#39;&lt;nameshort&gt;-&lt;seriesnum&gt;&#39;

**--symlink &lt;file&gt;**
: Create symlink to &lt;file&gt; once we have the header of the recording

**--thumb-ext &lt;ext&gt;**
: Thumbnail filename extension to use

**--thumbsize &lt;index|width&gt;**
: Default thumbnail size/index to use for the current recording and metadata (see --info for thumbnailN: to get size/index)

**--thumbsizecache &lt;index|width&gt;**
: Default thumbnail size/index to use when building cache and index (see --info for thumbnailN: to get size/index)

**--whitespace, -w**
: Keep whitespace (and escape chars) in filenames

**--xml-alpha**
: Create freevo/Mythtv menu sorted alphabetically by programme name

**--xml-channels**
: Create freevo/Mythtv menu of channels -&gt; programme names -&gt; episodes

**--xml-names**
: Create freevo/Mythtv menu of programme names -&gt; episodes

<a id="pvr-options"></a>

## PVR Options


**--comment &lt;string&gt;**
: Adds a comment to a PVR search

**--pvr [pvr search name]**
: Runs the PVR using all saved PVR searches (intended to be run every hour from cron etc). The list can be limited by adding a regex to the command. Synonyms: --pvrrun, --pvr-run

**--pvr-add &lt;search name&gt;**
: Save the named PVR search with the specified search terms.  Search terms required. Use --search=.* to force download of all available programmes. Synonyms: --pvradd

**--pvr-del &lt;search name&gt;**
: Remove the named search from the PVR searches. Synonyms: --pvrdel

**--pvr-disable &lt;search name&gt;**
: Disable (not delete) a named PVR search. Synonyms: --pvrdisable

**--pvr-enable &lt;search name&gt;**
: Enable a previously disabled named PVR search. Synonyms: --pvrenable

**--pvr-exclude &lt;string&gt;**
: Exclude the PVR searches to run by search name (regex or comma separated values). Synonyms: --pvrexclude

**--pvr-list**
: Show the PVR search list. Synonyms: --pvrlist

**--pvr-queue**
: Add currently matched programmes to queue for later one-off recording using the --pvr option. Search terms required unless --pid specified. Use --search=.* to force download of all available programmes. Synonyms: --pvrqueue

**--pvr-scheduler &lt;seconds&gt;**
: Runs the PVR using all saved PVR searches every &lt;seconds&gt;. Synonyms: --pvrscheduler

**--pvr-single &lt;search name&gt;**
: Runs a named PVR search. Synonyms: --pvrsingle

<a id="config-options"></a>

## Config Options


**--expiry, -e &lt;secs&gt;**
: Cache expiry in seconds (default 4hrs)

**--limit-matches &lt;number&gt;**
: Limits the number of matching results for any search (and for every PVR search)

**--localfilesdirs &lt;dir&gt;[,dir,]**
: Directories/Folders to scan for new files

**--nopurge**
: Don&#39;t ask to delete programmes recorded over 30 days ago

**--packagemanager &lt;string&gt;**
: Tell the updater that we were installed using a package manager and don&#39;t update (use either: apt,rpm,deb,yum,disable)

**--plugins-update**
: Update get_iplayer plugins to the latest

**--prefs-add**
: Add/Change specified saved user or preset options

**--prefs-clear**
: Remove *ALL* saved user or preset options

**--prefs-del**
: Remove specified saved user or preset options

**--prefs-show**
: Show saved user or preset options

**--preset, -z &lt;name&gt;**
: Use specified user options preset

**--preset-list**
: Show all valid presets

**--profile-dir &lt;dir&gt;**
: Override the user profile directory/folder

**--refresh, --flush, -f**
: Refresh cache

**--refresh-exclude &lt;string&gt;**
: Exclude matched channel(s) when refreshing cache (regex or comma separated values)

**--refresh-future**
: Obtain future programme schedule when refreshing cache (between 7-14 days)

**--refresh-include &lt;string&gt;**
: Include matched channel(s) when refreshing cache (regex or comma separated values)

**--skipdeleted**
: Skip the download of metadata/thumbs/subs if the media file no longer exists. Use with --history &amp; --metadataonly/subsonly/thumbonly.

**--update, -u**
: Update get_iplayer if a newer one exists

**--webrequest &lt;urlencoded string&gt;**
: Specify all options as a urlencoded string of &quot;name=val&amp;name=val&amp;...&quot;

<a id="external-program-options"></a>

## External Program Options


**--atomicparsley &lt;path&gt;**
: Location of AtomicParsley tagger binary

**--ffmpeg &lt;path&gt;**
: Location of ffmpeg binary

**--flvstreamer &lt;path&gt;**
: Location of flvstreamer binary

**--id3v2 &lt;path&gt;**
: Location of id3v2 or id3tag binary

**--lame &lt;path&gt;**
: Location of lame binary

**--mplayer &lt;path&gt;**
: Location of mplayer binary

**--vlc &lt;path&gt;**
: Location of vlc or cvlc binary

<a id="tagging-options"></a>

## Tagging Options


**--no-tag**
: Do not tag downloaded programmes

**--tag-cnid**
: AtomicParsley supports --cnID argument to add catalog ID used for combining HD and SD versions in iTunes

**--tag-fulltitle**
: Use complete title (including series) instead of shorter episode title

**--tag-hdvideo**
: AtomicParsley supports --hdvideo argument for HD video flag

**--tag-longdesc**
: AtomicParsley supports --longdesc argument for long description text

**--tag-longdescription**
: AtomicParsley supports --longDescription argument for long description text

**--tag-podcast**
: Tag downloaded radio and tv programmes as iTunes podcasts (requires MP3::Tag module for AAC/MP3 files)

**--tag-podcast-radio**
: Tag only downloaded radio programmes as iTunes podcasts (requires MP3::Tag module for AAC/MP3 files)

**--tag-podcast-tv**
: Tag only downloaded tv programmes as iTunes podcasts

**--tag-utf8**
: AtomicParsley accepts UTF-8 input

<a id="author"></a>

# AUTHOR

get_iplayer was written by Phil Lewis &lt;iplayer2 (at sign) linuxcentre.net&gt; and is now maintained by the contributors at http://www.infradead.org/get_iplayer/html/get_iplayer.html

This manual page was originally written by Jonathan Wiltshire &lt;jmw@debian.org&gt; for the Debian project (but may be used by others).

<a id="copyright-notice"></a>

# COPYRIGHT NOTICE

get_iplayer v2.82, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.
