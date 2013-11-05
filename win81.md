## Windows 8.1

### Web PVR Manager and Internet Explorer 11

The Web PVR Manager may not launch properly with Internet Explorer 11 after you upgrade your system to Windows 8.1.  Instead, IE 11 may display the error message "This page can’t be displayed".  This is due to IE 11's Enhanced Protected Mode, which blocks access to servers running on the machine's loopback address (127.0.0.1).  By default, the Web PVR Manager's server component runs on the loopback address at: `http://127.0.0.1:1935`.  If you encounter this error, download the updated get_iplayer installer from:

<http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe>

and re-install get_iplayer.  When you run the installer, select only the "get_iplayer" component for re-installation.  There is no need to re-install the helper applications.  After re-installing get_iplayer, the Web PVR Manager shortcut will launch your browser directed to `http://localhost:1935`.

#### Notes

* You do not need to re-install get_iplayer if you do not use IE 11.  This issue does not pertain to Chrome or Firefox.
* You do not need to re-install get_iplayer if you do not use Windows 8.1.  This issue does not pertain to Windows 8 and earlier.  Not yet, at least.
* Do not disable Enhanced Protection Mode unless you have another reason to do so.  Re-install get_iplayer instead.