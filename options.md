# get_iplayer Options

# Table of Contents

* [Search Options](#search-options)

* [Display Options](#display-options)

* [Recording Options](#recording-options)

* [Output Options](#output-options)

* [PVR Options](#pvr-options)

* [Config Options](#config-options)

* [External Program Options](#external-program-options)

* [Tagging Options](#tagging-options)

<a id="search-options"></a>

## Search Options

|Options file|Command line|Description|
|------------|------------|-----------|
|before|--before|Limit search to programmes added to the cache before N hours ago|
|category|--category &lt;string&gt;|Narrow search to matched categories (regex or comma separated values)|
|channel|--channel &lt;string&gt;|Narrow search to matched channel(s) (regex or comma separated values)|
|exclude|--exclude &lt;string&gt;|Narrow search to exclude matched programme names (regex or comma separated values)|
|excludecategory|--exclude-category &lt;string&gt;|Narrow search to exclude matched categories (regex or comma separated values)|
|excludechannel|--exclude-channel &lt;string&gt;|Narrow search to exclude matched channel(s) (regex or comma separated values)|
|fields|--fields &lt;field1&gt;,&lt;field2&gt;,...|Searches only in the specified comma separated fields|
|future|--future|Search future programme schedule if it has been indexed (refresh cache with: --refresh --refresh-future).|
|history|--history|Search/show recordings history|
|long|--long, -l|Additionally search in programme descriptions and episode names (same as --fields=name,episode,desc )|
|search|--search &lt;search term&gt;|GetOpt compliant way of specifying search args|
|since|--since|Limit search to programmes added to the cache in the last N hours|
|type|--type &lt;type&gt;|Only search in these types of programmes: livetv,tv,liveradio,radio,all (tv is default)|
|versionlist|--versions &lt;versions&gt;|Version of programme to search or record.  List is processed from left to right and first version found is downloaded.  Example: &#39;--versions signed,audiodescribed,default&#39; will prefer signed and audiodescribed programmes if available.  Default: &#39;default&#39;|

<a id="display-options"></a>

## Display Options

|Options file|Command line|Description|
|------------|------------|-----------|
|conditions|--conditions|Shows GPLv3 conditions|
|debug|--debug|Debug output|
|dumpoptions|--dump-options|Dumps all options with their internal option key names|
|help|--help, -h|Intermediate help text|
|helpbasic|--helpbasic, --usage|Basic help text|
|helplong|--helplong|Advanced help text|
|hide|--hide|Hide previously recorded programmes|
|info|--info, -i|Show full programme metadata and availability of modes and subtitles (max 50 matches)|
|list|--list &lt;categories&#124;channel&gt;|Show a list of available categories/channels for the selected type and exit|
|listformat|--listformat &lt;format&gt;|Display programme data based on a user-defined format string (such as &lt;pid&gt;, &lt;name&gt; etc)|
|listplugins|--listplugins|Display a list of currently available plugins or programme types|
|long|--long, -l|Show long programme info|
|manpage|--manpage &lt;file&gt;|Create man page based on current help text|
|nocopyright|--nocopyright|Don&#39;t display copyright header|
|page|--page &lt;number&gt;|Page number to display for multipage output|
|pagesize|--pagesize &lt;number&gt;|Number of matches displayed on a page for multipage output|
|quiet|--quiet, -q|No logging output|
|series|--series|Display Programme series names only with number of episodes|
|showcacheage|--show-cache-age|Displays the age of the selected programme caches then exit|
|showoptions|--show-options|Shows options which are set and where they are defined|
|showver|-V|Show get_iplayer version and exit.|
|sortmatches|--sort &lt;fieldname&gt;|Field to use to sort displayed matches|
|sortreverse|--sortreverse|Reverse order of sorted matches|
|streaminfo|--streaminfo|Returns all of the media stream urls of the programme(s)|
|terse|--terse|Only show terse programme info (does not affect searching)|
|tree|--tree|Display Programme listings in a tree view|
|verbose|--verbose, -v|Verbose|
|warranty|--warranty|Displays warranty section of GPLv3|

<a id="recording-options"></a>

## Recording Options

|Options file|Command line|Description|
|------------|------------|-----------|
|aactomp3|--aactomp3|Transcode AAC audio to MP3 with ffmpeg/avconv (CBR 128k unless --mp3vbr is specified)|
|attempts|--attempts &lt;number&gt;|Number of attempts to make or resume a failed connection|
|bandwidth|--bandwidth|In radio realaudio mode specify the link bandwidth in bps for rtsp streaming (default 512000)|
|ffmpegliveradioopts|--ffmpeg-liveradio-opts &lt;options| Add custom options to ffmpeg re-muxing for liveradio|
|ffmpeglivetvopts|--ffmpeg-livetv-opts &lt;options&gt;|Add custom options to ffmpeg re-muxing for livetv|
|ffmpegradioopts|--ffmpeg-radio-opts &lt;options&gt;|Add custom options to ffmpeg re-muxing for radio|
|ffmpegtvopts|--ffmpeg-tv-opts &lt;options&gt;|Add custom options to ffmpeg re-muxing for tv|
|force|--force|Ignore programme history (unsets --hide option also). Forces a script update if used with -u|
|get|--get, -g|Start recording matching programmes. Search terms required unless --pid specified. Use  --search=.* to force download of all available programmes.|
|hash|--hash|Show recording progress as hashes|
|liveradiomode|--liveradiomode &lt;mode&gt;,&lt;mode&gt;,...|Live Radio recording modes: flashaachigh,flashaacstd,flashaudio,flashaaclow,wma. Shortcuts: default,good,better(=default),best,rtmp,flash,flashaac. (&#39;default&#39;=flashaachigh,flashaacstd,flashaaclow,wma)|
|livetvmode|--livetvmode &lt;mode&gt;,&lt;mode&gt;,...|Live TV recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow. Shortcuts: default,good,better(=default),best,rtmp,flash. (&#39;default&#39;=flashvhigh,flashhigh,flashstd,flashnormal,flashlow)|
|metadataonly|--metadata-only|Create specified metadata info file without any recording or streaming (can also be used with thumbnail option).|
|mmsnothread|--mmsnothread|Disable parallel threaded recording for mms|
|modes|--modes &lt;mode&gt;,&lt;mode&gt;,...|Recording modes.  See --tvmode and --radiomode for available modes and defaults. Shortcuts: default,good,better(=default),best. Use --modes=best to select highest quality available (incl. HD TV).|
|mp3vbr|--mp3vbr|Set LAME VBR mode to N (0 to 9) for AAC transcoding. 0 = target bitrate 245 Kbit/s, 9 = target bitrate 65 Kbit/s (requires --aactomp3)|
|multimode|--multimode|Allow the recording of more than one mode for the same programme - WARNING: will record all specified/default modes!!|
|overwrite|--overwrite|Overwrite recordings if they already exist|
|partialproxy|--partial-proxy|Only uses web proxy where absolutely required (try this extra option if your proxy fails)|
|pid|--pid &lt;pid&gt;|Record an arbitrary pid that does not necessarily appear in the index.|
|pidrecursive|--pid-recursive|When used with --pid record all the embedded pids if the pid is a series or brand pid.|
|proxy|--proxy, -p &lt;url&gt;|Web proxy URL e.g. &#39;http://USERNAME:PASSWORD@SERVER:PORT&#39; or &#39;http://SERVER:PORT&#39;|
|radiomode|--radiomode &lt;mode&gt;,&lt;mode&gt;,...|Radio recording modes: flashaachigh,flashaacstd,flashaudio,flashaaclow,wma. Shortcuts: default,good,better(=default),best,rtmp,flash,flashaac. (&#39;default&#39;=flashaachigh,flashaacstd,flashaudio,flashaaclow,wma)|
|raw|--raw|Don&#39;t transcode or change the recording/stream in any way (i.e. radio/realaudio, rtmp/flv)|
|rtmpliveradioopts|--rtmp-liveradio-opts &lt;options&gt;|Add custom options to rtmpdump for liveradio|
|rtmplivetvopts|--rtmp-livetv-opts &lt;options&gt;|Add custom options to rtmpdump for livetv|
|rtmpport|--rtmpport &lt;port&gt;|Override the RTMP port (e.g. 443)|
|rtmpradioopts|--rtmp-radio-opts &lt;options&gt;|Add custom options to rtmpdump for radio|
|rtmptvopts|--rtmp-tv-opts &lt;options&gt;|Add custom options to rtmpdump for tv|
|start|--start &lt;secs&#124;hh:mm:ss&gt;|Recording/streaming start offset (rtmp and realaudio only)|
|stop|--stop &lt;secs&#124;hh:mm:ss&gt;|Recording/streaming stop offset (can be used to limit live rtmp recording length) rtmp and realaudio only|
|suboffset|--suboffset &lt;offset&gt;|Offset the subtitle timestamps by the specified number of milliseconds|
|subsonly|--subtitles-only|Only download the subtitles, not the programme|
|subsraw|--subsraw|Additionally save the raw subtitles file|
|subtitles|--subtitles|Download subtitles into srt/SubRip format if available and supported|
|tagonly|--tag-only|Only update the programme tag and not download the programme (can also be used with --history)|
|test|--test, -t|Test only - no recording (will show programme type)|
|thumb|--thumb|Download Thumbnail image if available|
|thumbonly|--thumbnail-only|Only Download Thumbnail image if available, not the programme|
|tvmode|--tvmode &lt;mode&gt;,&lt;mode&gt;,...|TV recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow. Shortcuts: default,good,better(=default),best,rtmp,flash. (Use &#39;best&#39; for HD TV. &#39;default&#39;=flashvhigh,flashhigh,flashstd,flashnormal,flashlow)|
|url|--url &quot;&lt;url&gt;&quot;|Record the embedded media player in the specified URL. Use with --type=&lt;type&gt;.|
|wav|--wav|In radio realaudio mode output as wav and don&#39;t transcode to mp3|

<a id="output-options"></a>

## Output Options

|Options file|Command line|Description|
|------------|------------|-----------|
|command|--command, -c &lt;command&gt;|Run user command after successful recording using args such as &lt;pid&gt;, &lt;name&gt; etc|
|email|--email &lt;address&gt;|Email HTML index of matching programmes to specified address|
|emailpassword|--email-password &lt;password&gt;|Email password|
|emailport|--email-port &lt;port number&gt;|Email port number (default: appropriate port for --email-security)|
|emailsecurity|--email-security &lt;TLS&#124;SSL&gt;|Email security TLS, SSL (default: none)|
|emailsender|--email-sender &lt;address&gt;|Optional email sender address|
|emailsmtp|--email-smtp &lt;hostname&gt;|SMTP server IP address to use to send email (default: localhost)|
|emailuser|--email-user &lt;username&gt;|Email username|
|fatfilename|--fatfilename|Omit characters forbidden by FAT filesystems from filenames but keep whitespace|
|fileprefix|--file-prefix &lt;format&gt;|The filename prefix (excluding dir and extension) using formatting fields. e.g. &#39;&lt;name&gt;-&lt;episode&gt;-&lt;pid&gt;&#39;|
|fxd|--fxd &lt;file&gt;|Create Freevo FXD XML of matching programmes in specified file|
|html|--html &lt;file&gt;|Create basic HTML index of matching programmes in specified file|
|isodate|--isodate|Use ISO8601 dates (YYYY-MM-DD) in filenames|
|metadata|--metadata &lt;type&gt;|Create metadata info file after recording. Valid types are: xbmc, xbmc_movie, freevo, generic|
|mkv|--mkv|Output video in MKV container instead of MP4. Currently no tagging supported from get_iplayer for MKV output|
|mythtv|--mythtv &lt;file&gt;|Create Mythtv streams XML of matching programmes in specified file|
|nowrite|--nowrite, -n|No writing of file to disk (use with -x to prevent a copy being stored on disk)|
|output|--output, -o &lt;dir&gt;|Recording output directory|
|outputliveradio|--outputliveradio &lt;dir&gt;|Output directory for live radio recordings|
|outputlivetv|--outputlivetv &lt;dir&gt;|Output directory for live tv recordings|
|outputlocalfiles|--outputlocalfiles &lt;dir&gt;|Output directory for localfiles recordings|
|outputpodcast|--outputpodcast &lt;dir&gt;|Output directory for podcast recordings|
|outputradio|--outputradio &lt;dir&gt;|Output directory for radio recordings|
|outputtv|--outputtv &lt;dir&gt;|Output directory for tv recordings|
|player|--player &#39;&lt;command&gt; &lt;options&gt;&#39;|Use specified command to directly play the stream|
|stdout|--stdout, -x|Additionally stream to STDOUT (so you can pipe output to a player)|
|stream|--stream|Stream to STDOUT (so you can pipe output to a player)|
|subdir|--subdir, -s|Put Recorded files into Programme name subdirectory|
|subdirformat|--subdir-format &lt;format&gt;|The format to be used for the subdirectory naming using formatting fields. e.g. &#39;&lt;nameshort&gt;-&lt;seriesnum&gt;&#39;|
|symlink|--symlink &lt;file&gt;|Create symlink to &lt;file&gt; once we have the header of the recording|
|thumbext|--thumb-ext &lt;ext&gt;|Thumbnail filename extension to use|
|thumbsize|--thumbsize &lt;index&#124;width&gt;|Default thumbnail size/index to use for the current recording and metadata (see --info for thumbnailN: to get size/index)|
|thumbsizecache|--thumbsizecache &lt;index&#124;width&gt;|Default thumbnail size/index to use when building cache and index (see --info for thumbnailN: to get size/index)|
|whitespace|--whitespace, -w|Keep whitespace (and escape chars) in filenames|
|xmlalpha|--xml-alpha|Create freevo/Mythtv menu sorted alphabetically by programme name|
|xmlchannels|--xml-channels|Create freevo/Mythtv menu of channels -&gt; programme names -&gt; episodes|
|xmlnames|--xml-names|Create freevo/Mythtv menu of programme names -&gt; episodes|

<a id="pvr-options"></a>

## PVR Options

|Options file|Command line|Description|
|------------|------------|-----------|
|comment|--comment &lt;string&gt;|Adds a comment to a PVR search|
|pvr|--pvr [pvr search name]|Runs the PVR using all saved PVR searches (intended to be run every hour from cron etc). The list can be limited by adding a regex to the command. Synonyms: --pvrrun, --pvr-run|
|pvradd|--pvr-add &lt;search name&gt;|Save the named PVR search with the specified search terms.  Search terms required. Use --search=.* to force download of all available programmes. Synonyms: --pvradd|
|pvrdel|--pvr-del &lt;search name&gt;|Remove the named search from the PVR searches. Synonyms: --pvrdel|
|pvrdisable|--pvr-disable &lt;search name&gt;|Disable (not delete) a named PVR search. Synonyms: --pvrdisable|
|pvrenable|--pvr-enable &lt;search name&gt;|Enable a previously disabled named PVR search. Synonyms: --pvrenable|
|pvrexclude|--pvr-exclude &lt;string&gt;|Exclude the PVR searches to run by search name (regex or comma separated values). Synonyms: --pvrexclude|
|pvrlist|--pvr-list|Show the PVR search list. Synonyms: --pvrlist|
|pvrqueue|--pvr-queue|Add currently matched programmes to queue for later one-off recording using the --pvr option. Search terms required unless --pid specified. Use --search=.* to force download of all available programmes. Synonyms: --pvrqueue|
|pvrscheduler|--pvr-scheduler &lt;seconds&gt;|Runs the PVR using all saved PVR searches every &lt;seconds&gt;. Synonyms: --pvrscheduler|
|pvrsingle|--pvr-single &lt;search name&gt;|Runs a named PVR search. Synonyms: --pvrsingle|

<a id="config-options"></a>

## Config Options

|Options file|Command line|Description|
|------------|------------|-----------|
|expiry|--expiry, -e &lt;secs&gt;|Cache expiry in seconds (default 4hrs)|
|limitmatches|--limit-matches &lt;number&gt;|Limits the number of matching results for any search (and for every PVR search)|
|localfilesdirs|--localfilesdirs &lt;dir&gt;[,dir,]|Directories/Folders to scan for new files|
|nopurge|--nopurge|Don&#39;t ask to delete programmes recorded over 30 days ago|
|packagemanager|--packagemanager &lt;string&gt;|Tell the updater that we were installed using a package manager and don&#39;t update (use either: apt,rpm,deb,yum,disable)|
|pluginsupdate|--plugins-update|Update get_iplayer plugins to the latest|
|prefsadd|--prefs-add|Add/Change specified saved user or preset options|
|prefsclear|--prefs-clear|Remove *ALL* saved user or preset options|
|prefsdel|--prefs-del|Remove specified saved user or preset options|
|prefsshow|--prefs-show|Show saved user or preset options|
|preset|--preset, -z &lt;name&gt;|Use specified user options preset|
|presetlist|--preset-list|Show all valid presets|
|profiledir|--profile-dir &lt;dir&gt;|Override the user profile directory/folder|
|refresh|--refresh, --flush, -f|Refresh cache|
|refreshexclude|--refresh-exclude &lt;string&gt;|Exclude matched channel(s) when refreshing cache (regex or comma separated values)|
|refreshfuture|--refresh-future|Obtain future programme schedule when refreshing cache (between 7-14 days)|
|refreshinclude|--refresh-include &lt;string&gt;|Include matched channel(s) when refreshing cache (regex or comma separated values)|
|skipdeleted|--skipdeleted|Skip the download of metadata/thumbs/subs if the media file no longer exists. Use with --history &amp; --metadataonly/subsonly/thumbonly.|
|update|--update, -u|Update get_iplayer if a newer one exists|
|webrequest|--webrequest &lt;urlencoded string&gt;|Specify all options as a urlencoded string of &quot;name=val&amp;name=val&amp;...&quot;|

<a id="external-program-options"></a>

## External Program Options

|Options file|Command line|Description|
|------------|------------|-----------|
|atomicparsley|--atomicparsley &lt;path&gt;|Location of AtomicParsley tagger binary|
|ffmpeg|--ffmpeg &lt;path&gt;|Location of ffmpeg or avconv binary. Synonyms: --avconv|
|id3v2|--id3v2 &lt;path&gt;|Location of id3v2 or id3tag binary|
|lame|--lame &lt;path&gt;|Location of lame binary|
|mplayer|--mplayer &lt;path&gt;|Location of mplayer binary|
|rtmpdump|--rtmpdump &lt;path&gt;|Location of rtmpdump binary. Synonyms: --flvstreamer|
|vlc|--vlc &lt;path&gt;|Location of vlc or cvlc binary|

<a id="tagging-options"></a>

## Tagging Options

|Options file|Command line|Description|
|------------|------------|-----------|
|noartwork|--no-artwork|Do not embed thumbnail image in output file.  All other metadata values will be written.|
|notag|--no-tag|Do not tag downloaded programmes|
|tag_cnid|--tag-cnid|Use AtomicParsley --cnID argument (if supported) to add catalog ID used for combining HD and SD versions in iTunes|
|tag_fulltitle|--tag-fulltitle|Use complete title (including series) instead of shorter episode title|
|tag_hdvideo|--tag-hdvideo|AtomicParsley supports --hdvideo argument for HD video flag|
|tag_longdesc|--tag-longdesc|AtomicParsley supports --longdesc argument for long description text|
|tag_longdescription|--tag-longdescription|AtomicParsley supports --longDescription argument for long description text|
|tag_podcast|--tag-podcast|Tag downloaded radio and tv programmes as iTunes podcasts (requires MP3::Tag module for AAC/MP3 files)|
|tag_podcast_radio|--tag-podcast-radio|Tag only downloaded radio programmes as iTunes podcasts (requires MP3::Tag module for AAC/MP3 files)|
|tag_podcast_tv|--tag-podcast-tv|Tag only downloaded tv programmes as iTunes podcasts|
|tag_utf8|--tag-utf8|AtomicParsley accepts UTF-8 input|
