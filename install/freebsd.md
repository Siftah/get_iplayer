## FreeBSD / PC-BSD

These instructions are for FreeBSD / PC-BSD 9.1.

### Command-line Interface (CLI)

If you have converted your system to use *pkgng*, replace `pkg_add -r` to `pkg install` in the instructions below.

#### PC-BSD Only

**2013-06-23: The PBI version of get_iplayer has not yet been updated to version 2.83 and consequently cannot download BBC TV programmes.  Until the PBI version is updated, build the get_iplayer port as described below.**

PC-BSD offers get_iplayer packaged in PBI format, which you can install with AppCafe or with:

	sudo pbi_add -r get_iplayer

If you install the PBI package, you may skip steps #1 and #2.

1. Install Perl

		pkg_add -r perl

    NOTE: Perl may already be installed if you installed a desktop environment.

2. Install get_iplayer port

	Before building the get_iplayer port you must retrieve the ports tree:

		sudo portsnap fetch
		sudo portsnap extract
	
	Install flvstreamer to avoid building it along with get_iplayer port:

		pkg_add -r flvstreamer

	Install get_iplayer port:

		cd /usr/ports/net/get_iplayer
		make install clean

3. Install Perl modules

		sudo pkg_add -r p5-MP3-Tag p5-MP3-Info p5-XML-Simple p5-Net-SMTP-SSL p5-Net-SMTP-TLS

4. Install external programs (except ffmpeg)

		sudo pkg_add -r rtmpdump AtomicParsley id3v2 mplayer

5. Install ffmpeg

	FreeBSD/PC-BSD offers two packaged versions of ffmpeg.  Version 0.7.x is packaged as *ffmpeg*, while version 1.0.x is packaged as *ffmpeg1*.  Install with:

		sudo pkg_add -r ffmpeg

	OR

		sudo pkg_add -r ffmpeg1

	NOTE: The *ffmpeg* package may already be installed if you installed a desktop environment.  Don't remove it - other packages depend on it.

	Although newer versions of ffmpeg are preferred, the 0.7.x build should still work with get_iplayer.    If you install the *ffmpeg1* package, you will need to configure get_iplayer to look for the `ffmpeg1` program:

		get_iplayer --prefs-add --ffmpeg=ffmpeg1

	**NOTE:** The `--aactomp3` option for get_iplayer will not work with either of the ffmpeg packages since they are not built with the LAME MP3 encoder.

6. Run CLI:

        get_iplayer [...]

### Web PVR Manager (WPM)

The WPM is installed as a system service, but it requires additional configuration and a small patch to work, as described below.  You may also use the [manual installation procedure](manual).

1. Create a location to store preferences, caches, and downloads

	As installed, the WPM will not work because it does not have a writeable location configured for get_iplayer preferences and caches.  The default download location is /tmp, which means your downwloads would be wiped on reboot.

	Create a working directory for the WPM service with the commands below.  The WPM service runs as the *get_iplayer* user, so the directory must be writable by that user.
	 	
		sudo mkdir /usr/home/get_iplayer
		sudo chown get_iplayer:get_iplayer /usr/home/get_iplayer

2. Patch the WPM service script

	The rtmpdump utility requires that the HOME environment variable point to a writeable location in order to store the `.swfinfo` file used for SWF verification.  get_iplayer also uses HOME to locate preferences and caches.  The WPM service runs as the *get_iplayer* user, but HOME is set for the *root* user and cannot be written by the WPM.  The effect is that no caches can be saved and thus no programmes appear in the WPM search results.  SWF verification also will fail.

	Open the WPM service script (`/usr/local/etc/rc.d/get_iplayer`) in an editor.  The last line of the script should be:

		run_rc_command "$1"

	Insert the line below immediately **before** the last line:

		export HOME="${get_iplayer_chdir}"

	The last two lines in the script should now be:

		export HOME="${get_iplayer_chdir}"
		run_rc_command "$1"

	Save the edited file.

	These changes have the effect of setting HOME for the WPM service script to the working directory created in #1.  The *get_iplayer* user - and thus the WPM service and rtmpdump - can write to that location.  Preferences and caches for the *get_iplayer* user can be stored and the WPM will work correctly.

3. Configure the WPM service

	Add the following lines to /etc/rc.conf:
	
		get_iplayer_enable="YES"
		get_iplayer_chdir="/usr/home/get_iplayer"
		get_iplayer_bind_port="1935"

	These settings:
	* Enable the WPM service.  It will now start at boot time.
	* Set the WPM working directory.  This is where downloads will be saved by default.
	* Set the port where the WPM listens for connections.  The default value in the FreeBSD port is 9370, but has been reset here to 1935, the value typically used on other platforms. Port 1935 is used to support RTMP streaming from the WPM.  If you don't require that functionality, you can omit the `get_iplayer_bind_port` setting and keep the default port.
	
4. Start the WPM service

		sudo service get_iplayer start

5. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

	OR
  
	<http://127.0.0.1:9370>

	if you kept the default FreeBSD port setting.
