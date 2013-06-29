## OpenBSD

These instructions are for OpenBSD 5.3.

### Command-line Interface (CLI)

1. Install get_iplayer package and dependencies

	    sudo pkg_add get_iplayer
    
2. Install components not installed with get_iplayer package

    	sudo pkg_add ffmpeg mplayer p5-Net-SMTP-SSL p5-Authen-SASL p5-Net-SMTP-TLS-ButMaintained

3. Run CLI with:

    	get_iplayer […]

NOTE: If you use SSL email, you may see a deprecation warning about the use of SSL_verify_mode, a parameter used by the IO::Socket::SSL module.  However, your emails should still be transmitted successfully.

### Web PVR Manager (WPM)

The WPM is not installed with the get_iplayer package.  Use the [[manual installation procedure|manual]].

