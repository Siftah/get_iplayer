[[getiplayer.jpg|alt=getiplayer]] lives! This project is the
continuation of Phil Lewis's excellent work on
get\_iplayer

About get\_iplayer
==================

This tool allows you to search, index and record/stream:

-   **[BBC iPlayer TV](http://www.bbc.co.uk/iplayer/tv)** - up to 3200
    kbps HD 720p H.264 / Quicktime / MP4
-   **[BBC Live TV](http://www.bbc.co.uk/iplayer/tv)** - 500 kbps H.264
    / MP4
-   **[BBC iPlayer Radio](http://www.bbc.co.uk/iplayer/radio)** - up to
    192 kbps MP3 / AAC and Realaudio
-   **[BBC Live Radio](http://www.bbc.co.uk/iplayer/radio)** - up to 192
    kbps MP3 / AAC, WMA and Realaudio
-   **[BBC Podcasts](http://www.bbc.co.uk/radio/podcasts/directory/)** -
    up to 192 kbps MP3 / AAC
-   **[BBC iPlayer TV subtitles](http://www.bbc.co.uk/iplayer/tv)** -
    SubRip / srt

Unlike the web sites above, get\_iplayer has PVR-like capabilities (like
Sky+ / TiVo / Series-Link); You can save lists of programme searches
which are automatically recorded when they become available so that you
can watch them when you choose and on devices that cannot run Adobe
Flash Player - even if you don’t have adequate broadband speeds or if
your broadband streams too slowly at peak hours when you want to watch a
programme.

The iPhone H.264 feeds from the BBC are higher quality than in the Flash
iPlayer (normal quality). See the [beebhack
wiki](http://beebhack.wikia.com/wiki/IPlayer_TV#Comparison_Table) for a
comparison. They are intended for the Apple iPhone and are consequently
difficult to download for any other OS. The same goes for the iPhone MP3
radio streams. get\_iplayer also allows recording of the high-quality
(even HD 720p) flash based content using
[rtmpdump](http://rtmpdump.mplayerhq.hu/). None of the above content is
‘protected’ by DRM. get\_iplayer cannot remove DRM.

Phil Lewis and a few others worked out how to work around these problems
and now have tools which essentially simulate an iPhone as far as the
BBC web servers are concerned.

*[get\_iplayer](http://www.infradead.org/get_iplayer.html)* does the
recording, indexing and searching of the iPlayer TV/Radio programmes and
podcasts available. It can even stream the iPlayer TV programmes while
recording them to mplayer, vlc or xine, etc.

Download
--------

Released versions of get\_iplayer can be downloaded from
[ftp://ftp.infradead.org/pub/get\_iplayer/](ftp://ftp.infradead.org/pub/get_iplayer/).
The latest version is v2.82.

The latest changes can be found in the [git](http://git-scm.com/)
version control repository, at `git://git.infradead.org/get_iplayer.git`
([browse](http://git.infradead.org/get_iplayer.git)).

Linux users should find that their distribution has a get\_iplayer
package which will automatically pull in all required dependencies
(rtmpdump, ffmpeg, etc.). Fedora users, for example, will find
get\_iplayer in the [RPM Fusion](http://www.rpmfusion.org/) repository
of packages for the "Free World". Just issue the command
'`yum install get_iplayer`'

Life is, as usual, more complex for Windows users. There is no sane
packaging system under Windows which lets software packages express
their dependencies and arrange for other software to be installed to
meet their requirements. Therefore, we have created a Windows installer
for get\_iplayer which will attempt to download and install the various
requirements. This can be obtained from:

[http://www.infradead.org/get\_iplayer\_win/get\_iplayer\_setup\_latest.exe](http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe)

Help / Development
------------------

For help using get\_iplayer, and to submit or suggest improvements,
there is a [mailing
list](http://lists.infradead.org/mailman/listinfo/get_iplayer), archived
[here](http://lists.infradead.org/pipermail/get_iplayer/) so you can see
if your question has already been answered before you post it.

When using this (or any) mailing list, please observe standard rules of
'[Netiquette](http://david.woodhou.se/email.html)' — no HTML, no
top-posting, no excessive quotations, etc.

If you submit patches for get\_iplayer, please do try to make sure they
apply cleanly to the current git tree, and that they're not mangled by
your email software. Sending the patch to yourself first, then checking
that you can save it to a file and apply it, is a useful technique.

DRM
---

get\_iplayer does not circumvent any digital rights management security
(see the [BBC’s
website](http://news.bbc.co.uk/1/hi/technology/6944830.stm) on how to do
that with the Windows-only DRM content they provide). get\_iplayer does
not circumvent any effective technological measures. The BBC does not
implement any such measures. They use RTMP which is a streaming protocol
now publicly published by Adobe. Sometimes they use RTMP ‘SWF
verification’ which has proven to be ineffective in its current BBC
implementation (flvstreamer cannot handle such verification requests so
the stream is dropped and is then automatically resumed). The iPhone
streams are also unprotected and use plain progressive download HTTP
protocol. The WMA and realaudio streams and likewise unprotected. The
BBC may at some point choose to effectively protect their streams with
DRM or some ‘effective technological measure’ in which case get\_iplayer
will no longer be a useful tool for those streams. The BBC do implement
DRM on their Adobe Air downloadable files and therefore get\_iplayer is
not useful with those. The BBC iPlayer TV only works in the UK so that
they can limit the reach of their output to UK TV Licence fee payers who
fund iPlayer (although legally you do not require a licence to watch
non-live iPlayer output).

Uses
----

The script is primarily intended for use for recording and playing back
TV and Radio content on devices that cannot support Adobe
Flash/Air/Silverlight, systems which run entirely on open-source
software (i.e. no Adobe Flash/Air or Silverlight), recording content for
mobile devices that have no access to broadband/wi-fi or running on
devices that have such limited memory that running a browser with a
flash player or AIR is not possible (or not permitted). For me this
would be an [Xbox running Xebian
Linux](http://www.xbox-linux.org/wiki/Xebian) with
[Freevo](http://freevo.org) or XBMC. The Xbox only has 64MiB of memory
and struggles enormously with Adobe flash (Adobe doesn’t permit you run
flash player or AIR on a games console either). One major use of
get\_iplayer is for those unfortunate enough to have slow broadband
speeds; get\_iplayer can pre-record the programme you wish to watch so
that you do not get the endless re-buffering that you experience with
the flash player. Some ISPs actually throttle iPlayer streaming during
peak hours. get\_iplayer can actually lessen the ISP’s (and BBC’s)
traffic load if the PVR functionality is used off-peak. Please use this
tool responsibly and don’t try to download all BBC programmes for
example. There is a built-in ‘limit matches’ option to stop get\_iplayer
doing this just in case you accidentally set it up wrongly.

Fair Use
--------

Of course, to respect the content providers’ wishes and fair-use
legislation in your jurisdiction, you should keep the recorded content
for no longer than is locally acceptable (30 days seems to be accepted
in the UK for TV video recordings for example), not attempt to obtain it
from outside of the UK and not redistribute it. get\_iplayer is not
intended for use in making illegal copies of copyrighted content. Please
respect the rights of the content owners when recording. get\_iplayer
will attempt to remove its recorded content which is more than 30 days
old. Podcasts and certain radio programmes can be kept for longer but
you must investigate this on a case-by-case basis.

Features
--------

-   Recording/Streaming of TV, Radio and Podcasts from BBC sites
-   Recording/Streaming of Live BBC iPlayer TV & Radio
-   Recording/Streaming of Embedded media in BBC Learning Zone, Archive
    and News sites
-   PVR functionality allows predefined searches to be recorded from a
    scheduler such as cron or Windows scheduler
-   Queuing of programmes for batched recording or for recording
    off-peak
-   Resume recordings of partially recorded content
-   Stream iPlayer or podcast content via mplayer or xine while
    recording it
-   Allow multiple programmes to be recorded in one command
-   Indexing of all available programmes
-   Script update capability
-   Advanced Searching on programme name, episode, description, channel
    or category, etc
-   Limit search by programmes made available after a specific number of
    hours
-   Removal of recorded content which is more than 30 days old
-   Meta-tagging of recorded iPlayer iPhone/H.264 and mp3 files for
    importing into iTunes
-   Plug-in based architecture to allow new channels and sites to be
    added by 3rd-parties

Reported to Work on:
--------------------

It has been tested by users under Linux (Fedora, Centos/RHEL, Ubuntu,
Debian, OpenSuSE, OLPC, ArchLinux, Puppy, NSLU2), MacOSX, iPhone and
Windows XP/VIsta/7 (Cygwin, Strawberry Perl)

* * * * *

David Woodhouse \<[dwmw2@infradead.org](mailto:dwmw2@infradead.org)\>

Last modified: Sun Jan 9 16:18:39 GMT 2011
