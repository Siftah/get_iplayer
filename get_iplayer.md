![getiplayer](getiplayer.jpg) lives! This project is the continuation of
Phil Lewis's excellent work on `get_iplayer`.

## About `get_iplayer`

`get_iplayer` allows you to
search, index and record/stream:

-   **[BBC iPlayer TV](http://www.bbc.co.uk/iplayer/tv)** - up to 3200 kbps HD 720p H.264 / MP4
-   **[BBC Live TV](http://www.bbc.co.uk/iplayer/tv)** - up to 1500 kbps H.264 / MP4
-   **[BBC iPlayer Radio](http://www.bbc.co.uk/iplayer/radio)** - up to 320 kbps MP3 / AAC
-   **[BBC Live Radio](http://www.bbc.co.uk/iplayer/radio)** - up to 320 kbps MP3 / AAC / WMA
-   **[BBC Podcasts](http://www.bbc.co.uk/podcasts)** - up to 192 kbps MP3 / AAC
-   **[BBC iPlayer TV subtitles](http://www.bbc.co.uk/iplayer/tv)** - SubRip / srt

`get_iplayer` does the recording, indexing and searching of the iPlayer TV/Radio
programmes and podcasts available. It can even stream the iPlayer TV programmes
while recording them to mplayer, vlc or xine, etc.  

`get_iplayer` can access feeds from the BBC that are higher quality than those
used in the Flash iPlayer (normal quality). See the [beebhack wiki]
(http://beebhack.wikia.com/wiki/IPlayer_TV#Comparison_Table) for a
comparison. `get_iplayer` also allows recording of the high-quality
(HD 720p) Flash-based TV content using [rtmpdump](http://rtmpdump.mplayerhq.hu/).
None of the above content is ‘protected’ by DRM. `get_iplayer` cannot remove DRM.

`get_iplayer` also has PVR-like capabilities (like
Sky+ / TiVo / Series-Link). You can save lists of programme searches
which are automatically recorded when they become available so that you
can watch them when you choose and on devices that cannot run Adobe
Flash Player - even if you don’t have adequate broadband speeds or if
your broadband streams too slowly at peak hours when you want to watch a
programme.

## Obtaining `get_iplayer`

Full source code for released versions of `get_iplayer` can be downloaded from
[ftp://ftp.infradead.org/pub/get_iplayer/](ftp://ftp.infradead.org/pub/get_iplayer/).
The latest version is v2.82.

The latest changes can be found in the [Git](http://git-scm.com/)
version control repository, at `git://git.infradead.org/get_iplayer.git`
([browse](http://git.infradead.org/get_iplayer.git)).

We have created a Windows installer for `get_iplayer` which will attempt to download
and install the various requirements. This can be obtained from:

[http://www.infradead.org/get\_iplayer\_win/get\_iplayer\_setup\_latest.exe](http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe)

Linux/Unix/OSX users can find more information **[[here|installation]]**.

## Help

For help using `get_iplayer`, and to submit or suggest improvements,
there is a [mailing list](http://lists.infradead.org/mailman/listinfo/get_iplayer),
with a browsable archive **[here](http://lists.infradead.org/pipermail/get_iplayer/)**
and a searchable archive **[here](http://www.mail-archive.com/get_iplayer@lists.infradead.org/)**:

Check a mailing list archive so you can see if your question has already been
answered before you post it.

When using this (or any) mailing list, please observe standard rules of
'[Netiquette](http://david.woodhou.se/email.html)' — no HTML, no
top-posting, no excessive quotations, etc.

## Contributing

If you submit patches for `get_iplayer`, make sure they
apply cleanly to the current git tree, and that they're not mangled by
your email software. Sending the patch to yourself first, then checking
that you can save it to a file and apply it, is a useful technique.

## Uses

The script is primarily intended for use for recording and playing back
TV and Radio content on devices that cannot support Adobe
Flash/Air/Silverlight, systems which run entirely on open-source
software (i.e. no Adobe Flash/Air or Silverlight), recording content for
mobile devices that have no access to broadband/wi-fi or running on
devices that have such limited memory that running a browser with a
Flash player or AIR is not possible (or not permitted). One major use of
`get_iplayer` is for those unfortunate enough to have slow broadband
speeds; `get_iplayer` can pre-record the programme you wish to watch so
that you do not get the endless re-buffering that you experience with
the flash player. Some ISPs actually throttle iPlayer streaming during
peak hours. `get_iplayer` can actually lessen the ISP’s (and BBC’s)
traffic load if the PVR functionality is used off-peak. Please use this
tool responsibly and don’t try to download all BBC programmes for
example. There is a built-in ‘limit matches’ option to stop `get_iplayer`
doing this just in case you accidentally set it up wrongly.

## DRM

`get_iplayer` does not circumvent any digital rights management security. 
`get_iplayer` does not circumvent any effective technological measures. The BBC
does not implement any such measures. They use RTMP which is a streaming protocol
now publicly published by Adobe. Sometimes they use RTMP ‘SWF
verification’ which has proven to be ineffective in its current BBC
implementation.  The BBC may at some point choose to effectively protect their
streams with DRM or some ‘effective technological measure’ in which case `get_iplayer`
will no longer be a useful tool for those streams. The BBC do implement
DRM on their Adobe Air downloadable files and therefore `get_iplayer` is
not useful with those. The BBC iPlayer TV only works in the UK so that
they can limit the reach of their output to the UK TV Licence fee payers who
fund iPlayer (although legally you do not require a licence to watch
non-live iPlayer output).

## Fair Use

Of course, to respect the content providers’ wishes and fair-use
legislation in your jurisdiction, you should keep the recorded content
for no longer than is locally acceptable (30 days seems to be accepted
in the UK for TV video recordings for example), not attempt to obtain it
from outside of the UK and not redistribute it. `get_iplayer` is not
intended for use in making illegal copies of copyrighted content. Please
respect the rights of the content owners when recording. `get_iplayer`
will attempt to remove its recorded content which is more than 30 days
old. Podcasts and certain radio programmes can be kept for longer but
you must investigate this on a case-by-case basis.

## Features

-   Recording/Streaming of TV, Radio and Podcasts from BBC sites
-   Recording/Streaming of Live BBC iPlayer TV & Radio
-   Recording/Streaming of Embedded media in BBC Learning Zone, Archive and News sites
-   PVR functionality allows predefined searches to be recorded from a scheduler such as cron or Windows scheduler
-   Queuing of programmes for batched recording or for recording off-peak
-   Resume recordings of partially recorded content
-   Stream iPlayer or podcast content via mplayer or xine while recording it
-   Allow multiple programmes to be recorded in one command
-   Indexing of all available programmes
-   Script update capability
-   Advanced Searching on programme name, episode, description, channel or category, etc
-   Limit search by programmes made available after a specific number of hours
-   Removal of recorded content which is more than 30 days old
-   Metadata tagging of recorded iPlayer MP4, M4A and MP3 files for importing into iTunes
-   Plug-in based architecture to allow new channels and sites to be added by 3rd-parties

## Supported Platforms

`get_iplayer` has been tested by users on Linux/Unix (numerous flavours), OS X (10.5+) and Windows (XP/Vista/7/8).
