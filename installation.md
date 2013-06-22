## get_iplayer Installation

### Oh-So-Important Note:

**If the version of get_iplayer you are about to install was released before 2013-06-06, please do not install it.  It is broken due to changes by the BBC. All releases of get_iplayer 2.83 or higher are fixed, and most package versions of get_iplayer 2.82 have been fixed.  Check the information for your release.  If you must continue using get_iplayer 2.82 released before 2013-06-06, see [[this page|swfurl]] for instructions on how to adjust your get_iplayer settings to restore downloads.**

## Table of Contents

- [Requirements](#requirements)
- [Linux/Unix](#linux)
    - [Manual Installation](#linux-manual)
    - [Package Manager Installation](#linux-package)
        - [Debian](#linux-package-debian)
        - [Ubuntu](#linux-package-ubuntu)
        - [Raspbian / Raspberry Pi](#linux-package-raspbian)
        - [openSUSE](#linux-package-opensuse)
        - [Arch Linux](#linux-package-arch)
        - [Puppy Linux](#linux-package-puppy)
        - [OpenBSD](#unix-package-openbsd)
        - [FreeBSD](#unix-package-freebsd)
        - [PC-BSD](#unix-package-pcbsd)
- [OS X](#osx)
    - [Manual Installation](#osx-manual)
    - [Installer](#osx-installer)
    - [Package Manager Installation](#osx-package)
        - [Homebrew](#osx-homebrew)
        - [MacPorts](#osx-macports)
* [Windows](#windows)
    * [Installer](#windows-installer)
    * [Cygwin](#windows-cygwin)
* [Perlbrew](#perlbrew)
* [Git HEAD](#git-head)
    * [Using Git](#git-head-git)
    * [Linux/Unix/OS X](#git-head-linux)
    * [Windows](#git-head-windows)

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
* XML::Simple - Parse [BBC RDF metadata](http://www.bbc.co.uk/ontologies/programmes/2009-09-07.shtml) to extract media links from BBC brand pages and programme microsites. Supports --pid-recursive option.

<a name="requirements-programs"></a>
### External Programs

get_iplayer employs external programs to download streams and manipulate media files:

- [rtmpdump](http://rtmpdump.mplayerhq.hu/) - Saves Flash audio/video streams to FLV files.
- [ffmpeg](http://ffmpeg.org) - Converts FLV files to MP4, M4A, MP3, or AVI format (for BBC TV, BBC national radio and BBC webcams).
- [mplayer](http://www.mplayerhq.hu) - Converts FLV files to MP3 format (for BBC regional and local radio). Also saves Windows Media audio streams to WMA files (for BBC radio).
- [AtomicParsley](http://atomicparsley.sourceforge.net) - Metadata tagging for MP4 and M4A files.
- [id3v2](http://id3v2.sourceforge.net) - Metadata tagging for MP3 files. However, the MP3::Tag Perl module is preferred because it supports more complete ID3 tagging.

Details of how external programs are used can be found [here](modes#external-programs).

<a name="linux"></a>
## Linux/Unix

<a name="linux-manual"></a>
### Manual Installation

<a name="linux-manual-perl"></a>
#### Perl Support

Perl is part of the base system for most Linux/Unix distributions.  If not, it will almost certainly be available in your system's package repositories.

##### Packaged Modules

Many Perl modules used by get_iplayer should be available in the package repositories for your system.  However, the naming convention for packaged Perl modules differs between distributions.  Generally speaking, a module's namespace separator ("::") is replaced by a hyphen, a prefix (and sometimes a suffix) are added, and the name is sometimes changed to lower case.  Consider an example: 

The package names for the **MP3::Tag** Perl module in some different distributions are:

* DEB-based (Debian, Ubuntu): **libmp3-tag-perl**
* RPM-based (openSUSE, Fedora): **perl-MP3-Tag**
* Ports-based (OpenBSD, MacPorts): **p5-mp3-tag** or **p5-MP3-Tag**

One variation from the above scheme is important to know.  The package names for the required **LWP** module are:

* DEB-based (Debian, Ubuntu): **libwww-perl**
* RPM-based (openSUSE, Fedora): **perl-libwww-perl**
* Ports-based (OpenBSD, MacPorts): **p5-libwww**

<a name="linux-manual-perl-local"></a>
##### Local Module Library

All the Perl modules utilised by get_iplayer may not be available via the package manager for your system.  It is generally unwise to employ superuser access to force additional modules into your system's Perl installation. As an alternative, you can create a local module library with [cpanminus](http://search.cpan.org/~miyagawa/App-cpanminus/) and the Perl [local::lib](http://search.cpan.org/~ether/local-lib) module.  Your local library will contain just the additional Perl modules you need. The instructions below are derived from:

<http://stackoverflow.com/questions/2980297/how-can-i-use-cpan-as-a-non-root-user>

To install cpanminus and local::lib and set up your local library in ~/perl5:

```
curl -L "http://cpanmin.us" | perl - -l ~/perl5 App::cpanminus local::lib
eval `perl -I ~/perl5/lib/perl5 -Mlocal::lib`
echo 'eval `perl -I ~/perl5/lib/perl5 -Mlocal::lib`' >> ~/.profile
```

**NOTE**: If your system does not have `curl` try `wget`.  Replace `curl -L` with `wget -O-`.

This example is for the bash shell and assumes that your profile is loaded from ~/.profile, but you may prefer to use ~/.bash_profile.  You may also prefer to initialise your environment in ~/.bashrc and load that file from ~/.profile or ~/.bash_profile. The equivalent locations are different for different shells, e.g., ~/.login and ~/.cshrc for csh or ~/.login and ~/.tcshrc for tcsh.  The "eval" statement initialises environment variables necessary for local::lib to function, so place it in whichever file you use to set up your shell environment.

After your local library is set up, you can install modules with `cpanm Module::Name [Module::Name …]`. For example, to install the Perl modules for get_iplayer:

``` bash
cpanm LWP MP3::Info MP3::Tag Net::SMTP::SSL Net::SMTP::TLS::ButMaintained XML::Simple
```

<a name="linux-manual-programs"></a>
#### External Programs

The external programs used by get_iplayer should be available in the package repositories for your system.  The package name will almost always be the same as the program itself.  For example, to install the utilities for get_iplayer in Debian: 

`sudo apt-get install rtmpdump ffmpeg mplayer atomicparsley id3v2`

Replace `sudo apt-get install` with `sudo zypper install` (openSUSE), `sudo pacman -S` (Arch Linux), `sudo pkg_add` (OpenBSD) or `sudo pkg_add -r` (FreeBSD).

A few distros do not provide all the necessary external programs in their official repositories.  You may need to acquire external programs from other repositories or - in rare instances - be required to build your own.

<a name="linux-manual-cli"></a>
#### Command-line Interface (CLI)

1. Download the latest release to working directory

    `curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer`

	**NOTE**: If your system does not have `curl` try `wget`.  Replace `curl -kLO` with `wget --no-check-certificate`.

2. Ensure the script is executable

    `chmod 755 ./get_iplayer`

3. Execute the script once to initialise the config directory ($HOME/.get_iplayer) and download plugins

    `./get_iplayer`

4. Optionally install get_iplayer somewhere in PATH (e.g., /usr/local/bin)

    `sudo install -m 755 ./get_iplayer /usr/local/bin`

5. Run CLI (assumed installed in PATH) with:

    `get_iplayer […]`

<a name="linux-manual-wpm"></a>
#### Web PVR Manager (WPM)

1. Download the latest release to working directory

    `curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/latest/get_iplayer.cgi`

	**NOTE**: If your system does not have `curl` try `wget`.  Replace `curl -kLO` with `wget --no-check-certificate`.

2. Ensure the script is executable

    `chmod 755 ./get_iplayer.cgi`

3. Optionally install get_iplayer.cgi somewhere in PATH (e.g., /usr/local/bin)

    `sudo install -m 755 ./get_iplayer.cgi /usr/local/bin`

4. Launch WPM (assumed installed in PATH):

    `get_iplayer.cgi --listen 127.0.0.1 --port 1935`

5. If CLI is not in PATH, its location must be explicitly set

    `get_iplayer.cgi --listen 127.0.0.1 --port 1935 --getiplayer /path/to/get_iplayer`

6. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

7. Stop the WPM by typing Ctrl-C.

<a name="linux-package"></a>
### Package Manager Installation

Some Linux/Unix distributions have get_iplayer packages in their software repositories.  These packages are installed using the package manager provided with the Linux/Unix distribution. If get_iplayer is not packaged for your system, use the [manual installation procedure](#linux-manual) above.  

Installing a packaged version of get_iplayer will automatically install other required applications and libraries, including Perl modules and external programs.  get_iplayer is packaged differently for different systems, so some components may require separate installation using your package manager.  The instructions below cover installation of both required and optional components to enable all get_iplayer functionality.

These instructions cover Linux/Unix distributions known to have working get_iplayer 2.82 packages at the time get_iplayer 2.83 was released.  If the installation process for any of these Linux/Unix distributions has changed, or you wish to add a new distribution, please either edit this wiki page or post corrections to the [get_iplayer mailing list](http://lists.infradead.org/mailman/listinfo/get_iplayer).  

<a name="linux-package-debian"></a>
#### Debian

These instructions are for Debian 7 (stable, wheezy).  Information for Debian 6 (squeeze) can be found [[here|debian6]].

##### Command-line Interface (CLI)

1. Install get-iplayer package (note that package name contains hyphen, not underscore)

    `sudo apt-get install get-iplayer`

2. Install components not installed with get-iplayer package

    `sudo apt-get install ffmpeg mplayer libmp3-tag-perl libnet-smtp-ssl-perl libauthen-sasl-perl`

3. The packaged Perl modules for secure email with TLS in Debian 7.0 are currently incompatible with the packaged version of IO::Socket::SSL.  If TLS is your only secure email option, you can use the [local::lib method](#linux-manual-perl-local) described above to create a local Perl module library and install the necessary module:

	`cpanm Net::SMTP::TLS::ButMaintained`

4. Run CLI with:

	`get_iplayer […]`


##### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM with:

    `get_iplayer_web_pvr`

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-package-debian-testing"></a>
##### Update to Debian Testing/Unstable Version

If you should ever need to update to a get-iplayer package that is newer than the one provided in Debian stable, you can download and install the Debian testing/unstable package directly.  Although installing packages from testing on a stable system is often discouraged, it is currently safe to do so with the get-iplayer package.

1. Check the package and make sure that dependencies have not changed

	<http://packages.debian.org/stable/get-iplayer>

	Switch to the testing/unstable package pages using the links at the top right of the page.
	
2. If the dependencies still look OK, download the Debian testing/unstable get-iplayer package from your preferred mirror

    <http://packages.debian.org/testing/all/get-iplayer/download>

    <http://packages.debian.org/unstable/all/get-iplayer/download>

3. Remove just the old get-iplayer package

	`sudo dpkg -r get-iplayer`

4. Install the downloaded DEB file (version 2.83-1 in this example)

    `sudo dpkg -i get-iplayer_2.83-1_all.deb`

	Only the get-iplayer package will be updated, so this method assumes that dependencies have not changed in the newer package.

 
<a name="linux-package-ubuntu"></a>
#### Ubuntu

These instructions are for Ubuntu 13.04 (Raring Ringtail).

##### Command-line Interface (CLI)

Although the Debian get-iplayer package is incorporated in Ubuntu repositories, Ubuntu users are recommended to use the get_iplayer PPA version (see below).  If you must use the Ubuntu package, refer to the above instructions for Debian installation. The only change for Ubuntu is that you should additionally install the `libnet-smtp-tls-butmaintained-perl` package.  

Ubuntu LTS (Long Term Support) releases such as 12.04 (Precise Pangolin) will very likely have obsolete get-iplayer packages in their repositories.  Please use the PPA version instead.  Ubuntu editions that have [reached end-of-life](https://wiki.ubuntu.com/Releases) should use the [manual installation procedure](#linux-manual).

##### PPA Installation

The [get-iplayer PPA](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer) (Personal Package Archive) is maintained by Jon Davies.  Packages with up-to-date versions of get_iplayer and dependencies are available for supported Ubuntu releases from 10.04 onwards.

1. Add the PPA repository

    `sudo apt-add-repository ppa:jon-hedgerows/get-iplayer`

2. Ensure package database is current

    `sudo apt-get update`

3. Install get_iplayer and all dependencies from PPA:

    `sudo apt-get install get-iplayer`
    
    You may install from the PPA over an existing get_iplayer installation from the Ubuntu repositories.  Dependencies will be updated if necessary.

4. Install components not installed with get-iplayer package

    `sudo apt-get install libnet-smtp-ssl-perl libauthen-sasl-perl libnet-smtp-tls-butmaintained-perl`

5. Run CLI with:

    `get_iplayer […]`

If you wish to remove the PPA packages and roll back any updates:

`sudo ppa-purge ppa:jon-hedgerows/get-iplayer`

##### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM in with this command:

    `get_iplayer_web_pvr`

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-package-raspbian"></a>
#### Raspbian / Raspberry Pi

These instructions are for Raspbian wheezy.

##### Command-line Interface (CLI)

Although the Debian get-iplayer package is incorporated in Raspbian repositories, Raspbian users are recommended to use the get_iplayer repository version (see below).  If you must use the Debian package, refer to the above instructions for Debian installation.  Note that the version of AtomicParsley
packaged with Raspbian frequently fails with files downloaded with get_iplayer.

##### get_iplayer Repository Installation

1. Add the repository

    Paste these _five_ lines into a terminal window:

    ```bash
    sudo bash -c "cat > /etc/apt/sources.list.d/packages.hedgerows.org.uk.list <<EOF
    deb http://packages.hedgerows.org.uk/raspbian wheezy/
    deb-src http://packages.hedgerows.org.uk/raspbian wheezy/
    EOF
    "
    ```

1. Update, and install the repository signing key, and update again:

    ```bash
    sudo apt-get update
    sudo apt-get --allow-unauthenticated -y install jonhedgerows-keyring
    sudo apt-get update
    ```

1. Install the get-iplayer package

    `sudo apt-get install get-iplayer`

1. Run CLI with:

    `get_iplayer […]`

##### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM in with this command:

    `get_iplayer_web_pvr`

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-package-opensuse"></a>
#### openSUSE

These instructions are for openSUSE 12.3.

##### Command-line Interface (CLI)

The CLI package for openSUSE is maintained in the [Packman](http://packman.links2linux.org/package/get_iplayer) repository.

1. Install restricted formats support according to the instructions here:

    <http://opensuse-community.org/Restricted_formats>
    
    The Packman repository should now be added to your system.  The ffmpeg utility also will have been installed.

2. Update package database

    `sudo zypper update`

3. Install get_iplayer package and dependencies

    `sudo zypper install get_iplayer`

4. Install components not installed with get_iplayer package

    `sudo zypper install perl-MP3-Tag perl-Net-SMTP-SSL perl-Authen-SASL`

5. The official openSUSE repositories do not provide packages for AtomicParsley, nor do they provide packaged Perl modules to support TLS secure email.  You can find third-party packages supplied through the openSUSE Build Service: 

    <http://software.opensuse.org/package/AtomicParsley>
    
    <http://software.opensuse.org/package/perl-Net-SMTP-TLS>

    Although labelled as unstable, these packages should be safe to install. You may opt for one-click installation, or you may download the RPM files and install them manually:

    `sudo zypper install AtomicParsley-0.9.2+svn110-3.1.i586.rpm`

    NOTE: Download the correct AtomicParsley RPM for your system architecture.

    `sudo zypper install perl-Net-SMTP-TLS-0.12-6.1.noarch.rpm`

    If you opt for one-click installation, the initial "Additional Software Repositories" screen will display an option to "Remain subscribed to these repositories after installation".  Since these are one-off installations, uncheck that option.

	There is no packaged version of id3v2 available, but you will not require it with the MP3::Tag module installed.

6. Run CLI with:

    `get_iplayer […]`


##### Web PVR Manager (WPM)

The WPM is maintained in a separate package in the [Packman](http://packman.links2linux.org/package/get_iplayer) repository. 

1. Install CLI as described above

2. Install WPM package and dependencies

    `sudo zypper install get_iplayer-pvr`

3. Launch the WPM with:

    `get_iplayer_pvr`
    
    The WPM will open in a new xterm and your default browser will open to this URL:
    
    <http://127.0.0.1:1935>

4. Stop the WPM by typing Ctrl-C in the xterm where it is running.

<a name="linux-package-arch"></a>
#### Arch Linux

These instructions are for Arch Linux 3.9.4

##### Command-line Interface (CLI)

1. Install packages available in official repositories

	`sudo pacman -S rtmpdump ffmpeg mplayer id3v2 perl-xml-simple perl-mp3-info`

2. Install remaining packages from Arch User Repository (AUR)

	Although not covered here, you may also be able to install the AUR packages with [yaourt](https://wiki.archlinux.org/index.php/Yaourt).

	First, make a base directory for the package builds:

	`mkdir ~/packages`

	Then download, build and install each package in turn:

	``` bash
	cd ~/packages
	curl -kLO https://aur.archlinux.org/packages/ge/get_iplayer/get_iplayer.tar.gz
	tar xzf get_iplayer.tar.gz
	cd get_iplayer
	makepkg -s
	sudo pacman -U get_iplayer*.tar.xz

	cd ~/packages
	curl -kLO https://aur.archlinux.org/packages/at/atomicparsley/atomicparsley.tar.gz
	tar xzf atomicparsley.tar.gz
	cd atomicparsley
	makepkg -s
	sudo pacman -U atomicparsley*.tar.xz

	cd ~/packages
	curl -kLO https://aur.archlinux.org/packages/pe/perl-mp3-tag/perl-mp3-tag.tar.gz
	tar xzf perl-mp3-tag.tar.gz
	cd perl-mp3-tag
	makepkg -s
	sudo pacman -U perl-mp3-tag*.tar.xz

	cd ~/packages
	curl -kLO https://aur.archlinux.org/packages/pe/perl-net-smtp-tls-butmaintained/perl-net-smtp-tls-butmaintained.tar.gz
	tar xzf perl-net-smtp-tls-butmaintained.tar.gz
	cd perl-net-smtp-tls-butmaintained
	makepkg -s
	sudo pacman -U perl-net-smtp-tls-butmaintained*.tar.xz
	```

	With `perl-net-smtp-tls-butmaintained` version 0.21, makepkg fails with the message "ERROR: Failure while downloading Net-SMTP-TLS-ButMaintained-0.21.tar.gz".  That error indicates the upstream source code was removed.  If that happens you can try this procedure:
	
	``` bash
	# Hack PKGBUILD to download source from a different location
	cp PKGBUILD PKGBUILD.orig
	sed -e "s|search.cpan.org/CPAN|cpan.metacpan.org|g" PKGBUILD.orig > PKGBUILD
	
	# Skip checksum integrity check during package build
	makepkg -s --skipinteg
	
	# Install the package
	sudo pacman -U perl-net-smtp-tls-butmaintained*.tar.xz
	```

NOTE: If you use SSL email, you may see a deprecation warning about the use of SSL_verify_mode, a parameter used by the IO::Socket::SSL module.  However, your emails should still be transmitted successfully.

##### Web PVR Manager (WPM)

The WPM is not installed with the get_iplayer package.  Use the [manual installation procedure](#linux-manual-wpm).

<a name="linux-package-puppy"></a>
#### Puppy Linux

TODO: Awaiting Update

##### Command-line Interface (CLI)

##### Web PVR Manager (WPM)

<a name="linux-package-openbsd"></a>
#### OpenBSD

These instructions are for OpenBSD 5.3.

##### Command-line Interface (CLI)

1. Install get_iplayer package and dependencies

    `sudo pkg_add get_iplayer`
    
2. Install components not installed with get_iplayer package

    `sudo pkg_add ffmpeg mplayer p5-Net-SMTP-SSL p5-Authen-SASL p5-Net-SMTP-TLS-ButMaintained`

3. Run CLI with:

    `get_iplayer […]`

NOTE: If you use SSL email, you may see a deprecation warning about the use of SSL_verify_mode, a parameter used by the IO::Socket::SSL module.  However, your emails should still be transmitted successfully.

##### Web PVR Manager (WPM)

The WPM is not installed with the get_iplayer package.  Use the [manual installation procedure](#linux-manual-wpm).

<a name="linux-package-freebsd"></a>
#### FreeBSD

TODO: Awaiting Update

These instructions are for FreeBSD 9.1.

##### Command-line Interface (CLI)

##### Web PVR Manager (WPM)

#### PC-BSD

TODO: Awaiting Update

These instructions are for PC-BSD 9.1.

##### Command-line Interface (CLI)

##### Web PVR Manager (WPM)

<a name="osx"></a>
## OS X

<a name="osx-manual"></a>
### Manual Installation

<a name="osx-manual-perl"></a>
#### Perl Support
Perl is part of the OS X base system, so no installation is necessary.

Additional Perl modules may be installed using the [local::lib method](#linux-manual-perl-local) described above for Linux/Unix.  Note that the LWP and XML::Simple modules are already installed with the system Perl on OS X.

<a name="osx-manual-programs"></a>
#### External Programs

WIP

<a name="osx-manual-cli"></a>
#### Command-line Interface (CLI)

Use the [manual installation procedure](#linux-manual-cli) described above for Linux/Unix.

<a name="osx-manual-wpm"></a>
#### Web PVR Manager (WPM)

Use the [manual installation procedure](#linux-manual-wpm) described above for Linux/Unix.

<a name="osx-installer"></a>
### Installer

WIP

<a name="osx-package"></a>
### Package Manager Installation

<a name="osx-homebrew"></a>
#### Homebrew

Full information on installing get_iplayer with [Homebrew](http://mxcl.github.com/homebrew/) can be found here:

<https://github.com/dinkypumpkin/homebrew-get_iplayer/wiki>

##### Perl Support

Homebrew is designed to work with the system Perl installed with OS X, so no additional Perl installation is required.  The OS X system Perl already includes the LWP and XML::Simple modules. Additional Perl modules may be installed using the [local::lib method](#linux-manual-perl-local) described above for Linux/Unix.  

##### External Programs

All external programs can be installed with the get_iplayer package, as noted below.  They may also be installed separately:

``` bash
$ brew update
$ brew install rtmpdump ffmpeg mplayer atomicparsley id3v2
```

##### Command-line Interface (CLI)

Install get_iplayer and all related external programs with:

``` bash
$ brew tap dinkypumpkin/get_iplayer
$ brew update
$ brew install --with-deps get_iplayer
```

##### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM with:

    `get_iplayer_web_pvr`

2. The WPM will launch in a `screen` session and your default browser will be opened to this URL:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="osx-macports"></a>
#### MacPorts

get_iplayer is not packaged in [MacPorts](http://www.macports.org). However, MacPorts provides all the dependencies required for get_iplayer on OS X.  Install MacPorts using the instructions [here](http://www.macports.org/install.php).  You can use the "pkg" installer for your system.

##### Perl Support

Because MacPorts is a self-contained system, you must install the MacPorts build of Perl (it will be pulled in as a dependency of other packages anyway), which will become your default Perl.  If you use other Perl applications that current rely on the system Perl distributed with OS X, be sure to install any modules required for those applications into the MacPorts Perl library.  If you find you need to switch between multiple Perl installations, take a look at [Perlbrew](http://perlbrew.pl).

1. Install Perl
 
    `sudo port install perl5`

    This installs the default Perl version (currently 5.12). If you wish to install a newer version such as 5.16, add the necessary variant flag:

	`sudo port install perl5 +perl5_16`

2. Install Perl modules

    `sudo port install p5-libwww-perl p5-xml-simple p5-mp3-tag p5-mp3-info`

3. The Perl modules to support secure email are not packaged in  MacPorts.  However, they can be installed with a [CPAN](http://www.cpan.org) client into the MacPorts Perl library:

    `sudo cpan Net::SMTP::SSL Authen::SASL Net::SMTP::TLS::ButMaintained`


##### External Programs

1. Install external programs (except ffmpeg)

    `sudo port install rtmpdump mplayer atomicparsley id3v2`

2. Install ffmpeg

    `sudo port install ffmpeg`

    This example pulls in X11, Python and other dependencies you may not want or need.  If you want a slimmed-down installation of ffmpeg, use the "no_X11" variant:

    `sudo port install ffmpeg +no_x11`
    
##### Command-line Interface (CLI)

Use the [manual installation procedure](#osx-manual-cli) described above.

##### Web PVR Manager (WPM)

Use the [manual installation procedure](#osx-manual-wpm) described above.

<a name="windows"></a>
## Windows

<a name="windows-installer"></a>
### Installer

Windows users should use the provided installer.  Download the latest version from:

<http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe>

#### Perl Support

The installer will install a private customised version of [Strawberry Perl](http://strawberryperl.com/) that includes all necessary Perl modules.  It will not interfere with any other Perl distribution you may already have installed.

#### External Programs

The installer will download and install all the required Windows support programs.

#### Command-line Interface (CLI)

1. Start the installer and follow the wizard in the usual manner.  Select all components for installation The installer will download and install get_iplayer, Perl and the Windows support programs: RTMPDump, FFmpeg, MPlayer, LAME, AtomicParsley and VLC Media Player. 

2. To start the CLI go to **All Programs -> get_iplayer -> Get_iPlayer** on the Start menu.  In the Windows 8 Start screen, click the **Get_iPlayer** tile.   The CLI will launch in a console window.  The working directory of the console window will be the get_iplayer installation directory, typically `C:\Program Files\get_iplayer` or `C:\Program Files (x86)\get_iplayer` on 64-bit Windows.  The CLI expects to operate in that directory, so do not change to another location.

3. **NOTE**: Unless you opt to change the default value, the installer sets the location for recorded programmes to `iPlayer Recordings` on your Windows desktop.  This setting only applies to the administrator user who ran the installer.  If you have multiple users running get_iplayer on one Windows system, the other users will need to configure their own output folders with the CLI:

	`get_iplayer --prefs-add --output "%USERPROFILE%/Desktop/iPlayer Recordings"`

#### Web PVR Manager (WPM)

The WPM is installed along with the CLI.
    
1. To start the WPM go to **All Programs -> get_iplayer -> Web PVR Manager** on the Start menu.  In the Windows 8 Start screen, click the **Web PVR Manager** tile.  

2. The WPM will launch in a console window and your default browser will be opened to this URL:

    <http://127.0.0.1:1935>

<a name="windows-cygwin"></a>
### Cygwin

TODO

#### Perl Support

#### External Programs

#### Command-line Interface (CLI)

#### Web PVR Manager (WPM)

<a name="perlbrew"></a>
## Perlbrew

get_iplayer 2.83 or higher is compatible with [Perlbrew](http://perlbrew.pl) on Linux/Unix/OS X.  Once you have activated the Perl installation you intend to use for get_iplayer, use cpan or cpanm to install the necessary modules:

`cpanm LWP MP3::Info MP3::Tag XML::Simple Net::SMTP::SSL Authen::SASL Net::SMTP::TLS::ButMaintained`

<a name="git-head"></a>
## Git HEAD

Git HEAD is the latest development version (HEAD) of get_iplayer from the Git repository. There may be occasions when you wish to use the Git HEAD version of get_iplayer in order to test bug fixes or new features.  

<a name="git-head-git"></a>
### Using Git (all platforms)

1. Clone the get_iplayer repository

	`git clone git://github.com/dinkypumpkin/get_iplayer`

	The get_iplayer code will now be in a sub directory named `get_iplayer`, so use `cd get_iplayer` to navigate to that location.

2. Back up and replace existing CLI/WPM

	You may run both the CLI and WPM directly from the cloned repository. If you wish to update your existing installation:

	**Linux/Unix/OS X:** Proceed from step #2 in the [CLI manual installation procedure](#linux-manual-cli) or [WPM manual installation procedure](#linux-manual-wpm) as appropriate.  If you are replacing a package installation, it is recommended that you first remove the get_iplayer package (but leave external programs installed), then follow the manual installation procedure to install the Git HEAD version to /usr/local/bin (or similar).

	**Windows:** See the instructions [below](#git-head-windows).


<a name="git-head-linux"></a>
### Linux/Unix/OS X

#### Command-line Interface (CLI)

1. Download the Git HEAD version to working directory

    `curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer`

	NOTE: If your system does not have `curl` try `wget`.  Replace `curl -kLO` with `wget --no-check-certificate`.

2. Back up and replace existing CLI

	You may run the CLI from the download location. If you wish to replace your existing get_iplayer installation, proceed from step #2 in the [manual installation procedure](#linux-manual-cli) after first backing up your existing CLI.  

	If you are replacing a package installation, it is recommended that you first remove the get_iplayer package (but leave external programs installed), then follow the manual installation procedure to install the Git HEAD version to /usr/local/bin (or similar). 

#### Web PVR Manager (WPM)

1. Download the Git HEAD version to working directory

    `curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer.cgi`

	NOTE: If your system does not have `curl` try `wget`.  Replace `curl -kLO` with `wget --no-check-certificate`.

2. Back up and replace existing WPM

	You may run the WPM from the download location.  If you wish to replace your existing get_iplayer installation, proceed from step #2 in the [manual installation procedure](#linux-manual-wpm) after first backing up your existing WPM.  

	If you are replacing a package installation, it is recommended that you first remove the get_iplayer package (but leave external programs installed), then follow the manual installation procedure to install the Git HEAD version to /usr/local/bin (or similar).  
<a name="git-head-windows"></a>
### Windows

Windows lacks a built-in command line downloader, but you may install either [curl](http://www.paehl.com/open_source/?download=curl_730_0_ssl.zip) or [wget](http://downloads.sourceforge.net/gnuwin32/wget-1.11.4-1-setup.exe) yourself and use the download instructions for Linux/Unix/OS X above.  The only difference is that you should rename the CLI script from "get_iplayer" to "get_iplayer.pl" after downloading.  The instructions below describe an alternative method to download the files with your web browser.

Updating an existing Windows installation is different from updating a Linux/Unix/OS X installation.  Regardless of how you download the Git HEAD scripts, use the update instructions below.


#### Command-line Interface (CLI)

1. Download the development version to working directory

	Click link below to open file in your browser, then type Ctrl-S to save after file loads:

	<https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer>

	**NOTE:** Make sure the file is saved as a plain text file (Text Document). Your web browser may prompt you save the file as "get_iplayer.txt".  Change the file name to "get_iplayer.pl".  You may also rename the file after downloading.

2. Back up and replace existing CLI (requires admin privileges)

	``` bat
	copy C:\Program Files\get_iplayer\get_iplayer.pl get_iplayer.pl.bak
	copy get_iplayer.pl C:\Program Files\get_iplayer\get_iplayer.pl
	```

	NOTE: Replace `C:\Program Files` with `C:\Program Files (x86)` for 64-bit Windows.

#### Web PVR Manager (WPM)

1. Download the development version to working directory

	Click link below to open file in your browser, then type Ctrl-S to save after file loads:

	<https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer.cgi>

	**NOTE:** Make sure the file is saved as a plain text file (Text Document).  Your web browser may prompt you save the file as "get_iplayer.txt" or "get_iplayer.cgi.txt".  Change the file name to "get_iplayer.cgi".  You may also rename the file after downloading.

2. Back up and replace existing WPM (requires admin privileges)

	``` bat
	copy C:\Program Files\get_iplayer\get_iplayer.cgi get_iplayer.cgi.bak
	copy get_iplayer.cgi C:\Program Files\get_iplayer\get_iplayer.cgi
	```

	NOTE: Replace `C:\Program Files` with `C:\Program Files (x86)` for 64-bit Windows.
