## Git HEAD - Linux/Unix/OS X

"Git HEAD" is the latest development version of get_iplayer from the Git repository. There may be occasions when you wish to use the Git HEAD version of get_iplayer in order to test bug fixes or new features.

### Command-line Interface (CLI)

1. Download the Git HEAD version to working directory

	    curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer

	Alternate location:

		curl -KLO http://git.infradead.org/get_iplayer.git/blob_plain/master:/get_iplayer

	NOTE: If your system does not have `curl` try `wget`.  Replace `curl -kLO` with `wget --no-check-certificate`.

2. Back up and replace existing CLI

	You may run the CLI from the download location. If you wish to replace your existing get_iplayer installation, proceed from step #2 in the CLI [[manual installation procedure|manual]] after first backing up your existing CLI.  

	If you are replacing a package installation, it is recommended that you first remove the get_iplayer package (but leave external programs installed), then follow the manual installation procedure to install the Git HEAD version to /usr/local/bin (or similar). 

#### Web PVR Manager (WPM)

1. Download the Git HEAD version to working directory

		curl -kLO https://raw.github.com/dinkypumpkin/get_iplayer/master/get_iplayer.cgi

	Alternate location:

		curl -KLO http://git.infradead.org/get_iplayer.git/blob_plain/master:/get_iplayer.cgi
		
	NOTE: If your system does not have `curl` try `wget`.  Replace `curl -kLO` with `wget --no-check-certificate`.

2. Back up and replace existing WPM

	You may run the WPM from the download location.  If you wish to replace your existing get_iplayer installation, proceed from step #2 in the WPM [[manual installation procedure|manual]] after first backing up your existing WPM.  

	If you are replacing a package installation, it is recommended that you first remove the get_iplayer package (but leave external programs installed), then follow the manual installation procedure to install the Git HEAD version to /usr/local/bin (or similar).  

