## Debian

These instructions are for Debian 7 (stable, wheezy).  Information for Debian 6 (squeeze) can be found [[here|debian6]].

### Command-line Interface (CLI)

1. Install get-iplayer package (note that package name contains hyphen, not underscore)

	    sudo apt-get install get-iplayer

2. Install components not installed with get-iplayer package

    	sudo apt-get install ffmpeg mplayer libmp3-tag-perl libnet-smtp-ssl-perl libauthen-sasl-perl

3. The packaged Perl modules for secure email with TLS in Debian 7.0 are currently incompatible with the packaged version of IO::Socket::SSL.  If TLS is your only secure email option, you can use the [[local::lib method|manual] to create a local Perl module library and install the necessary module:

		cpanm Net::SMTP::TLS::ButMaintained

4. Run CLI with:

		get_iplayer […]


### Web PVR Manager (WPM)

The WPM is installed along with the CLI.

1. Launch the WPM with:

    `get_iplayer_web_pvr`

2. Once the WPM is running, connect to it by opening this URL in your browser:

    <http://127.0.0.1:1935>

3. Stop the WPM by typing Ctrl-C.

<a name="linux-package-debian-testing"></a>
### Update to Debian Testing/Unstable Version

If you should ever need to update to a get-iplayer package that is newer than the one provided in Debian stable, you can download and install the Debian testing/unstable package directly.  Although installing packages from testing on a stable system is often discouraged, it is currently safe to do so with the get-iplayer package.

1. Check the package and make sure that dependencies have not changed

	<http://packages.debian.org/stable/get-iplayer>

	Switch to the testing/unstable package pages using the links at the top right of the page.
	
2. If the dependencies still look OK, download the Debian testing/unstable get-iplayer package from your preferred mirror

    <http://packages.debian.org/testing/all/get-iplayer/download>

    <http://packages.debian.org/unstable/all/get-iplayer/download>

3. Remove just the old get-iplayer package

		sudo dpkg -r get-iplayer

4. Install the downloaded DEB file (version 2.83-1 in this example)

    	sudo dpkg -i get-iplayer_2.83-1_all.deb

	Only the get-iplayer package will be updated, so this method assumes that dependencies have not changed in the newer package.

