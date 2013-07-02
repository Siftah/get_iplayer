## openSUSE

These instructions are for openSUSE 12.3.

**2013-06-23: The openSUSE get_iplayer package has not yet been updated to version 2.83 and consequently cannot download BBC TV programmes.  Until the package is updated, please see [this page](swfurl) for instructions on configuring get_iplayer to restore the TV downloads.**

### Command-line Interface (CLI)

The CLI package for openSUSE is maintained in the [Packman](http://packman.links2linux.org/package/get_iplayer) repository.

1. Install restricted formats support according to the instructions here:

    <http://opensuse-community.org/Restricted_formats>
    
    The Packman repository should now be added to your system.  The ffmpeg utility also will have been installed.

2. Update package database

    	sudo zypper update

3. Install get_iplayer package and dependencies

    	sudo zypper install get_iplayer

4. Install components not installed with get_iplayer package

    	sudo zypper install perl-MP3-Tag perl-Net-SMTP-SSL perl-Authen-SASL

5. The official openSUSE repositories do not provide packages for AtomicParsley, nor do they provide packaged Perl modules to support TLS secure email.  You can find third-party packages supplied through the openSUSE Build Service: 

    <http://software.opensuse.org/package/AtomicParsley>
    
    <http://software.opensuse.org/package/perl-Net-SMTP-TLS>

    Although labelled as unstable, these packages should be safe to install. You may opt for one-click installation, or you may download the RPM files and install them manually:

    	sudo zypper install AtomicParsley-0.9.2+svn110-3.1.i586.rpm

    NOTE: Download the correct AtomicParsley RPM for your system architecture.

    	sudo zypper install perl-Net-SMTP-TLS-0.12-6.1.noarch.rpm

    If you opt for one-click installation, the initial "Additional Software Repositories" screen will display an option to "Remain subscribed to these repositories after installation".  Since these are one-off installations, uncheck that option.

	There is no packaged version of id3v2 available, but you will not require it with the MP3::Tag module installed.

6. Run CLI with:

    	get_iplayer […]


### Web PVR Manager (WPM)

The WPM is maintained in a separate package in the [Packman](http://packman.links2linux.org/package/get_iplayer) repository. 

1. Install CLI as described above

2. Install WPM package and dependencies

    	sudo zypper install get_iplayer-pvr

3. Launch the WPM with:

    	get_iplayer_pvr
    
    The WPM will open in a new xterm and your default browser will open to this URL:
    
    <http://127.0.0.1:1935>

4. Stop the WPM by typing Ctrl-C in the xterm where it is running.
