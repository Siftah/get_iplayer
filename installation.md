# get_iplayer Installation

[[_TOC_]]

<a name="Requirements"></a>
## Requirements

get_iplayer runs on Linux/Unix (numerous flavours), OS X (10.5+) and Windows (XP/Vista/7/8).

- Perl with LWP module is required.  
- For Flash audio/video you will need [rtmpdump](http://rtmpdump.mplayerhq.hu/) to save downloads to FLV files.
- For WMA audio you will need [mplayer](http://www.mplayerhq.hu) to save downloads to WMA files.
- For BBC TV and national radio you will need [ffmpeg](http://ffmpeg.org) to convert FLV files to MP4, M4A, MP3, or AVI format.
- For BBC regional and local radio you will need [mplayer](http://www.mplayerhq.hu) to convert FLV files to MP3 format.
- For metadata tagging of MP4 and M4A files you will need [AtomicParsley](http://atomicparsley.sourceforge.net).
- For metadata tagging of MP3 files you may use [id3v2](http://id3v2.sourceforge.net).  However, the optional MP3::Tag Perl module is preferred since it supports more complete ID3 tagging.

More information about external program requirements can be found [below](#External Program Requirements).

#### Optional Perl Modules

Optional Perl modules may be installed for added functionality:

* MP3::Info - Required for *localfiles* plugin
* MP3::Tag - Full ID3 tagging of MP3 files
* Net::SMTP::SSL and Authen::SASL - SSL secure email (e.g. Yahoo Mail)
* Net::SMTP::TLS::ButMaintained - TLS secure email (e.g., GMail)
* XML::Simple - Parsing of [BBC RDF metadata](http://www.bbc.co.uk/ontologies/programmes/2009-09-07.shtml) for extraction of media links from BBC brand pages and programme microsites. Supports --pid-recursive option.

<a name="Linux/Unix"></a>
## Linux/Unix

<a name="Linux/Unix Manual"></a>
### Manual Installation

#### Support Applications

WIP

#### Main Script

Download the latest release version:

    $ wget --no-check-certificate https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer

Ensure the script is executable:

    $ chmod 755 ./get_iplayer

Execute the script once to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    $ ./get_iplayer

Optionally install somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install ./get_iplayer /usr/local/bin

Run script (assumed installed in $PATH):

	$ get_iplayer ...

#### Web PVR

Download the latest release version:

    $ wget --no-check-certificate https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer.cgi

Ensure the script is executable:

    $ chmod 755 ./get_iplayer.cgi

Optionally install somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install ./get_iplayer.cgi /usr/local/bin

Launch standalone Web PVR (assumed installed in $PATH):

	$ get_iplayer.cgi -l 127.0.0.1 -p 1935

If get_iplayer main script is not in $PATH, location must be explicitly set:

	$ get_iplayer.cgi -l 127.0.0.1 -p 1935 -g /path/to/get_iplayer

Once Web PVR is running, connect to it by opening this URL in your browser:

<http://127.0.0.1:1935>

### Package Manager Installation

Some Linux/Unix distributions have get_iplayer packaged in their software repositories.  These packages are installed using the package manager provided with your distro.  Installing a packaged version of get_iplayer will automatically install other required applications and libraries.  Optional support applications may also be installed separately using the package manager.

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

<a name="OSX Manual"></a>
### Manual Installation

#### Support Applications

WIP

#### Main Script

Download the latest release version:

    $ curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer

Ensure the script is executable:

    $ chmod 755 ./get_iplayer

Execute the script once with no arguments to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    $ ./get_iplayer

Optionally install the script somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install ./get_iplayer /usr/local/bin

#### Web PVR

Download the latest release version:

    $ curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer.cgi

Ensure the script is executable:

    $ chmod 755 ./get_iplayer.cgi

Optionally install somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install ./get_iplayer.cgi /usr/local/bin

Launch standalone Web PVR (assumed installed in $PATH):

	$ get_iplayer.cgi -l 127.0.0.1 -p 1935

If get_iplayer main script is not in $PATH, location must be explicitly set:

	$ get_iplayer.cgi -l 127.0.0.1 -p 1935 -g /path/to/get_iplayer

Once Web PVR is running, connect to it by opening this URL in your browser:

<http://127.0.0.1:1935>

<a name="OSX Homebrew"></a>
### Homebrew

WIP

<a name="Windows"></a>
## Windows

<a name="Windows Installer"></a>
### Installer

Download the latest Windows installer from:

<http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe>

Start the installer and follow the wizard in the usual manner. The installer will (optionally) download and install the Windows support programs: FFmpeg, rtmpdump, VLC Media Player, AtomicParsley, MPlayer, and lame. The Windows installer version of get_iplayer uses [Strawberry Perl](http://strawberryperl.com/).

To use get_iplayer go to the Start menu and select **Get_iPlayer** from the **get_iplayer** submenu. Alternatively, start the [[Web PVR Manager|webpvr]] from the start menu. Recorded programmes, by default, can be found in the **iPlayer Recordings** folder on your Windows desktop.

<a name="Windows Cygwin"></a>
### Cygwin

Download and install [Cygwin](http://cygwin.com/setup.exe).  Make sure you install libwww-perl (LWP) along with the default packages.  Then, in Cygwin shell:

WIP

<a name="External Program Requirements"></a>
## External Program Requirements

### Download Modes, Output Formats and External Programs Required

The table below shows the external programmes required to download and - if applicable - convert and tag files produced from each combination of recording mode and output format used by get_iplayer.

|Type|Mode|Format|rtmpdump|ffmpeg|mplayer|atomicparsley|id3v2|
|----|----|------|--------|------|-------|-------------|-----|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>&#160;|mp4<br/>mp4<br/>mp4<br/>mp4<br/>avi<br/>mp4<br/>(h264/aac)|X|X||X||
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --raw)|flv<br/>(h264/aac)|X|||||
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --mkv)|mkv<br/>(h264/aac)|X|X||||
|Radio|flashaudio|mp3|X||X||X|
|Radio|flashaudio<br/>(with --raw)|flv<br/>(mp3)|X|||||
|Radio|flashaac|m4a<br/>(aac)|X|X||X||
|Radio|flashaac<br/>(with --raw)|flv<br/>(aac)|X|||||
|Radio|flashaac<br/>(with --aactomp3)|mp3|X|X|||X|
|Radio|wma|wma|||X|||
|Podcast|podcast|mp3||||||
