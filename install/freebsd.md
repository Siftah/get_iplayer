## FreeBSD / PC-BSD

These instructions are for FreeBSD 9.1 / PC-BSD 9.1-RELEASE using `pkgng`.

### Command-line Interface (CLI)

#### PC-BSD Only

PC-BSD offers get_iplayer packaged in PBI format, which you can install with AppCafe or with:

	sudo pbi_add -r get_iplayer

If you install the PBI package, you must skip steps #1 and #2 below.

**NOTE:** The PBI version of get_iplayer is only available for 64-bit PC-BSD.  If you have a 32-bit version of PC-BSD 9.1 (released before 32-bit builds were discontinued in June 2013), **do not** install the get_iplayer 2.82 PBI - it is broken.

1. Install Perl

		sudo pkg install perl

    NOTE: Perl will likely already be installed if you installed a desktop environment.

2. Install get_iplayer port

	Before building the get_iplayer port you must retrieve the ports tree:

		sudo portsnap fetch
		sudo portsnap extract
	
	Install dependencies to avoid unnecessary builds:

		sudo pkg install p5-libwww rtmpdump

	Install get_iplayer port:

		cd /usr/ports/net/get_iplayer
		sudo make install clean

3. Install Perl modules

		sudo pkg install p5-MP3-Tag p5-MP3-Info p5-XML-Simple p5-Net-SMTP-SSL p5-Net-SMTP-TLS

4. Install external programs (except ffmpeg)

		sudo pkg install AtomicParsley id3v2 mplayer

5. Install ffmpeg

	FreeBSD/PC-BSD offers two packaged versions of ffmpeg.  Version 0.7.x is packaged as *ffmpeg*, while version 1.x is packaged as *ffmpeg1*.  Install with:

		sudo pkg install ffmpeg

	OR

		sudo pkg install ffmpeg1

	NOTE: The *ffmpeg* package may already be installed if you installed a desktop environment.  Don't remove it - other packages depend on it.

	Although newer versions of ffmpeg are preferred, the 0.7.x build should still work with get_iplayer.    If you install the *ffmpeg1* package, you will need to configure get_iplayer to look for the `ffmpeg1` program:

		get_iplayer --prefs-add --ffmpeg=ffmpeg1

	**FreeBSD Only:** The `--aactomp3` option for get_iplayer will not work with either of the ffmpeg packages since they are not built with the LAME MP3 encoder.

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

	Open the WPM service script (`/usr/local/etc/rc.d/get_iplayer`) in a text editor.  The last line of the script should be:

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

6. After the WPM has opened in your browser, click the `Refresh Cache` button.  A new tab or window will open that shows the cache being refreshed.  Leave that tab or window open to have the cache refreshed automatically every hour.  You can also manually refresh the cache at any time.