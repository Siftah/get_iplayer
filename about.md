![getiplayer](getiplayer.jpg) lives! This project is the continuation of
[Phil Lewis](http://linuxcentre.net/getiplayer)'s excellent work on get_iplayer.

## Introduction

get_iplayer allows you to search, index and record/stream:

-   **[BBC iPlayer TV](http://www.bbc.co.uk/iplayer/tv)** - up to 2800 kbps HD 720p H.264 + AAC
-   **[BBC Live TV](http://www.bbc.co.uk/iplayer/tv)** - up to 1500 kbps H.264 + AAC
-   **[BBC iPlayer Radio](http://www.bbc.co.uk/iplayer/radio)** - up to 320 kbps MP3 / AAC / WMA
-   **[BBC Live Radio](http://www.bbc.co.uk/iplayer/radio)** - up to 320 kbps MP3 / AAC / WMA
-   **[BBC Podcasts](http://www.bbc.co.uk/podcasts)** - up to 192 kbps MP3 / AAC
-   **[BBC iPlayer TV subtitles](http://www.bbc.co.uk/iplayer/tv)** - SubRip (srt)

get_iplayer indexes, searches and records/streams the iPlayer TV/Radio
programmes and podcasts available. It can also stream iPlayer TV/Radio programmes
while recording them to mplayer, vlc or xine, etc.  

get_iplayer can access feeds from the BBC that are higher quality than those
used in the iPlayer web site Flash player. See the [beebhack wiki](http://beebhack.wikia.com/wiki/IPlayer_TV#Comparison_Table) for a comparison. get_iplayer also supports recording of the high-quality (HD 720p) Flash-based TV content using 
[rtmpdump](http://rtmpdump.mplayerhq.hu/). None of the above content is "protected" by DRM. get_iplayer cannot remove DRM.

get_iplayer also has PVR-like capabilities (like
Sky+ / TiVo / Series-Link). You can save lists of programme searches
which are automatically recorded when they become available so that you
can watch them when you choose and on devices that cannot run Adobe
Flash Player - even if you don’t have adequate broadband speeds or if
your broadband streams too slowly at peak hours when you want to watch a
programme.

## Features

-   Recording/Streaming of TV, Radio and Podcasts from BBC sites
-   Recording/Streaming of Live BBC iPlayer TV & Radio
-   Recording/Streaming of Embedded media in BBC Learning Zone, Archive and News sites
-   PVR functionality allows predefined searches to be recorded from a scheduler such as cron or Windows scheduler
-   Queuing of programmes for batched recording or for recording off-peak
-   Resume recordings of partially recorded content
-   Stream iPlayer or podcast content via mplayer, vlc or xine while recording it
-   Allow multiple programmes to be recorded in one command
-   Indexing of all available programmes
-   Advanced Searching on programme name, episode, description, channel or category, etc
-   Limit search by programmes made available after a specific number of hours
-   Removal of recorded content which is more than 30 days old
-   Metadata tagging of recorded iPlayer MP4, M4A and MP3 files for importing into iTunes
-   Plug-in based architecture to allow new channels and sites to be added by 3rd-parties

## Installation

get_iplayer runs on Linux/Unix (numerous flavours), OS X (10.5+) and Windows (XP/Vista/7/8).

There is a Windows installer for get_iplayer which will download
and install necessary dependencies. The installer can be found at:

<http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe>

More installation information can be found **[[here|installation]]**.

## Help

For help using get_iplayer, and to submit or suggest improvements,
there is a [mailing list](http://lists.infradead.org/mailman/listinfo/get_iplayer),
with a browsable archive **[here](http://lists.infradead.org/pipermail/get_iplayer/)**
and a searchable archive **[here](http://www.mail-archive.com/get_iplayer@lists.infradead.org/)**.
Check a mailing list archive so you can see if your question has already been
answered before you post it.

When using this (or any) mailing list, please observe standard rules of
'[Netiquette](http://david.woodhou.se/email.html)' — no HTML, no
top-posting, no excessive quotations, etc.

## Uses

The script is primarily intended for use for recording and playing back
TV and Radio content on devices that cannot support Adobe
Flash/Air/Silverlight, systems which run entirely on open-source
software (i.e. no Adobe Flash/Air or Silverlight), recording content for
mobile devices that have no access to broadband/wi-fi or running on
devices that have such limited memory that running a browser with a
Flash player or AIR is not possible (or not permitted). One major use of
get_iplayer is for those unfortunate enough to have slow broadband
speeds; get_iplayer can pre-record the programme you wish to watch so
that you do not get the endless re-buffering that you experience with
the flash player. Some ISPs actually throttle iPlayer streaming during
peak hours. get_iplayer can actually lessen the ISP’s (and BBC’s)
traffic load if the PVR functionality is used off-peak. Please use this
tool responsibly and don’t try to download all BBC programmes for
example. There is a built-in 'limit matches' option to stop get_iplayer
doing this just in case you accidentally set it up wrongly.

## DRM

get_iplayer does not circumvent any digital rights management security. 
get_iplayer does not circumvent any effective technological measures. The BBC
does not implement any such measures. They use RTMP which is a streaming protocol
now publicly published by Adobe. Sometimes they use RTMP ‘SWF
verification’ which has proven to be ineffective in its current BBC
implementation.  The BBC may at some point choose to effectively protect their
streams with DRM or some ‘effective technological measure’ in which case get_iplayer
will no longer be a useful tool for those streams. The BBC do implement
DRM on their Adobe Air downloadable files and therefore get_iplayer is
not useful with those. The BBC iPlayer TV only works in the UK so that
they can limit the reach of their output to the UK TV Licence fee payers who
fund iPlayer (although legally you do not require a licence to watch
non-live iPlayer output).

## Fair Use

Of course, to respect the content providers’ wishes and fair-use
legislation in your jurisdiction, you should keep the recorded content
for no longer than is locally acceptable (30 days seems to be accepted
in the UK for TV video recordings for example), not attempt to obtain it
from outside of the UK and not redistribute it. get_iplayer is not
intended for use in making illegal copies of copyrighted content. Please
respect the rights of the content owners when recording. get_iplayer
will attempt to remove its recorded content which is more than 30 days
old. Podcasts and certain radio programmes can be kept for longer but
you must investigate this on a case-by-case basis.

