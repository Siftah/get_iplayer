## FreeBSD / PC-BSD

These instructions are for FreeBSD / PC-BSD 9.1.

### Command-line Interface (CLI)

**FreeBSD Only** 

Perl is not part of the base system install, so install it first with:

	pkg_add -r perl

**PC-BSD Only** 

 PC-BSD offers get_iplayer packaged in PBI format, which you can install with AppCafe or with:

	pbi_add -r get_iplayer

If you install the PBI package, you may skip step #1.

1. Install get_iplayer port

	NOTE: Before building the get_iplayer port you must update your ports tree with portsnap.
	
	First install flvstreamer to avoid building it along with get_iplayer port:

		pkg_add -r flvstreamer

	Install get_iplayer port:

		cd /usr/ports/net/get_iplayer
		make install clean

2. Install Perl modules

		pkg_add -r p5-MP3-Tag p5-MP3-Info p5-XML-Simple p5-Net-SMTP-SSL p5-Net-SMTP-TLS

3. Install external programs (except ffmpeg)

		pkg_add -r rtmpdump ffmpeg AtomicParsley id3v2 mplayer

4. Install ffmpeg

	FreeBSD/PC-BSD offers two versions of ffmpeg.  Version 0.7.x is packaged as `ffmpeg`, while version 1.0.x is packaged as `ffmpeg1`.  Install with:

		pkg_add -r ffmpeg
	OR
		
		pkg_add -r ffmpeg1

	Although newer versions of ffmpeg are preferred, the 0.7.x build should still work with get_iplayer.  If you wish to use the 1.0.x build, you will need to configure get_iplayer to look for the `ffmpeg1` program:

		get_iplayer --prefs-add --ffmpeg=ffmpeg1


### Web PVR Manager (WPM)

The WPM is not installed with the get_iplayer package.  Use the [manual installation procedure](manual).

