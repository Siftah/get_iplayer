## Homebrew

Full information on installing get_iplayer with [Homebrew](http://mxcl.github.com/homebrew/) can be found here:

<https://github.com/dinkypumpkin/homebrew-get_iplayer/wiki>

### Perl Support

Homebrew is designed to work with the system Perl installed with OS X, so no additional Perl installation is required.  The OS X system Perl already includes the LWP and XML::Simple modules. Additional Perl modules may be installed using the [[local::lib method|manual]] described for Linux/Unix.  

### External Programs

All external programs can be installed with the get_iplayer package, as noted below.  They may also be installed separately:

	brew update
	brew install rtmpdump ffmpeg mplayer atomicparsley id3v2

### Command-line Interface (CLI)

Install get_iplayer and all related external programs with:

	brew tap dinkypumpkin/get_iplayer
	brew update
	brew install --with-deps get_iplayer

### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM with:

    	get_iplayer_web_pvr

2. The WPM will launch in a `screen` session and your default browser will be opened to this URL:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.
