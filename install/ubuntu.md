## Ubuntu

These instructions are for Ubuntu 13.04 (Raring Ringtail).


Although the Debian get-iplayer package is incorporated in Ubuntu repositories, Ubuntu users are recommended to use the get_iplayer PPA version.  If you must use the Ubuntu package, refer to the [[Debian instructions|debian]]. The only change for Ubuntu is that you should additionally install the `libnet-smtp-tls-butmaintained-perl` package.  

Ubuntu LTS (Long Term Support) releases such as 12.04 (Precise Pangolin) will very likely have obsolete get-iplayer packages in their repositories.  Please use the PPA version instead.  Ubuntu editions that have [reached end-of-life](https://wiki.ubuntu.com/Releases) should use the [][manual installation procedure|manual]].

### get_iplayer PPA

The [get-iplayer PPA](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer) (Personal Package Archive) is maintained by Jon Davies.  Packages with up-to-date versions of get_iplayer and dependencies are available for supported Ubuntu releases from 10.04 onwards.

### Command-line Interface (CLI)

1. Add the PPA repository

    	sudo apt-add-repository ppa:jon-hedgerows/get-iplayer

2. Ensure package database is current

    	sudo apt-get update

3. Install get_iplayer and all dependencies from PPA:

    	sudo apt-get install get-iplayer
    
    You may install from the PPA over an existing get_iplayer installation from the Ubuntu repositories.  Dependencies will be updated if necessary.

4. Install components not installed with get-iplayer package

	    sudo apt-get install libnet-smtp-ssl-perl libauthen-sasl-perl libnet-smtp-tls-butmaintained-perl

5. Run CLI with:

    	get_iplayer […]

If you wish to remove the PPA packages and roll back any updates:

	sudo ppa-purge ppa:jon-hedgerows/get-iplayer

### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM in with this command:

    	get_iplayer_web_pvr

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

