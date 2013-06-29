
## Git HEAD - Windows

"Git HEAD" is the latest development version of get_iplayer from the Git repository. There may be occasions when you wish to use the Git HEAD version of get_iplayer in order to test bug fixes or new features.

Windows lacks a built-in command line downloader, but you may install either [curl](http://www.paehl.com/open_source/?download=curl_730_0_ssl.zip) or [wget](http://downloads.sourceforge.net/gnuwin32/wget-1.11.4-1-setup.exe) yourself and use the [[download instructions for Linux/Unix/OS X|githeadunix]].  The only difference is that you should rename the CLI script from "get_iplayer" to "get_iplayer.pl" after downloading.  The instructions below describe an alternative method to download the files with your web browser.

Updating an existing Windows installation is different from updating a Linux/Unix/OS X installation.  Regardless of how you download the Git HEAD scripts, use the update instructions below.

#### Command-line Interface (CLI)

1. Download the development version to working directory

	Click link below to open file in your browser, then type Ctrl-S to save after file loads:

	<https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer>

	Alternate location:

	<http://git.infradead.org/get_iplayer.git/blob_plain/master:/get_iplayer>
	
	**NOTE:** Make sure the file is saved as a plain text file (Text Document). Your web browser may prompt you save the file as "get_iplayer.txt".  Change the file name to "get_iplayer.pl".  You may also rename the file after downloading.

2. Back up and replace existing CLI (requires admin privileges)

		copy "C:\Program Files\get_iplayer\get_iplayer.pl" get_iplayer.pl.Bak
		copy get_iplayer.pl "C:\Program Files\get_iplayer\get_iplayer.pl"

	NOTE: Replace `C:\Program Files` with `C:\Program Files (x86)` for 64-bit Windows.

#### Web PVR Manager (WPM)

1. Download the development version to working directory

	Click link below to open file in your browser, then type Ctrl-S to save after file loads:

	<https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer.cgi>

	Alternate location:

	<http://git.infradead.org/get_iplayer.git/blob_plain/master:/get_iplayer.cgi>

	**NOTE:** Make sure the file is saved as a plain text file (Text Document).  Your web browser may prompt you save the file as "get_iplayer.txt" or "get_iplayer.cgi.txt".  Change the file name to "get_iplayer.cgi".  You may also rename the file after downloading.

2. Back up and replace existing WPM (requires admin privileges)

		copy "C:\Program Files\get_iplayer\get_iplayer.cgi" get_iplayer.cgi.bak
		copy get_iplayer.cgi "C:\Program Files\get_iplayer\get_iplayer.cgi"

	NOTE: Replace `C:\Program Files` with `C:\Program Files (x86)` for 64-bit Windows.