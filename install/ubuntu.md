## Ubuntu

These instructions are for Ubuntu 13.10 (Saucy Salamander).

The get-iplayer versions incorporated in Ubuntu repositories are nearly always out of date or broken, so Ubuntu users should install from the get_iplayer PPA.  Ubuntu editions that have [reached end-of-life](https://wiki.ubuntu.com/Releases) should use the [manual installation procedure](manual).

### get_iplayer PPA

The [get-iplayer PPA](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer) (Personal Package Archive) is maintained by Jon Davies.  Packages with up-to-date versions of get_iplayer and dependencies are available for supported Ubuntu releases from 10.04 onwards.

### Command-line Interface (CLI)

1. Add the PPA repository

        # If you do not have apt-add-repository on your system, first install python-software-properties
        sudo apt-get install python-software-properties

    	sudo apt-add-repository ppa:jon-hedgerows/get-iplayer

2. Ensure package database is current

    	sudo apt-get update

3. Install get_iplayer from PPA with dependencies:

    	sudo apt-get install get-iplayer
    
    You may install from the PPA over an existing get_iplayer installation from the Ubuntu repositories.  Dependencies will be updated if necessary.

4. Install additional dependencies

        sudo apt-get install mplayer libavcodec-extra-53

    Installing the libavcodec-extra-53 and dependent libavutil-extra-51 packages will replace the libavcodec53 and libavutil51 packages if already installed.  The "extra" version is required for MP3 encoding.  NOTE: The version number (53) may be different in earlier or later editions of Ubuntu.

5. Run CLI with:

    	get_iplayer […]

If you wish to remove the PPA packages and roll back any updates:

    # If you do not have ppa-purge on your system, first install it
    sudo apt-get install ppa-purge

    sudo ppa-purge ppa:jon-hedgerows/get-iplayer

### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM in with this command:

    	get_iplayer_web_pvr

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. After the WPM has opened in your browser, click the `Refresh Cache` button.  A new tab or window will open that shows the cache being refreshed.  Leave that tab or window open to have the cache refreshed automatically every hour.  You can also manually refresh the cache at any time.

4. Stop the WPM by typing Ctrl-C.