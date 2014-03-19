## OpenBSD

These instructions are for OpenBSD 5.3.

### Command-line Interface (CLI)

1. Install get_iplayer 2.82 package and dependencies from release repository (assumes PKG_PATH configured)

        sudo pkg_add get_iplayer

2. Update to get_iplayer package (use current version and tarball) from snapshots repository (select different mirror if appropriate)

        sudo pkg_add http://www.mirrorservice.org/pub/OpenBSD/snapshots/packages/`machine -a`/get_iplayer-2.83.tgz
    
3. Install components not installed with get_iplayer package

        sudo pkg_add ffmpeg mplayer p5-Net-SMTP-SSL p5-Authen-SASL p5-Net-SMTP-TLS-ButMaintained

4. Run CLI with:

    	get_iplayer […]

NOTE: If you use SSL email, you may see a deprecation warning about the use of SSL_verify_mode, a parameter used by the IO::Socket::SSL module.  However, your emails should still be transmitted successfully.

### Web PVR Manager (WPM)

The WPM is not installed with the get_iplayer package.  Use the [[manual installation procedure|manual]].