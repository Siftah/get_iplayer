# Installation

<a name="Requirements"></a>
## Requirements

`get_iplayer` runs on Linux/Unix (numerous flavours), OS X (10.5+) and Windows (XP/Vista/7/8).

-   Perl (required)
-   LWP (libwww-perl) (required)
-   For Flash audio/video downloads you will need
    [rtmpdump](http://rtmpdump.mplayerhq.hu/) and
    optionally [ffmpeg](http://ffmpeg.org) (to
    convert flv files to mp4, m4a, mp3 or avi format)
-   For WMA Radio, [mplayer](http://www.mplayerhq.hu) is required.

Full information about external program requirements can be found [below](#External%20Program%20Requirements).

<a name="Linux"></a>
## Linux/Unix

### Manual Installation

Download the current release version using:

    wget http://www.infradead.org/get_iplayer/latest/get_iplayer
    
    chmod 755 get_iplayer

### Debian

TBD

### Ubuntu

TBD

### openSUSE

TBD

### OpenBSD

TBD

<a name="Windows"></a>
## Windows

<a name="Windows-Installer"></a>
### Installer

Download the latest windows installer from
[here](http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe).

Start the installer and follow the wizard in the usual manner. The
installer will (optionally) download and install the Windows support
programs: FFmpeg, rtmpdump, VLC Media Player, AtomicParsley, MPlayer, and lame.
The installer version of `get_iplayer` uses [Strawberry Perl](http://strawberryperl.com/).

To use `get_iplayer` go to the Start menu and select Get iPlayer from the **get_iplayer** submenu.
Alternatively, start the [][Web PVR Manager|webpvr]] from the start menu. Recorded programmes,
by default, can be found in the `iPlayer Recordings` folder on your Windows desktop.

Credit goes to Simon Dible for creating the original [NSIS](http://nsis.sourceforge.net/Main_Page) installer.

<a name="Windows-Cygwin"></a>
### Cygwin

Download and install [cygwin](http://cygwin.com/setup.exe).  Make sure you
install libwww-perl (LWP) along with the default packages.

Download the current release version in the cygwin shell:

    wget http://linuxcentre.net/get_iplayer/get_iplayer
    chmod 755 get_iplayer
    ./get_iplayer

<a name="OSX"></a>
## OS X

#### Manual Installation

Download the current release version using:

    curl http://www.infradead.org/get_iplayer/latest/get_iplayer -o get_iplayer
    chmod 755 get_iplayer

#### Support Binaries

TBD

#### Homebrew

TBD

<a name="External Program Requirements"></a>
## External Program Requirements

### Download Modes, Output Formats and External Programs Required

|Type|Mode|Format|rtmpdump|ffmpeg|mplayer|atomicparsley|id3v2|
|----|----|------|--------|------|-------|-------------|-----|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>&#160;|mp4<br/>mp4<br/>mp4<br/>mp4<br/>avi<br/>mp4<br/>(h264/aac)|Yes|Yes|-|Optional|-|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --raw)|flv<br/>(h264/aac)|Yes|-|-|-|-|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --mkv)|mkv<br/>(h264/aac)|Yes|Yes|-|-|-|
|Radio|flashaudio|mp3|Yes|-|Yes|-|Optional|
|Radio|flashaudio<br/>(with --raw)|flv<br/>(mp3)|Yes|-|-|-|-|
|Radio|flashaac|m4a<br/>(aac)|Yes|Yes|-|Optional|-|
|Radio|flashaac<br/>(with --raw)|flv<br/>(aac)|Yes|-|-|-|-|
|Radio|flashaac<br/>(with --aactomp3)|mp3|Yes|Yes|-|-|Optional|
|Radio|wma|wma|-|-|Yes|-|-|
|Podcast|podcast|mp3|-|-|-|-|Optional|
