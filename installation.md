# Installation

<a name="Requirements"></a>
## Requirements

get_iplayer runs on Linux/Unix (numerous flavours), OS X (10.5+) and Windows (XP/Vista/7/8).

-   Perl with LWP module is required
-   For Flash audio/video you will need [rtmpdump](http://rtmpdump.mplayerhq.hu/) to save downloads to flv files
-   For BBC TV and national radio you will need [ffmpeg](http://ffmpeg.org) to convert flv files to mp4, m4a, mp3 or avi format
-   For BBC regional and local radio you will need [mplayer](http://www.mplayerhq.hu) to convert flv files to mp3 format
-   For WMA audio you will need [mplayer](http://www.mplayerhq.hu) to save downloads to wma files

More information about external program requirements can be found [below](#External%20Program%20Requirements).

<a name="Linux"></a>
## Linux/Unix

### Manual Installation

Download the current release version:

    $ wget http://www.infradead.org/get_iplayer/latest/get_iplayer

Ensure the script is executable:

    $ chmod 755 get_iplayer

Execute the script once to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    $ ./get_iplayer

Install the script somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo mv ./get_iplayer /usr/local/bin

#### Support Applications

WIP

### Package Manager Installation

Some Linux/Unix distributions have get_iplayer packaged in their software repositories.  These packages are installed using the package manager (e.g., apt-get) provided with your distro.  Installing a packaged version of get_iplayer will automatically install other required applications and libraries.  Optional support applications may also be installed using the package manager.

Linux/Unix distros known to have up-to-date get_iplayer packages are listed below.  If get_iplayer is not packaged for your distro, use the manual installation instructions.

#### Debian

WIP

#### Ubuntu

WIP

#### openSUSE

WIP

#### OpenBSD

WIP

<a name="OSX"></a>
## OS X

#### Manual Installation

Download the current release version:

    $ curl -O http://www.infradead.org/get_iplayer/latest/get_iplayer

Ensure the script is executable:

    $ chmod 755 get_iplayer

Execute the script once to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    $ ./get_iplayer

Install the script somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo mv ./get_iplayer /usr/local/bin

#### Support Applications

WIP

#### Homebrew

WIP

<a name="Windows"></a>
## Windows

<a name="Windows-Installer"></a>
### Installer

Download the latest Windows installer from:

<http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe>

Start the installer and follow the wizard in the usual manner. The installer will (optionally) download and install the Windows support programs: FFmpeg, rtmpdump, VLC Media Player, AtomicParsley, MPlayer, and lame. The Windows installer version of get_iplayer uses [Strawberry Perl](http://strawberryperl.com/).

To use get_iplayer go to the Start menu and select **Get_iPlayer** from the **get_iplayer** submenu. Alternatively, start the [[Web PVR Manager|webpvr]] from the start menu. Recorded programmes, by default, can be found in the **iPlayer Recordings** folder on your Windows desktop.

<a name="Windows-Cygwin"></a>
### Cygwin

Download and install [Cygwin](http://cygwin.com/setup.exe).  Make sure you install libwww-perl (LWP) along with the default packages.  Then, in Cygwin shell:

Download the current release version:

    $ wget http://www.infradead.org/get_iplayer/latest/get_iplayer

Ensure the script is executable:

    $ chmod 755 get_iplayer

Execute the script once to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    $ ./get_iplayer

Install the script somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo mv ./get_iplayer /usr/local/bin


<a name="External Program Requirements"></a>
## External Program Requirements

### Download Modes, Output Formats and External Programs Required

|Type|Mode|Format|rtmpdump|ffmpeg|mplayer|atomicparsley|id3v2|
|----|----|------|--------|------|-------|-------------|-----|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>&#160;|mp4<br/>mp4<br/>mp4<br/>mp4<br/>avi<br/>mp4<br/>(h264/aac)|Required|Required|-|Optional|-|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --raw)|flv<br/>(h264/aac)|Required|-|-|-|-|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --mkv)|mkv<br/>(h264/aac)|Required|Required|-|-|-|
|Radio|flashaudio|mp3|Required|-|Required|-|Optional|
|Radio|flashaudio<br/>(with --raw)|flv<br/>(mp3)|Required|-|-|-|-|
|Radio|flashaac|m4a<br/>(aac)|Required|Required|-|Optional|-|
|Radio|flashaac<br/>(with --raw)|flv<br/>(aac)|Required|-|-|-|-|
|Radio|flashaac<br/>(with --aactomp3)|mp3|Required|Required|-|-|Optional|
|Radio|wma|wma|-|-|Required|-|-|
|Podcast|podcast|mp3|-|-|-|-|Optional|
