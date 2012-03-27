

SYNOPSIS
--------

           get_iplayer [<options>] [<regex|index> ...]

           get_iplayer --get [<options>] <regex|index> ...
           get_iplayer <url> --type=<type> [<options>]

           get_iplayer <pid|url> [--type=<type> <options>]

           get_iplayer --stream [<options>] <regex|index> | mplayer -cache 3072 -

           get_iplayer --stream  [<options>]  --type=<type>  <pid|url>  |  mplayer
           -cache 3072 -

           get_iplayer  --stream [<options>] --type=livetv,liveradio <regex|index>
           --player="mplayer -cache 128 -"

           get_iplayer --refresh

DESCRIPTION
-----------

           get_iplayer lists, searches and records BBC iPlayer TV/Radio, BBC  Pod-
           cast programmes. Other 3rd-Party plugins may be available.

           get_iplayer  has  three modes: recording a complete programme for later
           playback, streaming a programme directly  to  a  playback  application,
           such as mplayer; and as a Personal Video Recorder (PVR), subscribing to
           search terms and recording programmes automatically. It can also stream
           or record live BBC iPlayer output

           If  given  no  arguments,  get_iplayer updates and displays the list of
           currently available programmes.  Each available programme has a numeri-
           cal  identifier, pid.  get_iplayer utilises the rtmpdump tool to record
           BBC iPlayer programmes from RTMP flash streams at various qualities.

           In PVR mode, get_iplayer can be called from cron to  record  programmes
           to a schedule.

OPTIONS
-------

       Search Options:
           --before
                  Limit search to programmes added to the cache before N hours ago

           --category <string>
                  Narrow search to matched categories (regex  or  comma  separated
                  values)

           --channel <string>
                  Narrow  search  to  matched channel(s) (regex or comma separated
                  values)

           --exclude <string>
                  Narrow search to exclude matched programme names (regex or comma
                  Search future programme schedule if it has been indexed (refresh
                  cache with: --refresh --refresh-future).

           --history
                  Search/show recordings history

           --long, -l
                  Additionally search in programme descriptions and episode  names
                  (same as --fields=name,episode,desc )

           --search <search term>
                  GetOpt compliant way of specifying search args

           --since
                  Limit  search  to  programmes  added  to the cache in the last N
                  hours

           --type <type>
                  Only search in  these  types  of  programmes:  livetv,tv,livera-
                  dio,radio,all (tv is default)

           --versions <versions>
                  Version  of  programme  to  search or record.  List is processed
                  from left to right and first version found is downloaded.  Exam-
                  ple:   '--versions  signed,audiodescribed,default'  will  prefer
                  signed and audiodescribed  programmes  if  available.   Default:
                  'default'

       Display Options:
           --conditions
                  Shows GPLv3 conditions

           --debug
                  Debug output

           --dump-options
                  Dumps all options with their internal option key names

           --help, -h
                  Intermediate help text

           --helpbasic, --usage
                  Basic help text

           --helplong
                  Advanced help text

           --hide Hide previously recorded programmes

           --info, -i
                  Show  full programme metadata and availability of modes and sub-
                  titles (max 50 matches)

           --manpage <file>
                  Create man page based on current help text

           --nocopyright
                  Don't display copyright header

           --page <number>
                  Page number to display for multipage output

           --pagesize <number>
                  Number of matches displayed on a page for multipage output

           --quiet, -q
                  No logging output

           --series
                  Display Programme series names only with number of episodes

           --show-cache-age
                  Displays the age of the selected programme caches then exit

           --show-options
                  Shows options which are set and where they are defined

           --sort <fieldname>
                  Field to use to sort displayed matches

           --sortreverse
                  Reverse order of sorted matches

           --streaminfo
                  Returns all of the media stream urls of the programme(s)

           --terse
                  Only show terse programme info (does not affect searching)

           --tree Display Programme listings in a tree view

           --verbose, -v
                  Verbose

           --warranty
                  Displays warranty section of GPLv3

           -V     Show get_iplayer version and exit.

       Recording Options:
           --aactomp3
                  Transcode AAC audio to MP3 with ffmpeg (CBR 128k unless --mp3vbr
                  is specified)

                  all available programmes.

           --hash Show recording progress as hashes

           --liveradiomode <mode>,<mode>,..
                  Live Radio Recording modes: flashaac,realaudio,wma.  Use  --liv-
                  eradiomode=best  to  automatically select highest quality avail-
                  able.

           --livetvmode <mode>,<mode>,...
                  Live  TV  Recoding  modes:   flashhd,flashvhigh,flashhigh,flash-
                  std,flashnormal   (default:  flashhd,flashvhigh,flashhigh,flash-
                  std,flashnormal). Use --livetvmode=best to automatically  select
                  highest quality available.

           --metadata-only
                  Create  specified  metadata  info  file without any recording or
                  streaming (can also be used with thumbnail option).

           --mmsnothread
                  Disable parallel threaded recording for mms

           --modes <mode>,<mode>,...
                  Recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnor-
                  mal,flashlow,n95_wifi,flashaac,flashaachigh,flashaacstd,flashaa-
                  clow,flashaudio,realaudio,wma.  Use  --modes=best  to  automati-
                  cally select highest quality available.

           --mp3vbr
                  Set  LAME VBR mode to N (0 to 9) for AAC transcoding. 0 = target
                  bitrate 245 Kbit/s, 9  =  target  bitrate  65  Kbit/s  (requires
                  --aactomp3)

           --multimode
                  Allow the recording of more than one mode for the same programme
                  - WARNING: will record all specified/default modes!!

           --overwrite
                  Overwrite recordings if they already exist

           --partial-proxy
                  Only uses web proxy where absolutely required  (try  this  extra
                  option if your proxy fails)

           --pid <pid>
                  Record  an arbitrary pid that does not necessarily appear in the
                  index.

           --pid-recursive
                  When used with --pid record all the embedded pids if the pid  is
                  a series or brand pid.

           --rtmp-liveradio-opts <options>
                  Add custom options to flvstreamer for liveradio

           --rtmp-livetv-opts <options>
                  Add custom options to flvstreamer for livetv

           --rtmp-radio-opts <options>
                  Add custom options to flvstreamer for radio

           --rtmp-tv-opts <options>
                  Add custom options to flvstreamer for tv

           --rtmpport <port>
                  Override the RTMP port (e.g. 443)

           --start <secs>
                  Recording/streaming start offset (rtmp and realaudio only)

           --stop <secs>
                  Recording/streaming  stop offset (can be used to limit live rtmp
                  recording length) rtmp and realaudio only

           --suboffset <offset>
                  Offset the subtitle timestamps by the specified number  of  mil-
                  liseconds

           --subsraw
                  Additionally save the raw subtitles file

           --subtitles
                  Download  subtitles into srt/SubRip format if available and sup-
                  ported

           --subtitles-only
                  Only download the subtitles, not the programme

           --tag-only
                  Only update the programme tag and  not  download  the  programme
                  (can also be used with --history)

           --test, -t
                  Test only - no recording (will show programme type)

           --thumb
                  Download Thumbnail image if available

           --thumbnail-only
                  Only Download Thumbnail image if available, not the programme

           --tvmode <mode>,<mode>,...
                  TV   Recoding   modes:  rtmp,flashhd,flashvhigh,flashhigh,flash-
                  std,flashnormal,flashlow,n95_wifi   (default:   flashhigh,flash-

           --email <address>
                  Email HTML index of matching programmes to specified address

           --email-sender <address>
                  Optional email sender address

           --email-smtp <hostname>
                  SMTP server IP address to use to send email (default: localhost)

           --fatfilename
                  Omit characters forbidden by FAT filesystems from filenames  but
                  keep whitespace

           --file-prefix <format>
                  The  filename prefix (excluding dir and extension) using format-
                  ting fields. e.g. '<name>-<episode>-<pid>'

           --fxd <file>
                  Create Freevo FXD XML of matching programmes in specified file

           --html <file>
                  Create basic HTML index of matching programmes in specified file

           --isodate
                  Use ISO8601 dates (YYYY-MM-DD) in filenames

           --metadata <type>
                  Create  metadata  info  file  after  recording. Valid types are:
                  xbmc, xbmc_movie, freevo, generic

           --mkv  Output video in MKV container instead of MP4. Currently no  tag-
                  ging supported from get_iplayer for MKV output

           --mythtv <file>
                  Create  Mythtv  streams  XML of matching programmes in specified
                  file

           --nowrite, -n
                  No writing of file to disk (use with -x to prevent a copy  being
                  stored on disk)

           --output, -o <dir>
                  Recording output directory

           --outputliveradio <dir>
                  Output directory for live radio recordings

           --outputlivetv <dir>
                  Output directory for live tv recordings

           --outputlocalfiles <dir>
                  Output directory for localfiles recordings
                  Additionally  stream  to  STDOUT  (so  you  can pipe output to a
                  player)

           --stream
                  Stream to STDOUT (so you can pipe output to a player)

           --subdir, -s
                  Put Recorded files into Programme name subdirectory

           --subdir-format <format>
                  The format to be used for the subdirectory naming using  format-
                  ting fields. e.g. '<nameshort>-<seriesnum>'

           --symlink <file>
                  Create  symlink to <file> once we have the header of the record-
                  ing

           --thumb-ext <ext>
                  Thumbnail filename extension to use

           --thumbsize <index|width>
                  Default thumbnail size/index to use for  the  current  recording
                  and metadata (see --info for thumbnailN: to get size/index)

           --thumbsizecache <index|width>
                  Default  thumbnail  size/index  to  use  when building cache and
                  index (see --info for thumbnailN: to get size/index)

           --whitespace, -w
                  Keep whitespace (and escape chars) in filenames

           --xml-alpha
                  Create freevo/Mythtv menu  sorted  alphabetically  by  programme
                  name

           --xml-channels
                  Create  freevo/Mythtv  menu  of  channels  -> programme names ->
                  episodes

           --xml-names
                  Create freevo/Mythtv menu of programme names -> episodes

       PVR Options:
           --comment <string>
                  Adds a comment to a PVR search

           --pvr [pvr search name]
                  Runs the PVR using all saved PVR searches (intended  to  be  run
                  every  hour  from cron etc). The list can be limited by adding a
                  regex to the command. Synonyms: --pvrrun, --pvr-run

           --pvr-add <search name>

           --pvr-exclude <string>
                  Exclude the PVR searches to run by search name (regex  or  comma
                  separated values). Synonyms: --pvrexclude

           --pvr-list
                  Show the PVR search list. Synonyms: --pvrlist

           --pvr-queue
                  Add  currently  matched  programmes  to  queue for later one-off
                  recording using the --pvr option. Search terms  required  unless
                  --pid specified. Use --search=.* to force download of all avail-
                  able programmes. Synonyms: --pvrqueue

           --pvr-scheduler <seconds>
                  Runs the PVR using all saved PVR searches every <seconds>.  Syn-
                  onyms: --pvrscheduler

           --pvr-single <search name>
                  Runs a named PVR search. Synonyms: --pvrsingle

       Config Options:
           --expiry, -e <secs>
                  Cache expiry in seconds (default 4hrs)

           --limit-matches <number>
                  Limits  the  number  of matching results for any search (and for
                  every PVR search)

           --localfilesdirs <dir>[,dir,]
                  Directories/Folders to scan for new files

           --nopurge
                  Don't ask to delete programmes recorded over 30 days ago

           --packagemanager <string>
                  Tell the updater that we were installed using a package  manager
                  and don't update (use either: apt,rpm,deb,yum,disable)

           --plugins-update
                  Update get_iplayer plugins to the latest

           --prefs-add
                  Add/Change specified saved user or preset options

           --prefs-clear
                  Remove *ALL* saved user or preset options

           --prefs-del
                  Remove specified saved user or preset options

           --prefs-show
           --refresh-exclude <string>
                  Exclude matched channel(s) when refreshing cache (regex or comma
                  separated values)

           --refresh-future
                  Obtain future programme schedule when refreshing cache  (between
                  7-14 days)

           --refresh-include <string>
                  Include matched channel(s) when refreshing cache (regex or comma
                  separated values)

           --skipdeleted
                  Skip the download of metadata/thumbs/subs if the media  file  no
                  longer   exists.   Use   with  --history  &  --metadataonly/sub-
                  sonly/thumbonly.

           --update, -u
                  Update get_iplayer if a newer one exists

           --webrequest <urlencoded string>
                  Specify   all   options    as    a    urlencoded    string    of
                  "name=val&name=val&..."

       External Program Options:
           --atomicparsley <path>
                  Location of AtomicParsley tagger binary

           --ffmpeg <path>
                  Location of ffmpeg binary

           --flvstreamer <path>
                  Location of flvstreamer binary

           --id3v2 <path>
                  Location of id3v2 or id3tag binary

           --lame <path>
                  Location of lame binary

           --mplayer <path>
                  Location of mplayer binary

           --vlc <path>
                  Location of vlc or cvlc binary

       Tagging Options:
           --no-tag
                  Do not tag downloaded programmes

           --tag-fulltitle
                  Use complete title (including series) instead of shorter episode
                  Tag downloaded  radio  and  tv  programmes  as  iTunes  podcasts
                  (requires MP3::Tag module for AAC/MP3 files)

           --tag-podcast-radio
                  Tag   only   downloaded  radio  programmes  as  iTunes  podcasts
                  (requires MP3::Tag module for AAC/MP3 files)

           --tag-podcast-tv
                  Tag only downloaded tv programmes as iTunes podcasts

           --tag-utf8
                  AtomicParsley accepts UTF-8 input

AUTHOR
------

           get_iplayer was written by Phil Lewis  <iplayer2  (at  sign)  linuxcen-
           tre.net>    and    is   now   maintained   by   the   contributors   at
           http://www.infradead.org/get_iplayer/html/get_iplayer.html

           This  manual  page  was  originally  written  by   Jonathan   Wiltshire
           <jmw@debian.org> for the Debian project (but may be used by others).

COPYRIGHT NOTICE
----------------

           get_iplayer v2.80, Copyright (C) 2008-2010 Phil Lewis
             This  program  comes  with  ABSOLUTELY  NO  WARRANTY; for details use
           --warranty.
             This is free software, and you are welcome to redistribute  it  under
           certain
             conditions; use --conditions for details.






    Phil Lewis                        August 2011                   GET_IPLAYER(1)

* * * * *

Man(1) output converted with
[man2html](http://www.oac.uci.edu/indiv/ehood/man2html.html)
