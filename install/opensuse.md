## openSUSE

These instructions are for openSUSE 13.1.

### Command-line Interface (CLI)

1. Install restricted formats support according to the instructions here:

    <http://opensuse-community.org/Restricted_formats>
    
    The Packman repository should now be added to your system.  The ffmpeg utility also will have been installed.

2. Update package database

    	sudo zypper refresh

3. Install get_iplayer package and dependencies

    The get_iplayer package in the [Packman](http://packman.links2linux.org/package/get_iplayer) repository has not been updated to 2.83+ and thus should not be used.  You can find an updated package supplied through the openSUSE Build Service: 

    <http://software.opensuse.org/package/get_iplayer>

    Although labelled as unstable, the package should be safe to install. You may opt for one-click installation, or you may download the RPM file and install it manually (use current version and rpm):

    	sudo zypper install get_iplayer-2.85-5.1.noarch.rpm

4. Install components not installed with get_iplayer package

    	sudo zypper install perl-MP3-Tag perl-Net-SMTP-SSL perl-Authen-SASL id3v2

5. The official openSUSE repositories do not provide packages for AtomicParsley and MP3::Info, nor do they provide packaged Perl modules to support TLS secure email.  You can find third-party packages supplied through the openSUSE Build Service: 

    <http://software.opensuse.org/package/AtomicParsley>

    <http://software.opensuse.org/package/perl-MP3-Info>
    
    <http://software.opensuse.org/package/perl-Net-SMTP-TLS>

    Although labelled as unstable, these packages should be safe to install. You may opt for one-click installation, or you may download the RPM files and install them manually (amend file names as needed):

    	sudo zypper install AtomicParsley-0.9.2+svn110-3.1.i586.rpm

    NOTE: Download the correct AtomicParsley RPM for your system architecture.

        sudo zypper install perl-MP3-Info-1.23-7.1.i586.rpm

    NOTE: Download the correct MP3::Info RPM for your system architecture.

    	sudo zypper install perl-Net-SMTP-TLS-0.12-6.1.noarch.rpm

6. Run CLI with:

    	get_iplayer […]


### Web PVR Manager (WPM)

1. Install CLI as described above

2. Install WPM package and dependencies

    The get_iplayer-pvr package in the [Packman](http://packman.links2linux.org/package/get_iplayer) repository has not been updated to 2.83+ and thus should not be used.  You can find an updated package supplied through the openSUSE Build Service: 

    <http://software.opensuse.org/package/get_iplayer-pvr>

    Although labelled as unstable, the package should be safe to install. You may opt for one-click installation, or you may download the RPM file and install it manually  (use current version and rpm):

    	sudo zypper install get_iplayer-pvr-2.85-1.1.noarch.rpm

3. Launch the WPM in a terminal window with this command:

    	get_iplayer_pvr
    
    The WPM will open in a new xterm and your default browser will open to this URL:
    
    <http://127.0.0.1:1935>

    **NOTE:** As of v2.83, this no longer works due to changes in the WPM.  You will see several messages saying "The web pvr was unable to start." and your browser will not open.  However, the WPM actually will have started.  You can connect to it in your browser by clicking the URL above or entering the address in your web browser.

4. After the WPM has opened in your browser, click the `Refresh Cache` button.  A new tab or window will open that shows the cache being refreshed.  Leave that tab or window open to have the cache refreshed automatically every hour.  You can also manually refresh the cache at any time.

5. Stop the WPM by typing Ctrl-C in the xterm where it is running.