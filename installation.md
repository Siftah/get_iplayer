# get_iplayer Installation

## Table of Contents

- [Requirements](#requirements)
- [Linux/Unix](#linux)
    - [Manual Installation](#linux-manual)
    - [Package Manager Installation](#linux-package)
        - [Debian](#linux-package-debian)
        - [Ubuntu](#linux-package-ubuntu)
        - [openSUSE](#linux-package-opensuse)
        - [OpenBSD](#linux-package-openbsd)
- [OS X](#osx)
    - [Manual Installation](#osx-manual)
    - [Package Manager Installation](#osx-package)
        - [Homebrew](#osx-homebrew)
        - [MacPorts](#osx-macports)
* [Windows](#windows)
    * [Installer](#windows-installer)
    * [Cygwin](#windows-cygwin)
* [Perlbrew](#perlbrew)
* [External Program Usage](#external-program-usage)

<a name="requirements"></a>
## Requirements

get_iplayer runs on Linux/Unix (numerous flavours supported), OS X (10.5+) or Windows (XP/Vista/7/8).

<a name="requirements-perl"></a>
### Perl Support

* Perl 5.8.8+ is required

One Perl module is **required** for get_iplayer:

* LWP - Required for HTTP access to BBC servers

Optional Perl modules may be installed for added functionality:

* MP3::Info - Catalogue MP3 files in *localfiles* plugin
* MP3::Tag - Full ID3 tagging of MP3 files
* Net::SMTP::SSL and Authen::SASL - Send search results via SSL secure email (e.g. Yahoo Mail)
* Net::SMTP::TLS::ButMaintained or Net::SMTP::TLS - Send search results via TLS secure email (e.g., GMail)
* XML::Simple - Parse [BBC RDF metadata](http://www.bbc.co.uk/ontologies/programmes/2009-09-07.shtml) to extract media links from BBC brand pages and programme microsites. Supports --pid-recursive option.

<a name="requirements-programs"></a>
### External Programs

get_iplayer employs external programs to download streams and manipulate media files:

- [rtmpdump](http://rtmpdump.mplayerhq.hu/) - Saves Flash audio/video streams to FLV files.
- [ffmpeg](http://ffmpeg.org) - Converts FLV files to MP4, M4A, MP3, or AVI format (for BBC TV, BBC national radio and BBC webcams).
- [mplayer](http://www.mplayerhq.hu) - Converts FLV files to MP3 format (for BBC regional and local radio). Also saves Windows Media audio streams to WMA files (for BBC radio).
- [AtomicParsley](http://atomicparsley.sourceforge.net) - Metadata tagging for MP4 and M4A files.
- [id3v2](http://id3v2.sourceforge.net) - Metadata tagging for MP3 files. However, the MP3::Tag Perl module is preferred because it supports more complete ID3 tagging.

Details of how external programs are used can be found [below](#external-program-usage).

<a name="linux"></a>
## Linux/Unix

<a name="linux-manual"></a>
### Manual Installation

<a name="linux-manual-perl"></a>
#### Perl Support
Perl is part of the base system for most Linux/Unix distributions.  If not, it will almost certainly be available in your system's package repositories.

Many Perl modules used by get_iplayer should be available in the package repositories for your system.  However, the naming convention for packaged Perl modules differs between distributions.  Generally speaking, a module's namespace separator ("::") is replaced by a hyphen, a prefix (and sometimes a suffix) are added, and the name is sometimes changed to lower case.  Consider an example: The package names for the MP3::Tag Perl module in some different distributions are:

* DEB-based (Debian, Ubuntu): **libmp3-tag-perl**
* RPM-based (openSUSE, Fedora): **perl-MP3-Tag**
* Ports-based (OpenBSD, MacPorts): **p5-mp3-tag**

One variation from the above scheme is important to know.  The package names for the required LWP module are:

* DEB-based (Debian, Ubuntu): **libwww-perl**
* RPM-based (openSUSE, Fedora): **perl-libwww-perl**
* Ports-based (OpenBSD, MacPorts): **p5-libwww**

<a name="linux-manual-perl-local"></a>
All the optional Perl modules utilised by get_iplayer may not be available via the package manager for your system.  It is generally unwise to employ superuser access to force additional modules into your system Perl installation. As an alternative, you can create a local library with the Perl local::lib module.  Your local Perl library will contain just the additional Perl modules you need, available to your system Perl.  There are several ways to accomplish this, but a fairly simple method is described here.  The instructions below are taken from:

<http://stackoverflow.com/questions/2980297/how-can-i-use-cpan-as-a-non-root-user>

Install [cpanminus](http://search.cpan.org/~miyagawa/App-cpanminus/) and set up Perl local library:

```
$ curl -L -o - "http://cpanmin.us" | perl - -l ~/perl5 App::cpanminus local::lib
$ eval `perl -I ~/perl5/lib/perl5 -Mlocal::lib`
$ echo 'eval `perl -I ~/perl5/lib/perl5 -Mlocal::lib`' >> ~/.profile
```

This assumes your profile is stored in ~/.profile. Depending on your specific setup, you may wish to change that to ~/.bash_profile or ~/.bashrc (for non-login shells). 

After your local Perl library is set up, you can install modules by running `cpanm MODULE::NAME`. So, to install the MP3::Tag module for get_iplayer:

`$ cpanm MP3::Tag` 

<a name="linux-manual-programs"></a>
#### External Programs

The external programs used by get_iplayer should be available in the package repositories for your system.  The package name will almost always be the same as the program itself.  For example, to install the rtmpdump utility 

`$ sudo apt-get install rtmpdump`

There are a few distributions that do not provide all the necessary external programs in their repositories.  For example, Fedora does not provide a packaged version of AtomicParsley.

<a name="linux-manual-cli"></a>
#### Command-line Interface (CLI)

1. Download the latest release version to working directory:

    `$ wget --no-check-certificate https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer`

2. Ensure the script is executable:

    `$ chmod 755 ./get_iplayer`

3. Execute the script once to initialise the config directory ($HOME/.get_iplayer) and download plugins:

    `$ ./get_iplayer`

4. Optionally install get_iplayer somewhere in $PATH (e.g., /usr/local/bin):

    `$ sudo install -m 755 ./get_iplayer /usr/local/bin`

5. Run CLI (assumed installed in $PATH):

    `$ get_iplayer […]`

<a name="linux-manual-wpm"></a>
#### Web PVR Manager (WPM)

1. Download the latest release version:

    `$ wget --no-check-certificate https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer.cgi`

2. Ensure the script is executable:

    `$ chmod 755 ./get_iplayer.cgi`

3. Optionally install get_iplayer.cgi somewhere in $PATH (e.g., /usr/local/bin):

    `$ sudo install -m 755 ./get_iplayer.cgi /usr/local/bin`

4. Launch WPM (assumed installed in $PATH):

    `$ get_iplayer.cgi --listen 127.0.0.1 --port 1935`

5. If CLI is not in $PATH, its location must be explicitly set:

    `$ get_iplayer.cgi --listen 127.0.0.1 --port 1935 --getiplayer /path/to/get_iplayer`

6. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

7. Stop the WPM by typing Ctrl-C.

<a name="linux-package"></a>
### Package Manager Installation

Some Linux/Unix distributions have get_iplayer packages in their software repositories.  These packages are installed using the package manager provided with your Linux/Unix distribution.  Installing a packaged version of get_iplayer will automatically install other required applications and libraries, including Perl modules and external.  get_iplayer is packaged different for different systems, so some components may require separate installation using your package manager.

Instructions for Linux/Unix distributions known to have up-to-date get_iplayer packages are given below.  If get_iplayer is not packaged for your system, use the manual installation instructions above.

<a name="linux-package-debian"></a>
#### Debian

##### Command-line Interface (CLI)

###### Debian 7 (stable, wheezy)

1. Install get_iplayer package (note that package name contains hyphen, not underscore):

    `$ sudo apt-get install get-iplayer`

2. Install suggested packages for MP4/M4A/MP3 output and full MP3 tagging:

    `$ sudo apt-get install ffmpeg mplayer libmp3-tag-perl`

3. Optionally install packages for secure email support:

    `$ sudo apt-get libnet-smtp-ssl-perl libauthen-sasl-perl libnet-smtp-tls-butmaintained-perl`

If you should ever need or want to update to a newer get-iplayer package from Debian testing, you can download and install the package directly.  Although installing packages from testing on a stable system is generally discouraged, it is currently safe to do so with the get-iplayer package.

1. Download the Debian testing get-iplayer package from your preferred mirror:

    <http://packages.debian.org/testing/all/get-iplayer/download>

2. Install the downloaded DEB file (version 2.83-1 in this example):

    `$ sudo gdebi get-iplayer_2.83-1_all.deb`

###### Debian 6 (oldstable, squeeze)

The get-iplayer package available in the squeeze repository is obsolete and should not be used.  The procedure below is one way to install the get-iplayer package from Debian testing (jessie) on Debian oldstable (squeeze) without adding the Debian testing repository to your system.  However, you may wish to add the testing repository or use some other method. The ffmpeg package must also be upgraded since it is not compatible with newer versions of get_iplayer.  Although installing packages from testing on a stable system is generally discouraged, it is currently safe to do so with the get-iplayer package.

1. Add **squeeze-backports** repository according to these instructions:

    <http://backports.debian.org/Instructions/>

2. Ensure package database is updated:

    `$ sudo apt-get update`

3. Download the get-iplayer package for Debian testing from your preferred mirror:

    <http://packages.debian.org/testing/all/get-iplayer/download>

4. Install the downloaded DEB file (version 2.82-2 in this example):

    `$ sudo gdebi get-iplayer_2.82-2_all.deb`
    
    Required dependencies will also be installed.

5. Install recommended packages (normally installed with get-iplayer package on Debian stable):

    `$ sudo apt-get install atomicparsley id3v2 libmp3-info-perl`

6. Install suggested packages for MP4/M4A/MP3 output and full MP3 tagging:

    `$ sudo apt-get -t squeeze-backports install ffmpeg mplayer libmp3-tag-perl`
    
    If you already have ffmpeg and mplayer packages installed, they will be upgraded.

7. Optionally install packages for secure email support:

    `$ sudo apt-get libnet-smtp-ssl-perl libauthen-sasl-perl libnet-smtp-tls-perl`

##### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM with:

    `$ get_iplayer_web_pvr`

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-package-ubuntu"></a>
#### Ubuntu

##### Command-line Interface (CLI)

The Debian get-iplayer package is incorporated downstream in Ubuntu repositories, so the above instructions for Debian stable may also be used with Ubuntu.  However, Ubuntu LTS (Long Term Support) releases or Ubuntu editions that have [reached end-of-life](https://wiki.ubuntu.com/Releases) will very likely have obsolete get-iplayer packages.  Ubuntu users are recommended to install from the [get-iplayer   PPA](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer) (Personal Package Archive) maintained by Jon Davies.

1. Add the PPA repository:

    `$ sudo apt-add-repository ppa:jon-hedgerows/get-iplayer`

2. Ensure package database is current:

    `$ sudo apt-get update`

3. Install get_iplayer and all dependencies:

    `$ sudo apt-get install get-iplayer`
    
    You may install from the PPA over a get_iplayer installation from the Ubuntu repositories.  Existing dependencies will be updated if necessary.

4. Run CLI (assumed installed in $PATH):

    `$ get_iplayer […]`

If you wish to remove the PPA packages and roll back any updates:

`$ sudo ppa-purge ppa:jon-hedgerows/get-iplayer`

##### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM in with this command:

    `$ get_iplayer_web_pvr`

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-package-opensuse"></a>
#### openSUSE

##### Command-line Interface (CLI)

The CLI package for openSUSE is maintained in the [Packman](http://packman.links2linux.org/) repository.

1. Install restricted formats support according to the instructions for your openSUSE release:

    <http://opensuse-community.org/Restricted_formats>
    
    The Packman repository should now be added to your system.  The ffmpeg utility also will have been installed.

2. Update package database:

    `$ sudo zypper update`

3. Install get_iplayer package and dependencies:

    `$ sudo zypper install get_iplayer`

4. Install suggested package for full MP3 tagging:

    `$ sudo zypper install perl-MP3-Tag`

5. Optionally install packages for secure email (SSL only)

    `$ sudo zypper install perl-Net-SMTP-SSL perl-Authen-SASL`

6. The official openSUSE repositories do not provide packages for AtomicParsley, nor do they provide packaged Perl modules to support TLS secure email.  You can find third-party packages supplied through the openSUSE Build Service: 

    <http://software.opensuse.org/package/AtomicParsley>
    
    <http://software.opensuse.org/package/perl-Net-SMTP-TLS>

    Although labelled as unstable, these packages should be safe to install. You may opt for one-click installation, or you may download the RPM files and install them manually:

    `$ sudo zypper install AtomicParsley-0.9.2+svn110-3.1.i586.rpm`

    NOTE: Choose the correct AtomicParsley RPM for your system architecture

    `$ sudo zypper install perl-Net-SMTP-TLS-0.12-6.1.noarch.rpm`

    If you opt for one-click installation, the initial "Additional Software Repositories" screen will display an option to "Remain subscribed to these repositories after installation".  Since these are one-off installations, you should uncheck that option.

There is no packaged version of id3v2 available, but you will not require it with the MP3::Tag module installed

##### Web PVR Manager (WPM)

The WPM is maintained in a separate package in the [Packman](http://packman.links2linux.org/) repository. 

1. Install CLI as described above.

2. Install WPM package and dependencies:

    `$ sudo zypper install get_iplayer-pvr`

3. Launch the WPM with:

    `$ get_iplayer_pvr`
    
    The WPM will open in a new xterm and your default browser will open to this URL:
    
    <http://127.0.0.1:1935>

4. Stop the WPM by typing Ctrl-C in the xterm where it is running.

<a name="linux-package-openbsd"></a>
#### OpenBSD

##### Command-line Interface (CLI)

1. Install get_iplayer package and dependencies:

    `$ sudo pkg_add get_iplayer`
    
2. Install suggested packages for MP4/M4A/MP3 output:

    `$ sudo pkg_add ffmpeg mplayer`

3. Optionally install Perl Modules for secure email:

    `$ sudo pkg_add p5-Net-SMTP-SSL p5-Authen-SASL p5-Net-SMTP-TLS-ButMaintained`

##### Web PVR Manager (WPM)

The WPM is not installed with the get_iplayer package.  Use the [manual installation procedure](#linux-manual-wpm).

<a name="osx"></a>
## OS X

<a name="osx-manual"></a>
### Manual Installation

<a name="osx-manual-perl"></a>
#### Perl Support
Perl is part of the OS X base system, so no installation is necessary.

Additional Perl modules may be installed using the [local::lib method](#linux-manual-perl-local) described above for Linux/Unix, with one change: replace `wget -O-` with `curl -L -o -` in the instructions.  Also note that the LWP and XML::Simple modules are already installed with the system Perl on OS X.

<a name="osx-manual-programs"></a>
#### External Programs

TODO

<a name="osx-manual-cli"></a>
#### Command-line Interface (CLI)

Use the [manual installation procedure](#linux-manual-cli) described above for Linux/Unix, with one change - use the command below to download the CLI:

`$ curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer`

<a name="osx-manual-wpm"></a>
#### Web PVR Manager (WPM)

Use the [manual installation procedure](#linux-manual-wpm) described above for Linux/Unix, with one change - use the command below to download the WPM:

`$ curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer.cgi`

<a name="osx-package"></a>
### Package Manager Installation

<a name="osx-homebrew"></a>
#### Homebrew

##### Perl Support

Homebrew is designed to work with the system Perl installed with OS X, so no additional Perl installation is required.  The OS X system Perl already includes the LWP and XML::Simple modules.  

Additional Perl modules may be installed using the [local::lib method](#linux-manual-perl-local) described above for Linux/Unix, with one change: replace `wget -O-` with `curl -L -o -` in the instructions.  

##### External Programs

All external programs can be installed with the get_iplayer, as noted below.  They may also be installed separately:

```
$ brew update
$ brew install rtmpdump
$ brew install atomicparsley
$ brew install id3v2
$ brew install ffmpeg
$ brew install mplayer
```

##### Command-line Interface (CLI)

Full information on installing get_iplayer with [Homebrew](http://mxcl.github.com/homebrew/) can be found at:

<https://github.com/dinkypumpkin/homebrew-get_iplayer/wiki>

If you already use Homebrew, you can install get_iplayer and related external programs with:

```
$ brew tap dinkypumpkin/get_iplayer
$ brew update
$ brew install --with-deps get_iplayer
```

##### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM with:

    `$ get_iplayer_web_pvr`

2. The WPM will launch in a `screen` session and your default browser will be opened to this URL:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="osx-macports"></a>
#### MacPorts

get_iplayer is not packaged in [MacPorts](http://www.macports.org). However, MacPorts provides a means to set up the dependencies required for get_iplayer.

Install MacPorts using the instructions [here](http://www.macports.org/install.php).  You can use the "pkg" installer for your system.

##### Perl Support

NOTE: Because MacPorts is a self-contained system, you must install the MacPorts build of Perl (it will be pulled in as a dependency of other packages anyway).  If you use other Perl applications that current rely on the system Perl, be sure to install any modules required for those applications into the MacPorts Perl library.  If you find you need to switch between multiple installations, take a look at [Perlbrew](http://perlbrew.pl).

1. Install Perl
 
    `$ sudo port install perl5 +perl5_16`

    This example installs Perl 5.16 (perl5_16 variant).  If you wish to install the default version (5.12), omit "+perl5_16".

2. Install required LWP module:

    `$ sudo port install p5-libwww-perl`

3. Install suggested Perl modules:

    `$ sudo port install p5-xml-simple p5-mp3-tag p5-mp3-info`

4. The optional Perl modules to support secure email are not packaged in  MacPorts.  However, they can be installed with the [CPAN](http://www.cpan.org) client into the MacPorts Perl library.

    `$ sudo cpan Net::SMTP::SSL Authen::SASL Net::SMTP::TLS::ButMaintained`


##### External Programs

1. Install external programs (except ffmpeg):

    `$ sudo port install rtmpdump mplayer atomicparsley id3v2`

2. Install ffmpeg:

    `$ sudo port install ffmpeg +no_x11`

    This example installs the "no_x11" variant, which slims down the installation by not pulling in X11, Python and other dependencies of libsdl (a ffmpeg dependency).  If you want a full installation of libsdl with ffmpeg, omit "+no_X11".

##### Command-line Interface (CLI)

Use the [manual installation procedure](#osx-manual-cli) described above.

##### Web PVR Manager (WPM)

Use the [manual installation procedure](#osx-manual-wpm) described above.

<a name="windows"></a>
## Windows

<a name="windows-installer"></a>
### Installer

#### Perl Support

The installer will install a private customised version of [Strawberry Perl](http://strawberryperl.com/) that includes all necessary Perl modules.  It will not interfere with any other Perl distribution you may already have installed.

#### External Programs

The installer will download and install the required Windows support programs.  It will also install VLC Media Player.

#### Command-line Interface (CLI)

1. Download the latest Windows installer from:

    <http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe>

2. Start the installer and follow the wizard in the usual manner. The installer will download and install the Windows support programs: FFmpeg, rtmpdump, VLC Media Player, AtomicParsley, MPlayer, and lame. 

3. To start the CLI go to **Start -> get_iplayer -> get_iplayer**.  The CLI will launch in a console window.  The working directory of the console window will be the get_iplayer installation directory, typically `C:\Program Files\get_iplayer` or `C:\Program Files\get_iplayer (x86)` on 64-bit Windows.  The CLI expects to operate in that directory, so do not CD to another location.

**NOTE**: The installer sets the default location for recorded programmes to `iPlayer Recordings` on your Windows desktop.  This setting only applies to the user who ran the installer.  If you have multiple users running get_iplayer on one Windows system, the other users will need to configure their own output folders with the CLI:

`$ get_iplayer --prefs-add --output "%USERPROFILE%/Desktop/iPlayer Recordings"`

#### Web PVR Manager (WPM)

The WPM is installed along with CLI.
    
1. To start the WPM go to **Start -> get_iplayer -> Web PVR Manager**.  

2. The WPM will launch in a console window and your default browser will be opened to this URL:

    <http://127.0.0.1:1935>


<a name="windows-cygwin"></a>
### Cygwin

#### Perl Support

TODO

#### External Programs

TODO

#### CLI

1. Download and install Cygwin from

	<http://cygwin.com/setup.exe>
  
	Make sure you install libwww-perl (LWP) along with the default packages.

TODO

<a name="perlbrew"></a>
## Perlbrew

As of version 2.83, get_iplayer is compatible with [Perlbrew](http://perlbrew.pl).

TODO

<a name="external-program-usage"></a>
## External Program Usage

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


