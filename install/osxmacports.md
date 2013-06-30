## get_iplayer Installation - OS X - MacPorts

get_iplayer is not packaged in [MacPorts](http://www.macports.org). However, MacPorts provides all the dependencies required for get_iplayer on OS X.  Install MacPorts using the instructions [here](http://www.macports.org/install.php).  You can use the "pkg" installer for your system.

### Perl Support

Because MacPorts is a self-contained system, you must install the MacPorts build of Perl (it will be pulled in as a dependency of other packages anyway), which will become your default Perl.  If you use other Perl applications that current rely on the system Perl distributed with OS X, be sure to install any modules required for those applications into the MacPorts Perl library.  If you find you need to switch between multiple Perl installations, take a look at [Perlbrew](http://perlbrew.pl).

1. Install Perl
 
		sudo port install perl5

    This installs the default Perl version (currently 5.12). If you wish to install a newer version such as 5.16, add the necessary variant flag:

		sudo port install perl5 +perl5_16

2. Install Perl modules

		sudo port install p5-libwww-perl p5-xml-simple p5-mp3-tag p5-mp3-info

3. The Perl modules to support secure email are not packaged in  MacPorts.  However, they can be installed with a [CPAN](http://www.cpan.org) client into the MacPorts Perl library:

		sudo cpan Net::SMTP::SSL Authen::SASL Net::SMTP::TLS::ButMaintained


### External Programs

1. Install external programs (except ffmpeg)

		sudo port install rtmpdump mplayer atomicparsley id3v2

2. Install ffmpeg

		sudo port install ffmpeg

    This example pulls in X11, Python and other dependencies you may not want or need.  If you want a slimmed-down installation of ffmpeg, use the "no_X11" variant:

		sudo port install ffmpeg +no_x11
    
### Command-line Interface (CLI)

Use the CLI [manual installation procedure](manual) described for Linux/Unix.

### Web PVR Manager (WPM)

Use the WPM [manual installation procedure](manual) described for Linux/Unix.
