<H1>
get_iplayer Manual
</H1>
<H1>
Table of Contents
</H1>
<UL>
<LI>
<A HREF="#NAME">
NAME
</A>
</LI>
<LI>
<A HREF="#SYNOPSIS">
SYNOPSIS
</A>
</LI>
<LI>
<A HREF="#DESCRIPTION">
DESCRIPTION
</A>
</LI>
<LI>
<A HREF="#OPTIONS">
OPTIONS
</A>
<UL>
<LI>
<A HREF="#Search-Options">
Search Options
</A>
</LI>
<LI>
<A HREF="#Display-Options">
Display Options
</A>
</LI>
<LI>
<A HREF="#Recording-Options">
Recording Options
</A>
</LI>
<LI>
<A HREF="#Output-Options">
Output Options
</A>
</LI>
<LI>
<A HREF="#PVR-Options">
PVR Options
</A>
</LI>
<LI>
<A HREF="#Config-Options">
Config Options
</A>
</LI>
<LI>
<A HREF="#External-Program-Options">
External Program Options
</A>
</LI>
<LI>
<A HREF="#Tagging-Options">
Tagging Options
</A>
</LI>
</UL>
</LI>
<LI>
<A HREF="#AUTHOR">
AUTHOR
</A>
</LI>
<LI>
<A HREF="#COPYRIGHT-NOTICE">
COPYRIGHT NOTICE
</A>
</LI>
</UL>
<HR>
<H1>
<A NAME="NAME">
NAME
</A>
</H1>
get_iplayer - Stream Recording tool and PVR for BBC iPlayer, BBC Podcasts and more
<HR>
<H1>
<A NAME="SYNOPSIS">
SYNOPSIS
</A>
</H1>
<STRONG>get_iplayer</STRONG> [&lt;options&gt;] [&lt;regex|index&gt; ...]

<P>
<STRONG>get_iplayer</STRONG> <STRONG>--get</STRONG> [&lt;options&gt;] &lt;regex|index&gt; ...

<P>
<STRONG>get_iplayer</STRONG> &lt;url&gt; <STRONG>--type</STRONG>=&lt;type&gt; [&lt;options&gt;]

<P>
<STRONG>get_iplayer</STRONG> &lt;pid|url&gt; [<STRONG>--type</STRONG>=&lt;type&gt; &lt;options&gt;]

<P>
<STRONG>get_iplayer</STRONG> <STRONG>--stream</STRONG> [&lt;options&gt;] &lt;regex|index&gt; | mplayer <STRONG>-cache</STRONG> 3072 -

<P>
<STRONG>get_iplayer</STRONG> <STRONG>--stream</STRONG> [&lt;options&gt;] <STRONG>--type</STRONG>=&lt;type&gt; &lt;pid|url&gt; | mplayer <STRONG>-cache</STRONG> 3072 -

<P>
<STRONG>get_iplayer</STRONG> <STRONG>--stream</STRONG> [&lt;options&gt;] <STRONG>--type</STRONG>=livetv,liveradio &lt;regex|index&gt; <STRONG>--player</STRONG>=&quot;mplayer -cache 128 -&quot;

<P>
<STRONG>get_iplayer</STRONG> <STRONG>--refresh</STRONG>

<HR>
<H1>
<A NAME="DESCRIPTION">
DESCRIPTION
</A>
</H1>
<STRONG>get_iplayer</STRONG> lists, searches and records BBC iPlayer TV/Radio, BBC Podcast programmes. Other 3rd-Party plugins may be available.

<P>
<STRONG>get_iplayer</STRONG> has three modes: recording a complete programme for later playback, streaming a programme
directly to a playback application, such as mplayer; and as a Personal Video Recorder (PVR), subscribing to
search terms and recording programmes automatically. It can also stream or record live BBC iPlayer output

<P>
If given no arguments, <STRONG>get_iplayer</STRONG> updates and displays the list of currently available programmes.
Each available programme has a numerical identifier, <STRONG>pid</STRONG>.
<STRONG>get_iplayer</STRONG> utilises the <STRONG>rtmpdump</STRONG> tool to record BBC iPlayer programmes from RTMP flash streams at various qualities.

<P>
In PVR mode, <STRONG>get_iplayer</STRONG> can be called from cron to record programmes to a schedule.

<HR>
<H1>
<A NAME="OPTIONS">
OPTIONS
</A>
</H1>
<H2>
<A NAME="Search-Options">
Search Options
</A>
</H2>
<DL>
<DT>
<STRONG>--before
</STRONG>
</DT>
<DD>
Limit search to programmes added to the cache before N hours ago
</DD>
<DT>
<STRONG>--category &lt;string&gt;
</STRONG>
</DT>
<DD>
Narrow search to matched categories (regex or comma separated values)
</DD>
<DT>
<STRONG>--channel &lt;string&gt;
</STRONG>
</DT>
<DD>
Narrow search to matched channel(s) (regex or comma separated values)
</DD>
<DT>
<STRONG>--exclude &lt;string&gt;
</STRONG>
</DT>
<DD>
Narrow search to exclude matched programme names (regex or comma separated values)
</DD>
<DT>
<STRONG>--exclude-category &lt;string&gt;
</STRONG>
</DT>
<DD>
Narrow search to exclude matched categories (regex or comma separated values)
</DD>
<DT>
<STRONG>--exclude-channel &lt;string&gt;
</STRONG>
</DT>
<DD>
Narrow search to exclude matched channel(s) (regex or comma separated values)
</DD>
<DT>
<STRONG>--fields &lt;field1&gt;,&lt;field2&gt;,..
</STRONG>
</DT>
<DD>
Searches only in the specified comma separated fields
</DD>
<DT>
<STRONG>--future
</STRONG>
</DT>
<DD>
Search future programme schedule if it has been indexed (refresh cache with: --refresh --refresh-future).
</DD>
<DT>
<STRONG>--history
</STRONG>
</DT>
<DD>
Search/show recordings history
</DD>
<DT>
<STRONG>--long, -l
</STRONG>
</DT>
<DD>
Additionally search in programme descriptions and episode names (same as --fields=name,episode,desc )
</DD>
<DT>
<STRONG>--search &lt;search term&gt;
</STRONG>
</DT>
<DD>
GetOpt compliant way of specifying search args
</DD>
<DT>
<STRONG>--since
</STRONG>
</DT>
<DD>
Limit search to programmes added to the cache in the last N hours
</DD>
<DT>
<STRONG>--type &lt;type&gt;
</STRONG>
</DT>
<DD>
Only search in these types of programmes: livetv,tv,liveradio,radio,all (tv is default)
</DD>
<DT>
<STRONG>--versions &lt;versions&gt;
</STRONG>
</DT>
<DD>
Version of programme to search or record.  List is processed from left to right and first version found is downloaded.  Example: '--versions signed,audiodescribed,default' will prefer signed and audiodescribed programmes if available.  Default: 'default'
</DD>
</DL>
<H2>
<A NAME="Display-Options">
Display Options
</A>
</H2>
<DL>
<DT>
<STRONG>--conditions
</STRONG>
</DT>
<DD>
Shows GPLv3 conditions
</DD>
<DT>
<STRONG>--debug
</STRONG>
</DT>
<DD>
Debug output
</DD>
<DT>
<STRONG>--dump-options
</STRONG>
</DT>
<DD>
Dumps all options with their internal option key names
</DD>
<DT>
<STRONG>--help, -h
</STRONG>
</DT>
<DD>
Intermediate help text
</DD>
<DT>
<STRONG>--helpbasic, --usage
</STRONG>
</DT>
<DD>
Basic help text
</DD>
<DT>
<STRONG>--helplong
</STRONG>
</DT>
<DD>
Advanced help text
</DD>
<DT>
<STRONG>--hide
</STRONG>
</DT>
<DD>
Hide previously recorded programmes
</DD>
<DT>
<STRONG>--info, -i
</STRONG>
</DT>
<DD>
Show full programme metadata and availability of modes and subtitles (max 50 matches)
</DD>
<DT>
<STRONG>--list &lt;categories|channel&gt;
</STRONG>
</DT>
<DD>
Show a list of available categories/channels for the selected type and exit
</DD>
<DT>
<STRONG>--listformat &lt;format&gt;
</STRONG>
</DT>
<DD>
Display programme data based on a user-defined format string (such as &lt;pid&gt;, &lt;name&gt; etc)
</DD>
<DT>
<STRONG>--listplugins
</STRONG>
</DT>
<DD>
Display a list of currently available plugins or programme types
</DD>
<DT>
<STRONG>--long, -l
</STRONG>
</DT>
<DD>
Show long programme info
</DD>
<DT>
<STRONG>--manpage &lt;file&gt;
</STRONG>
</DT>
<DD>
Create man page based on current help text
</DD>
<DT>
<STRONG>--nocopyright
</STRONG>
</DT>
<DD>
Don't display copyright header
</DD>
<DT>
<STRONG>--page &lt;number&gt;
</STRONG>
</DT>
<DD>
Page number to display for multipage output
</DD>
<DT>
<STRONG>--pagesize &lt;number&gt;
</STRONG>
</DT>
<DD>
Number of matches displayed on a page for multipage output
</DD>
<DT>
<STRONG>--quiet, -q
</STRONG>
</DT>
<DD>
No logging output
</DD>
<DT>
<STRONG>--series
</STRONG>
</DT>
<DD>
Display Programme series names only with number of episodes
</DD>
<DT>
<STRONG>--show-cache-age
</STRONG>
</DT>
<DD>
Displays the age of the selected programme caches then exit
</DD>
<DT>
<STRONG>--show-options
</STRONG>
</DT>
<DD>
Shows options which are set and where they are defined
</DD>
<DT>
<STRONG>--sort &lt;fieldname&gt;
</STRONG>
</DT>
<DD>
Field to use to sort displayed matches
</DD>
<DT>
<STRONG>--sortreverse
</STRONG>
</DT>
<DD>
Reverse order of sorted matches
</DD>
<DT>
<STRONG>--streaminfo
</STRONG>
</DT>
<DD>
Returns all of the media stream urls of the programme(s)
</DD>
<DT>
<STRONG>--terse
</STRONG>
</DT>
<DD>
Only show terse programme info (does not affect searching)
</DD>
<DT>
<STRONG>--tree
</STRONG>
</DT>
<DD>
Display Programme listings in a tree view
</DD>
<DT>
<STRONG>--verbose, -v
</STRONG>
</DT>
<DD>
Verbose
</DD>
<DT>
<STRONG>--warranty
</STRONG>
</DT>
<DD>
Displays warranty section of GPLv3
</DD>
<DT>
<STRONG>-V
</STRONG>
</DT>
<DD>
Show get_iplayer version and exit.
</DD>
</DL>
<H2>
<A NAME="Recording-Options">
Recording Options
</A>
</H2>
<DL>
<DT>
<STRONG>--aactomp3
</STRONG>
</DT>
<DD>
Transcode AAC audio to MP3 with ffmpeg (CBR 128k unless --mp3vbr is specified)
</DD>
<DT>
<STRONG>--attempts &lt;number&gt;
</STRONG>
</DT>
<DD>
Number of attempts to make or resume a failed connection
</DD>
<DT>
<STRONG>--bandwidth
</STRONG>
</DT>
<DD>
In radio realaudio mode specify the link bandwidth in bps for rtsp streaming (default 512000)
</DD>
<DT>
<STRONG>--force
</STRONG>
</DT>
<DD>
Ignore programme history (unsets --hide option also). Forces a script update if used with -u
</DD>
<DT>
<STRONG>--get, -g
</STRONG>
</DT>
<DD>
Start recording matching programmes. Search terms required unless --pid specified. Use  --search=.* to force download of all available programmes.
</DD>
<DT>
<STRONG>--hash
</STRONG>
</DT>
<DD>
Show recording progress as hashes
</DD>
<DT>
<STRONG>--liveradiomode &lt;mode&gt;,&lt;mode&gt;,..
</STRONG>
</DT>
<DD>
Live Radio Recording modes: flashaac,realaudio,wma. Use --liveradiomode=best to automatically select highest quality available.
</DD>
<DT>
<STRONG>--livetvmode &lt;mode&gt;,&lt;mode&gt;,...
</STRONG>
</DT>
<DD>
Live TV Recoding modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal (default: flashhd,flashvhigh,flashhigh,flashstd,flashnormal). Use --livetvmode=best to automatically select highest quality available.
</DD>
<DT>
<STRONG>--metadata-only
</STRONG>
</DT>
<DD>
Create specified metadata info file without any recording or streaming (can also be used with thumbnail option).
</DD>
<DT>
<STRONG>--mmsnothread
</STRONG>
</DT>
<DD>
Disable parallel threaded recording for mms
</DD>
<DT>
<STRONG>--modes &lt;mode&gt;,&lt;mode&gt;,...
</STRONG>
</DT>
<DD>
Recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow,n95_wifi,flashaac,flashaachigh,flashaacstd,flashaaclow,flashaudio,realaudio,wma.  Use --modes=best to automatically select highest quality available.
</DD>
<DT>
<STRONG>--mp3vbr
</STRONG>
</DT>
<DD>
Set LAME VBR mode to N (0 to 9) for AAC transcoding. 0 = target bitrate 245 Kbit/s, 9 = target bitrate 65 Kbit/s (requires --aactomp3)
</DD>
<DT>
<STRONG>--multimode
</STRONG>
</DT>
<DD>
Allow the recording of more than one mode for the same programme - WARNING: will record all specified/default modes!!
</DD>
<DT>
<STRONG>--overwrite
</STRONG>
</DT>
<DD>
Overwrite recordings if they already exist
</DD>
<DT>
<STRONG>--partial-proxy
</STRONG>
</DT>
<DD>
Only uses web proxy where absolutely required (try this extra option if your proxy fails)
</DD>
<DT>
<STRONG>--pid &lt;pid&gt;
</STRONG>
</DT>
<DD>
Record an arbitrary pid that does not necessarily appear in the index.
</DD>
<DT>
<STRONG>--pid-recursive
</STRONG>
</DT>
<DD>
When used with --pid record all the embedded pids if the pid is a series or brand pid.
</DD>
<DT>
<STRONG>--proxy, -p &lt;url&gt;
</STRONG>
</DT>
<DD>
Web proxy URL e.g. '<A HREF="http://USERNAME:PASSWORD@SERVER:PORT'">http://USERNAME:PASSWORD@SERVER:PORT'</A> or '<A HREF="http://SERVER:PORT'">http://SERVER:PORT'</A>
</DD>
<DT>
<STRONG>--radiomode &lt;mode&gt;,&lt;mode&gt;,...
</STRONG>
</DT>
<DD>
Radio Recording mode(s): flashaac,flashaachigh,flashaacstd,flashaaclow,flashaudio,realaudio,wma (default: flashaachigh,flashaacstd,flashaudio,realaudio,flashaaclow). Use --radiomode=best to automatically select highest quality available.
</DD>
<DT>
<STRONG>--raw
</STRONG>
</DT>
<DD>
Don't transcode or change the recording/stream in any way (i.e. radio/realaudio, rtmp/flv)
</DD>
<DT>
<STRONG>--rtmp-liveradio-opts &lt;options&gt;
</STRONG>
</DT>
<DD>
Add custom options to rtmpdump for liveradio
</DD>
<DT>
<STRONG>--rtmp-livetv-opts &lt;options&gt;
</STRONG>
</DT>
<DD>
Add custom options to rtmpdump for livetv
</DD>
<DT>
<STRONG>--rtmp-radio-opts &lt;options&gt;
</STRONG>
</DT>
<DD>
Add custom options to rtmpdump for radio
</DD>
<DT>
<STRONG>--rtmp-tv-opts &lt;options&gt;
</STRONG>
</DT>
<DD>
Add custom options to rtmpdump for tv
</DD>
<DT>
<STRONG>--rtmpport &lt;port&gt;
</STRONG>
</DT>
<DD>
Override the RTMP port (e.g. 443)
</DD>
<DT>
<STRONG>--start &lt;secs|hh:mm:ss&gt;
</STRONG>
</DT>
<DD>
Recording/streaming start offset (rtmp and realaudio only)
</DD>
<DT>
<STRONG>--stop &lt;secs|hh:mm:ss&gt;
</STRONG>
</DT>
<DD>
Recording/streaming stop offset (can be used to limit live rtmp recording length) rtmp and realaudio only
</DD>
<DT>
<STRONG>--suboffset &lt;offset&gt;
</STRONG>
</DT>
<DD>
Offset the subtitle timestamps by the specified number of milliseconds
</DD>
<DT>
<STRONG>--subsraw
</STRONG>
</DT>
<DD>
Additionally save the raw subtitles file
</DD>
<DT>
<STRONG>--subtitles
</STRONG>
</DT>
<DD>
Download subtitles into srt/SubRip format if available and supported
</DD>
<DT>
<STRONG>--subtitles-only
</STRONG>
</DT>
<DD>
Only download the subtitles, not the programme
</DD>
<DT>
<STRONG>--tag-only
</STRONG>
</DT>
<DD>
Only update the programme tag and not download the programme (can also be used with --history)
</DD>
<DT>
<STRONG>--test, -t
</STRONG>
</DT>
<DD>
Test only - no recording (will show programme type)
</DD>
<DT>
<STRONG>--thumb
</STRONG>
</DT>
<DD>
Download Thumbnail image if available
</DD>
<DT>
<STRONG>--thumbnail-only
</STRONG>
</DT>
<DD>
Only Download Thumbnail image if available, not the programme
</DD>
<DT>
<STRONG>--tvmode &lt;mode&gt;,&lt;mode&gt;,...
</STRONG>
</DT>
<DD>
TV Recoding modes: rtmp,flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow,n95_wifi (default: flashhigh,flashstd,flashnormal). Use --tvmode=best to automatically select highest quality available.
</DD>
<DT>
<STRONG>--url &quot;&lt;url&gt;&quot;
</STRONG>
</DT>
<DD>
Record the embedded media player in the specified URL. Use with --type=&lt;type&gt;.
</DD>
<DT>
<STRONG>--wav
</STRONG>
</DT>
<DD>
In radio realaudio mode output as wav and don't transcode to mp3
</DD>
</DL>
<H2>
<A NAME="Output-Options">
Output Options
</A>
</H2>
<DL>
<DT>
<STRONG>--command, -c &lt;command&gt;
</STRONG>
</DT>
<DD>
Run user command after successful recording using args such as &lt;pid&gt;, &lt;name&gt; etc
</DD>
<DT>
<STRONG>--email &lt;address&gt;
</STRONG>
</DT>
<DD>
Email HTML index of matching programmes to specified address
</DD>
<DT>
<STRONG>--email-password &lt;password&gt;
</STRONG>
</DT>
<DD>
Email password
</DD>
<DT>
<STRONG>--email-port &lt;port number&gt;
</STRONG>
</DT>
<DD>
Email port number (default: appropriate port for --email-security)
</DD>
<DT>
<STRONG>--email-security &lt;TLS|SSL&gt;
</STRONG>
</DT>
<DD>
Email security TLS, SSL (default: none)
</DD>
<DT>
<STRONG>--email-sender &lt;address&gt;
</STRONG>
</DT>
<DD>
Optional email sender address
</DD>
<DT>
<STRONG>--email-smtp &lt;hostname&gt;
</STRONG>
</DT>
<DD>
SMTP server IP address to use to send email (default: localhost)
</DD>
<DT>
<STRONG>--email-user &lt;username&gt;
</STRONG>
</DT>
<DD>
Email username
</DD>
<DT>
<STRONG>--fatfilename
</STRONG>
</DT>
<DD>
Omit characters forbidden by FAT filesystems from filenames but keep whitespace
</DD>
<DT>
<STRONG>--file-prefix &lt;format&gt;
</STRONG>
</DT>
<DD>
The filename prefix (excluding dir and extension) using formatting fields. e.g. '&lt;name&gt;-&lt;episode&gt;-&lt;pid&gt;'
</DD>
<DT>
<STRONG>--fxd &lt;file&gt;
</STRONG>
</DT>
<DD>
Create Freevo FXD XML of matching programmes in specified file
</DD>
<DT>
<STRONG>--html &lt;file&gt;
</STRONG>
</DT>
<DD>
Create basic HTML index of matching programmes in specified file
</DD>
<DT>
<STRONG>--isodate
</STRONG>
</DT>
<DD>
Use ISO8601 dates (YYYY-MM-DD) in filenames
</DD>
<DT>
<STRONG>--metadata &lt;type&gt;
</STRONG>
</DT>
<DD>
Create metadata info file after recording. Valid types are: xbmc, xbmc_movie, freevo, generic
</DD>
<DT>
<STRONG>--mkv
</STRONG>
</DT>
<DD>
Output video in MKV container instead of MP4. Currently no tagging supported from get_iplayer for MKV output
</DD>
<DT>
<STRONG>--mythtv &lt;file&gt;
</STRONG>
</DT>
<DD>
Create Mythtv streams XML of matching programmes in specified file
</DD>
<DT>
<STRONG>--nowrite, -n
</STRONG>
</DT>
<DD>
No writing of file to disk (use with -x to prevent a copy being stored on disk)
</DD>
<DT>
<STRONG>--output, -o &lt;dir&gt;
</STRONG>
</DT>
<DD>
Recording output directory
</DD>
<DT>
<STRONG>--outputliveradio &lt;dir&gt;
</STRONG>
</DT>
<DD>
Output directory for live radio recordings
</DD>
<DT>
<STRONG>--outputlivetv &lt;dir&gt;
</STRONG>
</DT>
<DD>
Output directory for live tv recordings
</DD>
<DT>
<STRONG>--outputlocalfiles &lt;dir&gt;
</STRONG>
</DT>
<DD>
Output directory for localfiles recordings
</DD>
<DT>
<STRONG>--outputpodcast &lt;dir&gt;
</STRONG>
</DT>
<DD>
Output directory for podcast recordings
</DD>
<DT>
<STRONG>--outputradio &lt;dir&gt;
</STRONG>
</DT>
<DD>
Output directory for radio recordings
</DD>
<DT>
<STRONG>--outputtv &lt;dir&gt;
</STRONG>
</DT>
<DD>
Output directory for tv recordings
</DD>
<DT>
<STRONG>--player '&lt;command&gt; &lt;options&gt;'
</STRONG>
</DT>
<DD>
Use specified command to directly play the stream
</DD>
<DT>
<STRONG>--stdout, -x
</STRONG>
</DT>
<DD>
Additionally stream to STDOUT (so you can pipe output to a player)
</DD>
<DT>
<STRONG>--stream
</STRONG>
</DT>
<DD>
Stream to STDOUT (so you can pipe output to a player)
</DD>
<DT>
<STRONG>--subdir, -s
</STRONG>
</DT>
<DD>
Put Recorded files into Programme name subdirectory
</DD>
<DT>
<STRONG>--subdir-format &lt;format&gt;
</STRONG>
</DT>
<DD>
The format to be used for the subdirectory naming using formatting fields. e.g. '&lt;nameshort&gt;-&lt;seriesnum&gt;'
</DD>
<DT>
<STRONG>--symlink &lt;file&gt;
</STRONG>
</DT>
<DD>
Create symlink to &lt;file&gt; once we have the header of the recording
</DD>
<DT>
<STRONG>--thumb-ext &lt;ext&gt;
</STRONG>
</DT>
<DD>
Thumbnail filename extension to use
</DD>
<DT>
<STRONG>--thumbsize &lt;index|width&gt;
</STRONG>
</DT>
<DD>
Default thumbnail size/index to use for the current recording and metadata (see --info for thumbnailN: to get size/index)
</DD>
<DT>
<STRONG>--thumbsizecache &lt;index|width&gt;
</STRONG>
</DT>
<DD>
Default thumbnail size/index to use when building cache and index (see --info for thumbnailN: to get size/index)
</DD>
<DT>
<STRONG>--whitespace, -w
</STRONG>
</DT>
<DD>
Keep whitespace (and escape chars) in filenames
</DD>
<DT>
<STRONG>--xml-alpha
</STRONG>
</DT>
<DD>
Create freevo/Mythtv menu sorted alphabetically by programme name
</DD>
<DT>
<STRONG>--xml-channels
</STRONG>
</DT>
<DD>
Create freevo/Mythtv menu of channels -&gt; programme names -&gt; episodes
</DD>
<DT>
<STRONG>--xml-names
</STRONG>
</DT>
<DD>
Create freevo/Mythtv menu of programme names -&gt; episodes
</DD>
</DL>
<H2>
<A NAME="PVR-Options">
PVR Options
</A>
</H2>
<DL>
<DT>
<STRONG>--comment &lt;string&gt;
</STRONG>
</DT>
<DD>
Adds a comment to a PVR search
</DD>
<DT>
<STRONG>--pvr [pvr search name]
</STRONG>
</DT>
<DD>
Runs the PVR using all saved PVR searches (intended to be run every hour from cron etc). The list can be limited by adding a regex to the command. Synonyms: --pvrrun, --pvr-run
</DD>
<DT>
<STRONG>--pvr-add &lt;search name&gt;
</STRONG>
</DT>
<DD>
Save the named PVR search with the specified search terms.  Search terms required. Use --search=.* to force download of all available programmes. Synonyms: --pvradd
</DD>
<DT>
<STRONG>--pvr-del &lt;search name&gt;
</STRONG>
</DT>
<DD>
Remove the named search from the PVR searches. Synonyms: --pvrdel
</DD>
<DT>
<STRONG>--pvr-disable &lt;search name&gt;
</STRONG>
</DT>
<DD>
Disable (not delete) a named PVR search. Synonyms: --pvrdisable
</DD>
<DT>
<STRONG>--pvr-enable &lt;search name&gt;
</STRONG>
</DT>
<DD>
Enable a previously disabled named PVR search. Synonyms: --pvrenable
</DD>
<DT>
<STRONG>--pvr-exclude &lt;string&gt;
</STRONG>
</DT>
<DD>
Exclude the PVR searches to run by search name (regex or comma separated values). Synonyms: --pvrexclude
</DD>
<DT>
<STRONG>--pvr-list
</STRONG>
</DT>
<DD>
Show the PVR search list. Synonyms: --pvrlist
</DD>
<DT>
<STRONG>--pvr-queue
</STRONG>
</DT>
<DD>
Add currently matched programmes to queue for later one-off recording using the --pvr option. Search terms required unless --pid specified. Use --search=.* to force download of all available programmes. Synonyms: --pvrqueue
</DD>
<DT>
<STRONG>--pvr-scheduler &lt;seconds&gt;
</STRONG>
</DT>
<DD>
Runs the PVR using all saved PVR searches every &lt;seconds&gt;. Synonyms: --pvrscheduler
</DD>
<DT>
<STRONG>--pvr-single &lt;search name&gt;
</STRONG>
</DT>
<DD>
Runs a named PVR search. Synonyms: --pvrsingle
</DD>
</DL>
<H2>
<A NAME="Config-Options">
Config Options
</A>
</H2>
<DL>
<DT>
<STRONG>--expiry, -e &lt;secs&gt;
</STRONG>
</DT>
<DD>
Cache expiry in seconds (default 4hrs)
</DD>
<DT>
<STRONG>--limit-matches &lt;number&gt;
</STRONG>
</DT>
<DD>
Limits the number of matching results for any search (and for every PVR search)
</DD>
<DT>
<STRONG>--localfilesdirs &lt;dir&gt;[,dir,]
</STRONG>
</DT>
<DD>
Directories/Folders to scan for new files
</DD>
<DT>
<STRONG>--nopurge
</STRONG>
</DT>
<DD>
Don't ask to delete programmes recorded over 30 days ago
</DD>
<DT>
<STRONG>--packagemanager &lt;string&gt;
</STRONG>
</DT>
<DD>
Tell the updater that we were installed using a package manager and don't update (use either: apt,rpm,deb,yum,disable)
</DD>
<DT>
<STRONG>--plugins-update
</STRONG>
</DT>
<DD>
Update get_iplayer plugins to the latest
</DD>
<DT>
<STRONG>--prefs-add
</STRONG>
</DT>
<DD>
Add/Change specified saved user or preset options
</DD>
<DT>
<STRONG>--prefs-clear
</STRONG>
</DT>
<DD>
Remove *ALL* saved user or preset options
</DD>
<DT>
<STRONG>--prefs-del
</STRONG>
</DT>
<DD>
Remove specified saved user or preset options
</DD>
<DT>
<STRONG>--prefs-show
</STRONG>
</DT>
<DD>
Show saved user or preset options
</DD>
<DT>
<STRONG>--preset, -z &lt;name&gt;
</STRONG>
</DT>
<DD>
Use specified user options preset
</DD>
<DT>
<STRONG>--preset-list
</STRONG>
</DT>
<DD>
Show all valid presets
</DD>
<DT>
<STRONG>--profile-dir &lt;dir&gt;
</STRONG>
</DT>
<DD>
Override the user profile directory/folder
</DD>
<DT>
<STRONG>--refresh, --flush, -f
</STRONG>
</DT>
<DD>
Refresh cache
</DD>
<DT>
<STRONG>--refresh-exclude &lt;string&gt;
</STRONG>
</DT>
<DD>
Exclude matched channel(s) when refreshing cache (regex or comma separated values)
</DD>
<DT>
<STRONG>--refresh-future
</STRONG>
</DT>
<DD>
Obtain future programme schedule when refreshing cache (between 7-14 days)
</DD>
<DT>
<STRONG>--refresh-include &lt;string&gt;
</STRONG>
</DT>
<DD>
Include matched channel(s) when refreshing cache (regex or comma separated values)
</DD>
<DT>
<STRONG>--skipdeleted
</STRONG>
</DT>
<DD>
Skip the download of metadata/thumbs/subs if the media file no longer exists. Use with --history &amp; --metadataonly/subsonly/thumbonly.
</DD>
<DT>
<STRONG>--update, -u
</STRONG>
</DT>
<DD>
Update get_iplayer if a newer one exists
</DD>
<DT>
<STRONG>--webrequest &lt;urlencoded string&gt;
</STRONG>
</DT>
<DD>
Specify all options as a urlencoded string of &quot;name=val&amp;name=val&amp;...&quot;
</DD>
</DL>
<H2>
<A NAME="External-Program-Options">
External Program Options
</A>
</H2>
<DL>
<DT>
<STRONG>--atomicparsley &lt;path&gt;
</STRONG>
</DT>
<DD>
Location of AtomicParsley tagger binary
</DD>
<DT>
<STRONG>--ffmpeg &lt;path&gt;
</STRONG>
</DT>
<DD>
Location of ffmpeg binary
</DD>
<DT>
<STRONG>--id3v2 &lt;path&gt;
</STRONG>
</DT>
<DD>
Location of id3v2 or id3tag binary
</DD>
<DT>
<STRONG>--lame &lt;path&gt;
</STRONG>
</DT>
<DD>
Location of lame binary
</DD>
<DT>
<STRONG>--mplayer &lt;path&gt;
</STRONG>
</DT>
<DD>
Location of mplayer binary
</DD>
<DT>
<STRONG>--rtmpdump &lt;path&gt;
</STRONG>
</DT>
<DD>
Location of rtmpdump binary. Synonyms: --flvstreamer
</DD>
<DT>
<STRONG>--vlc &lt;path&gt;
</STRONG>
</DT>
<DD>
Location of vlc or cvlc binary
</DD>
</DL>
<H2>
<A NAME="Tagging-Options">
Tagging Options
</A>
</H2>
<DL>
<DT>
<STRONG>--no-artwork
</STRONG>
</DT>
<DD>
Do not embed thumbnail image in output file.  All other metadata values will be written.
</DD>
<DT>
<STRONG>--no-tag
</STRONG>
</DT>
<DD>
Do not tag downloaded programmes
</DD>
<DT>
<STRONG>--tag-cnid
</STRONG>
</DT>
<DD>
AtomicParsley supports --cnID argument to add catalog ID used for combining HD and SD versions in iTunes
</DD>
<DT>
<STRONG>--tag-fulltitle
</STRONG>
</DT>
<DD>
Use complete title (including series) instead of shorter episode title
</DD>
<DT>
<STRONG>--tag-hdvideo
</STRONG>
</DT>
<DD>
AtomicParsley supports --hdvideo argument for HD video flag
</DD>
<DT>
<STRONG>--tag-longdesc
</STRONG>
</DT>
<DD>
AtomicParsley supports --longdesc argument for long description text
</DD>
<DT>
<STRONG>--tag-longdescription
</STRONG>
</DT>
<DD>
AtomicParsley supports --longDescription argument for long description text
</DD>
<DT>
<STRONG>--tag-podcast
</STRONG>
</DT>
<DD>
Tag downloaded radio and tv programmes as iTunes podcasts (requires MP3::Tag module for AAC/MP3 files)
</DD>
<DT>
<STRONG>--tag-podcast-radio
</STRONG>
</DT>
<DD>
Tag only downloaded radio programmes as iTunes podcasts (requires MP3::Tag module for AAC/MP3 files)
</DD>
<DT>
<STRONG>--tag-podcast-tv
</STRONG>
</DT>
<DD>
Tag only downloaded tv programmes as iTunes podcasts
</DD>
<DT>
<STRONG>--tag-utf8
</STRONG>
</DT>
<DD>
AtomicParsley accepts UTF-8 input
</DD>
</DL>
<HR>
<H1>
<A NAME="AUTHOR">
AUTHOR
</A>
</H1>
get_iplayer was written by Phil Lewis &lt;iplayer2 (at sign) linuxcentre.net&gt; and is now maintained by the contributors at <A HREF="http://www.infradead.org/get_iplayer/html/get_iplayer.html">http://www.infradead.org/get_iplayer/html/get_iplayer.html</A>
<P>
This manual page was originally written by Jonathan Wiltshire &lt;jmw (at sign) debian.org&gt; for the Debian project (but may be used by others).
<HR>
<H1>
<A NAME="COPYRIGHT-NOTICE">
COPYRIGHT NOTICE
</A>
</H1>
get_iplayer v2.82, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.
