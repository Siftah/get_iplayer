# get_iplayer Installation

# Table of Contents

* [Requirements](#requirements)
* [Linux/Unix](#linux-unix)
	* [Manual Installation](#linux-unix-manual)
	* [Package Manager Installation](#linux-unix-package)
		* [Debian](#linux-unix-package-debian)
		* [Ubuntu](#linux-unix-package-ubuntu)
		* [openSUSE](#linux-unix-package-opensuse)
		* [OpenBSD](#linux-unix-package-openbsd)
* [OS X](#osx)
	* [Manual Installation](#osx-manual)
	* [Homebrew Installation](#osx-homebrew)
* [Windows](#windows)
	* [Installer](#windows-installer)
	* [Cygwin](#windows-cygwin)
* [External Program Requirements](#external-program-requirements)

<a name="requirements"></a>
## Requirements

### Platform

get_iplayer runs on Linux/Unix (numerous flavours), OS X (10.5+) and Windows (XP/Vista/7/8).

- Perl with LWP module is required.  

### External Programs

- For Flash audio/video you will need [rtmpdump](http://rtmpdump.mplayerhq.hu/) to save downloads to FLV files.
- For WMA audio you will need [mplayer](http://www.mplayerhq.hu) to save downloads to WMA files.
- For BBC TV and national radio you will need [ffmpeg](http://ffmpeg.org) to convert FLV files to MP4, M4A, MP3, or AVI format.
- For BBC regional and local radio you will need [mplayer](http://www.mplayerhq.hu) to convert FLV files to MP3 format.
- For metadata tagging of MP4 and M4A files you will need [AtomicParsley](http://atomicparsley.sourceforge.net).
- For metadata tagging of MP3 files you may use [id3v2](http://id3v2.sourceforge.net).  However, the optional MP3::Tag Perl module is preferred since it supports more complete ID3 tagging.

More information about external program requirements can be found [below](#external-program-requirements).

### Optional Perl Modules

Optional Perl modules may be installed for added functionality:

* MP3::Info - Required for *localfiles* plugin
* MP3::Tag - Full ID3 tagging of MP3 files
* Net::SMTP::SSL and Authen::SASL - SSL secure email (e.g. Yahoo Mail)
* Net::SMTP::TLS::ButMaintained or Net::SMTP::TLS - TLS secure email (e.g., GMail)
* XML::Simple - Parsing of [BBC RDF metadata](http://www.bbc.co.uk/ontologies/programmes/2009-09-07.shtml) for extraction of media links from BBC brand pages and programme microsites. Supports --pid-recursive option.

More information about installing optional Perl modules can be found [below](#optional-perl-modules).

<a name="linux-unix"></a>
## Linux/Unix

<a name="linux-unix-manual"></a>
### Manual Installation

#### External Programs

TODO

#### Command-line Interface (CLI)

1. Download the latest release version to working directory:

    $ wget --no-check-certificate https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer

2. Ensure the script is executable:

    $ chmod 755 ./get_iplayer

3. Execute the script once to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    $ ./get_iplayer

4. Optionally install get_iplayer somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install -m 755 ./get_iplayer /usr/local/bin

5. Run CLI (assumed installed in $PATH):

	$ get_iplayer […]

#### Web PVR Manager (WPM)

1. Download the latest release version:

    $ wget --no-check-certificate https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer.cgi

2. Ensure the script is executable:

    $ chmod 755 ./get_iplayer.cgi

3. Optionally install get_iplayer.cgi somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install -m 755 ./get_iplayer.cgi /usr/local/bin

4. Launch WPM (assumed installed in $PATH):

	$ get_iplayer.cgi --listen 127.0.0.1 --port 1935

5. If CLI is not in $PATH, its location must be explicitly set:

	$ get_iplayer.cgi --listen 127.0.0.1 --port 1935 --getiplayer /path/to/get_iplayer

6. Once the WPM is running, connect to it by opening this URL in your browser:

	<http://127.0.0.1:1935>

7. Stop the WPM by typing Ctrl-C.

<a name="linux-unix-package"></a>
### Package Manager Installation

Some Linux/Unix distributions maintain get_iplayer packages in their software repositories.  These packages are installed using the package manager provided with your Linux/Unix distribution.  Installing a packaged version of get_iplayer will automatically install other required applications and libraries.  Optional support applications may also be installed separately using the package manager.

Instructions Linux/Unix distributions known to have up-to-date get_iplayer packages are given below.  If get_iplayer is not packaged for your system, use the manual installation instructions above.

<a name="linux-unix-package-debian"></a>
#### Debian

##### Command-line Interface (CLI)

###### Debian 7 (stable, wheezy)

1. Install get_iplayer package (note that package name contains hyphen, not underscore):

	$ sudo apt-get install get-iplayer

2. Install suggested packages for MP4/M4A/MP3 output and full MP3 tagging:

	$ sudo apt-get install ffmpeg mplayer libmp3-tag-perl

3. Optionally install packages for secure email support:

	$ suto apt-get libnet-smtp-ssl-perl libauthen-sasl-perl libnet-smtp-tls-butmaintained-perl

If you should ever need or want to update to a newer get-iplayer package from Debian testing, you can download and install the package directly.  Although installing packages from testing on a stable system is generally discouraged, it is currently safe to do so with the get-iplayer package.

1. Download the Debian testing get-iplayer package from your preferred mirror:

	<http://packages.debian.org/testing/all/get-iplayer/download>

2. Install the downloaded DEB file (version 2.83-1 in this example):

	$ sudo gdebi get-iplayer_2.83-1_all.deb

###### Debian 6 (oldstable, squeeze)

The get-iplayer package available in the squeeze repository is obsolete and should not be used.  The procedure below is one way to install the get-iplayer package from Debian testing (jessie) on Debian oldstable (squeeze) without adding the Debian testing repository to your system.  However, you may wish to add the testing repository or use some other method. The ffmpeg package must also be upgraded since it is not compatible with newer versions of get_iplayer.  Although installing packages from testing on a stable system is generally discouraged, it is currently safe to do so with the get-iplayer package.

1. Add **squeeze-backports** repository according to these instructions:

	<http://backports.debian.org/Instructions/>

2. Ensure package database is updated:

	$ sudo apt-get update

3. Download the get-iplayer package for Debian testing from your preferred mirror:

	<http://packages.debian.org/testing/all/get-iplayer/download>

4. Install the downloaded DEB file (version 2.82-2 in this example):

	$ sudo gdebi get-iplayer_2.82-2_all.deb
	
	Required dependencies will also be installed.

5. Install recommended packages (normally installed with get-iplayer package on Debian stable):

	$ sudo apt-get install atomicparsley id3v2 libmp3-info-perl

6. Install suggested packages for MP4/M4A/MP3 output and full MP3 tagging:

	$ sudo apt-get -t squeeze-backports install ffmpeg mplayer libmp3-tag-perl
	
	If you already have ffmpeg and mplayer packages installed, they will be upgraded.

7. Optionally install packages for secure email support:

	$ sudo apt-get libnet-smtp-ssl-perl libauthen-sasl-perl libnet-smtp-tls-perl

##### Web PVR Manager (WPM)

As of version 2.82-2 (released with Debian 7.0) - the WPM is installed along with the CLI.

1. Launch the WPM in with this command:

	$ get_iplayer_web_pvr

2. Once the WPM is running, connect to it by opening this URL in your browser:

	<http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-unix-package-ubuntu"></a>
#### Ubuntu

##### Command-line Interface (CLI)

###### Ubuntu Repositories

The Debian get-iplayer package is incorporated downstream in Ubuntu package repositories, so the above instructions for Debian stable may also be used with Ubuntu.  However, Ubuntu LTS ( Long Term Support) releases or Ubuntu editions that have [reached end-of-life](https://wiki.ubuntu.com/Releases) will very likely have obsolete get-iplayer packages.  Ubuntu users are recommended to install from the PPA (Personal Package Archive) maintained by Jon Davies.

###### PPA Packages

1. Add the PPA repository:

	$ sudo apt-add-repository ppa:jon-hedgerows/get-iplayer

2. Ensure package database is current:

	$ sudo apt-get update

3. Install get_iplayer and all dependencies:

	$ sudo apt-get install get-iplayer
	
	You may install over a get-iplayer installation from the Ubuntu repositories.  Existing dependencies will be updated if necessary.

4. Run CLI (assumed installed in $PATH):

	$ get_iplayer […]

5. If you wish to remove the PPA packages and roll back any updates:

	$ sudo ppa-purge ppa:jon-hedgerows/get-iplayer


##### Web PVR Manager (WPM)

As of version 2.82-2 (released with Debian 7.0) - the WPM is installed along with the CLI.  This also applies to the PPA installation.

1. Launch the WPM in with this command:

	$ get_iplayer_web_pvr

2. Once the WPM is running, connect to it by opening this URL in your browser:

	<http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-unix-package-opensuse"></a>
#### openSUSE

##### Command-line Interface (CLI)

The CLI package for openSUSE is maintained in the [Packman](http://packman.links2linux.org/) repository.

1. Install restricted format supports according the instructions for your system:

	<http://opensuse-community.org/Restricted_formats>
	
	The Packman repository should now be added to your system.  The ffmpeg utility also will have been installed.

2. Update package database:

	$ sudo zypper update

3. Install get_iplayer package and dependencies:

	$ sudo zypper install get_iplayer

4. Install suggested package for full MP3 tagging:

	$ sudo zypper install perl-MP3-Tag

5. Optionally install packages for secure email (SSL only)

	$ sudo zypper install perl-Net-SMTP-SSL perl-Authen-SASL

6. The official openSUSE repositories do not provide packages for AtomicParsley, nor do they provide packaged Perl modules to support TLS secure email.  You can find third-party packages supplied through the openSUSE Build Service: 

	<http://software.opensuse.org/package/AtomicParsley>
	
	<http://software.opensuse.org/package/perl-Net-SMTP-TLS>

	Although labelled as unstable, these packages don't have dependents and should be safe to install. You may opt for one-click installation, or you may download the RPM files and install them manually (choose the correct AtomicParsley RPM for your system architecture):

	$ sudo zypper install AtomicParsley-0.9.2+svn110-3.1.i586.rpm

	$ sudo zypper install perl-Net-SMTP-TLS-0.12-6.1.noarch.rpm

	If you opt for one-click installation, the initial "Additional Software Repositories" screen will display an option to "Remain subscribed to these repositories after installation".  Since these are one-off installations, you should uncheck that option.

##### Web PVR Manager (WPM)

The WPM is maintained in a separate package in the [Packman](http://packman.links2linux.org/) repository. 

1. Install CLI as described above.

2. Install WPM package and dependencies:

	$ sudo zypper install get_iplayer-pvr

3. Launch the WPM with this command:

	$ get_iplayer_pvr
	
	The WPM will open in a new xterm and your default browser will open to this URL:
	
	<http://127.0.0.1:1935>

4. Stop the WPM by typing Ctrl-C in the xterm where it is running.

<a name="linux-unix-package-openbsd"></a>
#### OpenBSD

1. Install get_iplayer package and dependencies:

	$ pkg_add get_iplayer
	
2. Install suggested packages for MP4/M4A/MP3 output:

	$ pkg_add ffmpeg mplayer

<a name="osx"></a>
## OS X

<a name="osx-manual"></a>
### Manual Installation

#### External Programs

TODO

#### Command-line Interface (CLI)

1. Download the latest release version:

    $ curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer

2. Ensure the script is executable:

    $ chmod 755 ./get_iplayer

3. Execute the script once with no arguments to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    $ ./get_iplayer

4. Optionally install the script somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install 755 ./get_iplayer /usr/local/bin

5. Run script (assumed installed in $PATH):

	$ get_iplayer [...]

#### Web PVR Manager (WPM)

1. Download the latest release version:

    $ curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer.cgi

2. Ensure the script is executable:

    $ chmod 755 ./get_iplayer.cgi

3. Optionally install somewhere in $PATH (e.g., /usr/local/bin):

    $ sudo install 755 ./get_iplayer.cgi /usr/local/bin

4. Launch WPM (assumed installed in $PATH):

	$ get_iplayer.cgi --listen 127.0.0.1 --port 1935

5. If CLI is not in $PATH, location must be explicitly set:

	$ get_iplayer.cgi --listen 127.0.0.1 --port 1935 --get /path/to/get_iplayer

6. Once Web PVR Manager is running, connect to it by opening this URL in your browser:

	<http://127.0.0.1:1935>

<a name="osx-homebrew"></a>
### Homebrew

Full information on installing get_iplayer with [Homebrew](http://mxcl.github.com/homebrew/) can be found at:

<https://github.com/dinkypumpkin/homebrew-get_iplayer/wiki>

If you already use Homebrew, you can install get_iplayer and its dependencies with:

```
$ brew tap dinkypumpkin/get_iplayer
$ brew update
$ brew install --with-deps get_iplayer
```

Information re: installing optional Perl modules can be found
[here](https://github.com/dinkypumpkin/homebrew-get_iplayer/wiki#2-enhanced-metadata-tagging-for-mp3-files).
If you use the OS X system Perl, note that XML::Simple is already installed.

<a name="windows"></a>
## Windows

<a name="windows-installer"></a>
### Installer

1. Download the latest Windows installer from:

	<http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe>

2. Start the installer and follow the wizard in the usual manner. The installer will download and install the Windows support programs: FFmpeg, rtmpdump, VLC Media Player, AtomicParsley, MPlayer, and lame. The installer will also install a private customised version of [Strawberry Perl](http://strawberryperl.com/).  It will not interfere with any other Perl distribution you may already have installed.

3. To start the CLI go to **Start -> get_iplayer -> get_iplayer**.  The CLI will launch in a console window.  The working directory of the console window will be the get_iplayer installation directory, typically `C:\Program Files\get_iplayer` or `C:\Program Files\get_iplayer (x86)` on 64-bit Windows.  The CLI expects to operate in that directory, so do not CD to another location.

4. To start the WPM go to **Start -> get_iplayer -> Web PVR Manager**.  The WPM will launch in a console window and your default browser will be opened to this URL:

	<http://127.0.0.1:1935>

5. **NOTE**: The installer sets the location for recorded programmes to `iPlayer Recordings` on your Windows desktop.  This setting only applies to the user who ran the installer.  If you have multiple users running get_iplayer on one Windows system, the other users will need to configure their own output folders.

	$ get_iplayer --prefs-add --output "%USERPROFILE%/Desktop/iPlayer Recordings"

<a name="windows-cygwin"></a>
### Cygwin

Download and install [Cygwin](http://cygwin.com/setup.exe).  Make sure you install libwww-perl (LWP) along with the default packages.  Then, in Cygwin shell:

TODO

<a name="optional-perl-modules"></a>
## Installing Optional Perl Modules

**Linux/Unix/OS X**: All the optional Perl modules may not be available via the package manager for your system.  It is generally unwise to employ superuser access to force additional modules into your system's Perl intallation. As an alternative, you can create a personal library containing just the additional Perl modules you need.  There are several ways to accomplish this, but a fairly simple method is described here:

<http://stackoverflow.com/questions/2980297/how-can-i-use-cpan-as-a-non-root-user>

**OS X**: Users should replace `wget -O-` with `curl -L -o -` in the instructions.  Also note that XML::Simple is installed with the system Perl on OS X.

**Windows**: The get_iplayer Windows installer includes all optional Perl modules.  No extra installation steps are necessary.

<a name="external-program-requirements"></a>
## External Program Requirements

### Download Modes, Output Formats and External Programs Required

The table below shows the external programmes required to download and - if applicable - convert and tag files produced from each combination of recording mode and output format used by get_iplayer.

|Type|Mode|Format|rtmpdump|ffmpeg|mplayer|atomicparsley|id3v2/MP3::Tag|
|----|----|------|--------|------|-------|-------------|--------------|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>&#160;|mp4<br/>mp4<br/>mp4<br/>mp4<br/>avi<br/>mp4<br/>(h264/aac)|X|X||X||
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --raw)|flv<br/>(h264/aac)|X|||||
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --mkv)|mkv<br/>(h264/aac)|X|X||||
|Radio|flashaudio|mp3|X||X||X|
|Radio|flashaudio<br/>(with --raw)|flv<br/>(mp3)|X|||||
|Radio|flashaachigh<br/>flashaacstd<br/>flashaaclow|m4a<br/>(aac)|X|X||X||
|Radio|flashaachigh<br/>flashaacstd<br/>flashaaclow<br/>(with --raw)|flv<br/>(aac)|X|||||
|Radio|flashaachigh<br/>flashaacstd<br/>flashaaclow<br/>(with --aactomp3)|mp3|X|X|||X|
|Radio|wma|wma|||X|||
|Podcast|podcast|mp3||||||
