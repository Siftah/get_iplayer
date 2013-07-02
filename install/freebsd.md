## FreeBSD / PC-BSD

These instructions are for FreeBSD / PC-BSD 9.1.

### Command-line Interface (CLI)

**PC-BSD Only** 

**2013-06-23: The PBI version of get_iplayer has not yet been updated to version 2.83 and consequently cannot download BBC TV programmes.  Until the PBI version is updated, build the get_iplayer port as described below.  Alternatively, please see [this page](swfurl) for instructions on configuring get_iplayer to restore the TV downloads.**

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

Use the [manual installation procedure](manual).