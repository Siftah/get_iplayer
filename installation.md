## get_iplayer Installation

### Oh-So-Important Note:

**If the version of get_iplayer you are about to install was released before 2013-06-06, please do not install it.  It is broken due to changes by the BBC. All releases of get_iplayer 2.83 or higher are fixed, and most package versions of get_iplayer 2.82 have been fixed.  Check the information for your release.  If you must continue using get_iplayer 2.82 released before 2013-06-06, see [this page|swfurl) for instructions on how to adjust your get_iplayer settings to restore downloads.**

## Table of Contents

- Requirements
	- [Perl Support](#requirements-perl)
	- [External Programs](#requirements-programs)
- Linux/Unix
    - [[Manual Installation|manual]]
    - Package Installation
        - [[Debian|debian]]
        - [[Ubuntu|ubuntu]]
        - [[Raspbian / Raspberry Pi|raspbian]]
        - [[openSUSE|opensuse]]
        - [[Arch Linux|arch]]
        - [[OpenBSD|openbsd]]
        - [[FreeBSD / PC-BSD|freebsd]]
- OS X
    * [[Homebrew|osxhomebrew]]
    * [[MacPorts|osxmacports]]
    * [[Manual Installation|osxmanual]]
- Windows
    * [[Installer|winsetup]]
    * [[Manual Installation|winmanual]]
- Git HEAD
    - [[Using Git (all platforms)|githeadgit]]
    - [[Linux/Unix/OS X|githeadunix]]
    - [[Windows|githeadwin]]
- Miscellaneous
	- [[Perlbrew|perlbrew]]

<a name="requirements"></a>
## Requirements

get_iplayer runs on Linux/Unix (numerous flavours supported), OS X (10.5+) or Windows (XP/Vista/7/8).

<a name="requirements-perl"></a>
### Perl Support

* Perl 5.8.8+ is required

One Perl module (with dependencies) is required for get_iplayer:

* LWP - Required for HTTP access to BBC servers

Other Perl modules are recommended for added functionality:

* MP3::Info - Catalogue MP3 files in *localfiles* plugin
* MP3::Tag - Full ID3 tagging of MP3 files
* Net::SMTP::SSL and Authen::SASL - Send search results via SSL secure email (e.g. GMail, Yahoo Mail)
* Net::SMTP::TLS::ButMaintained (preferred) or Net::SMTP::TLS - Send search results via TLS secure email (e.g., GMail, iCloud)
* XML::Simple - Parse [BBC RDF metadata](http://www.bbc.co.uk/ontologies/programmes/2009-09-07.shtml) to extract media links from BBC brand pages and programme sites. Supports --pid-recursive option.

<a name="requirements-programs"></a>
### External Programs

get_iplayer employs external programs to download streams and manipulate media files:

- [rtmpdump](http://rtmpdump.mplayerhq.hu/) - Saves Flash audio/video streams to FLV files.
- [ffmpeg](http://ffmpeg.org) - Converts FLV files to MP4, M4A, MP3, or AVI format (for BBC TV, BBC national radio and BBC webcams).
- [mplayer](http://www.mplayerhq.hu) - Converts FLV files to MP3 format (for BBC regional and local radio). Also saves Windows Media audio streams to WMA files (for BBC radio).
- [AtomicParsley](http://atomicparsley.sourceforge.net) - Metadata tagging for MP4 and M4A files.
- [id3v2](http://id3v2.sourceforge.net) - Metadata tagging for MP3 files. However, the MP3::Tag Perl module is preferred because it supports more complete ID3 tagging.

Details of how external programs are used can be found [[here|modes#external-programs]].
