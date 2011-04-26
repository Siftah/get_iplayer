In reply to an off-list query, instructions on how to use my patched get_iplayer script:

\1. Download the new script

Go this URL in your web browser:

<https://github.com/dinkypumpkin/get_iplayer/raw/HEAD/get_iplayer>

You should see the full script in the browser window.

Use **File->Save As** (or equivalent for your browser) to save the script to your local disk.

You can also point curl, wget, etc. at the above URL.

\2. Locate the current script

If you're on Windows and you used the get\_iplayer installer, the current script will almost certainly be:

`C:\Program Files\get_iplayer\get_iplayer.pl`

Note that in the Windows installer version, the above script is invoked from a batch file:

`C:\Program Files\get_iplayer\get_iplayer.cmd`

Only the **.pl** file will be replaced.

If you're on Windows and you did not use the get\_iplayer installer (e.g., you're using Cygwin), only you will know where the script is located.  In this case, the file is most likely to be named _get\_iplayer_ (no .pl extension).

If you're on Linux/OSX, again, only you will know where the script is located.  In this case, the file will almost certainly be named _get\_iplayer_.

\3. Replace the current script

Back up the current script that you located above and replace it with the downloaded script.  Be sure it has same name as the current script (with or without a .pl extension).

If you're on Linux/OSX, you may want to ensure the new script is executable by running the following command from a shell prompt:

`chmod a+x <insert script location here>`

