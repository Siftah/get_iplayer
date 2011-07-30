## Instructions for using patched get_iplayer script

1. **Check master repository first**

    You should first check the change log at the master repository to see if the feature or fix you need has been incorporated:

    <http://git.infradead.org/get_iplayer.git/log>

    If so, go to this URL in your web browser:
    
    <http://git.infradead.org/get_iplayer.git/blob_plain/HEAD:/get_iplayer>

    You should see the full script in the browser window.
    
    Use **File->Save As** (or equivalent for your browser) to save the script to your local disk.
    
    You can also point curl, wget, etc. at the above URL.
    
    **NOTE:** Your browser may save the downloaded file as _get\_iplayer.txt_ or _get\_iplayer.pl.txt_.  Be aware of this when you look for the file to use it as a replacement for the current script (see below).

    If the fix for your problem is not in the master repository, proceed to Step 2 below to obtain the patched version of get_iplayer available here.

2. **Make sure you need the patched version**

    The patched version of get_iplayer in this repository may contain patches not yet incorporated into the master version (see above).  Check the change log for the patched version to make sure that the feature or fix you need has been incorporated:

    <https://github.com/dinkypumpkin/get_iplayer/commits/master/>

    If so, proceed to Step 3 below.  If not, send a post to the mailing list about your particular issue:

    <http://lists.infradead.org/mailman/listinfo/get_iplayer>

3. **Download the new script**
    
    Go to this URL in your web browser:
    
    <https://github.com/dinkypumpkin/get_iplayer/raw/master/get_iplayer>

    You should see the full script in the browser window.
    
    Use **File->Save As** (or equivalent for your browser) to save the script to your local disk.
    
    You can also point curl, wget, etc. at the above URL.
    
    **NOTE:** Your browser may save the downloaded file as _get\_iplayer.txt_ or _get\_iplayer.pl.txt_.  Be aware of this when you look for the file to use it as a replacement for the current script (see below).

4. **Locate the current script**
   
    If you're on Windows and you used the get\_iplayer installer, the current script will almost certainly be:
    
    `C:\Program Files\get_iplayer\get_iplayer.pl`
    
    Note that in the Windows installer version, the above script is invoked from a batch file:
    
    `C:\Program Files\get_iplayer\get_iplayer.cmd`
    
    Only the **.pl** file will be replaced.
    
    If you're on Windows and you did not use the get\_iplayer installer (e.g., you're using Cygwin), only you will know where the script is located.  In this case, the file is most likely to be named _get\_iplayer_ (no .pl extension).
    
    If you're on Linux/OSX, again, only you will know where the script is located.  In this case, the file will almost certainly be named _get\_iplayer_.
    
5. **Replace the current script**
    
    Back up the current script that you located above and replace it with the new downloaded script.  Be sure to give the new script file the same name as the current script (Windows:  _get\_iplayer.pl_, Linux/OSX:  _get\_iplayer_ ).
    
    If you're on Linux/OSX, you may want to ensure the new script is executable by running the following command from a shell prompt:
    
    `chmod a+x <insert script location here>`
    
    or, if the script is in your PATH:
    
    ``chmod a+x `which get_iplayer` ``
