## Instructions for using patched get_iplayer script

1. **Download from the Git repository**

    The Git repository incorporates changes to get_iplayer made since the last formal release. You should first check the change log at the master repository to see if the feature or fix you need has been incorporated:

    <http://git.infradead.org/get_iplayer.git/log>

    If so, go to this URL in your web browser:
    
    <http://git.infradead.org/get_iplayer.git/blob_plain/HEAD:/get_iplayer>

    You should see the full script in the browser window.
    
    Use **File->Save As** (or equivalent for your browser) to save the script to your local disk.
    
    You can also point curl, wget, etc. at the above URL.
    
    **NOTE:** Your browser may save the downloaded file as _get\_iplayer.txt_ or _get\_iplayer.pl.txt_.  Be aware of this when you look for the file to use it as a replacement for the current script (see below).

2. **Locate the current get\_iplayer script**
   
    If you're on Windows and you used the get\_iplayer installer, the current script will be:
    
    **Windows 32-bit**:

    `C:\Program Files\get_iplayer\get_iplayer.pl`

    **Windows 64-bit**:

    `C:\Program Files (x86)\get_iplayer`
    
    **Windows 7 / Vista**: First look for the `get_iplayer.pl` file in:

    `C:\Users\<username>\AppData\Local\VirtualStore\Program Files\get_iplayer`

    OR

    `C:\Users\<username>\AppData\Local\VirtualStore\Program Files (x86)\get_iplayer`

    If that file exists, it is the version currently in use, *NOT* the version of `get_iplayer.pl` in `C:\Program Files\get_iplayer` or `C:\Program Files (x86)\get_iplayer`.  The copy in the VirtualStore directory most likely will have resulted from `get_iplayer.pl` updating itself without the use of the Windows installer.  This triggers the Windows file virtualisation mechanism that redirects access for `get_iplayer.pl` to the virtual store copy.  If this is the case, you may either:

    * Replace the virtual store copy of `get_iplayer.pl` directly.  However, it may be overwritten if `get_iplayer.pl` ever updates itself again without using the Windows installer.
    * Re-install the `get_iplayer` component in the Windows installer.  That will remove the virtual store copy in the process.  You can then replace `C:\Program Files\get_iplayer\get_iplayer.pl` directly, so long as you have admin privileges on your machine. 

    Note that in the Windows installer version, the `get_iplayer.pl` script is invoked from a batch file:
    
    `C:\Program Files\get_iplayer\get_iplayer.cmd`
    
    Only the **.pl** file will be replaced.
    
    If you're on Windows and you did not use the get\_iplayer installer (e.g., you're using Cygwin), only you will know where the script is located.  In this case, the file is most likely to be named _get\_iplayer_ (no .pl extension).
    
    If you're on Linux/OSX, again, only you will know where the script is located.  In this case, the file will almost certainly be named _get\_iplayer_.
    
3. **Replace the current script**
    
    Back up the current script that you located above and replace it with the new downloaded script.  Be sure to give the new script file the same name as the current script (Windows:  _get\_iplayer.pl_, Linux/OSX:  _get\_iplayer_ ).
    
    If you're on Linux/OSX, you may want to ensure the new script is executable by running the following command from a shell prompt:
    
    `chmod a+x <insert script location here>`
    
    or, if the script is in your PATH:
    
    ``chmod a+x `which get_iplayer` ``
