## When SWF Verification Attacks

BBC Flash media servers use SWF verification, which means they verify that you are accessing media streams with an approved SWF (Flash player) file. get_iplayer contains such a SWF player URL, which it passes to rtmpdump to use in the verification process. Very occasionally, BBC servers will stop accepting the SWF player URL used by get_iplayer and you will be unable to download programmes.  This usually manifests as a series of rtmpdump errors in the get_iplayer output log similar to:

``` text
ERROR: WriteN, RTMP send error 10054 (42 bytes)
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
```

With verbose logging on (--verbose) you may also see an explicit verification failure:

``` text
DEBUG: (object begin)
DEBUG: Property: <Name:              level, STRING:     error>
DEBUG: Property: <Name:               code, STRING:     NetConnection.Connect.Rejected>
DEBUG: Property: <Name:        description, STRING:     Connection failed.>
DEBUG: Property: <Name:        description, STRING:     [ Client.SWFVerificiation.Rejected ] : status code 433>
DEBUG: (object end)
```

You can override the default URL with a working value until get_iplayer has been updated, as described below.  When the need arises, new SWF player URLs will be disseminated via the [get_iplayer mailing list](http://lists.infradead.org/mailman/listinfo/get_iplayer) and this page will be updated.  The URL values below are current as of date of publication.

### Update get_iplayer Preferences

**NOTE:** This procedure has been tested with get_iplayer 2.82.  If you have an older version, please update before proceeding. 

Override the default SWF player URL for each programme type by setting a preference in your user options file.  This must be done at a command prompt with the get_iplayer CLI. For example, to override the SWF player URL used for TV programmes:

1. Get thee to a command prompt
    * Linux/Unix: Open a window with your favourite terminal emulator
    * OSX: Open Terminal from /Applications/Utilities in Finder
    * Windows XP/Vista/7: Open *All Programs -> get_iplayer -> Get_iPlayer* from Start menu
    * Windows 8 Metro stylee: Click *Get_iPlayer* tile

    A new command window should open.

2. Select the entire text of the command below and copy it to the clipboard (Right Click -> Copy on all systems or: Ctrl-C on Windows/Linux, Cmd-C on OSX).

    ``` bash
    get_iplayer --prefs-add --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf" 
    ```

3. Click the window opened in #1 to make it active.

4. Paste the command text at the prompt, i.e., the cursor location in the window (Right Click -> Paste for all systems or: Ctrl-Shift-V on Linux, Cmd-V on OSX, or the sequence Alt+Space, e, p on Windows). The command text must be exactly as shown, all on one line.  

5. Press Return to execute the command. The output should look like:

    ``` text
    INFO: Added option 'rtmptvopts' = '--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf'
    INFO: Options file /home/<username>/.get_iplayer/options updated
    ```

6. Double check that your preferences were updated correctly by running this command:

    ``` bash
    get_iplayer --show-options
    ```

    The output should contain a line that looks like:

    ``` text
    rtmptvopts = --swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf
    ```

The sequence above applies a new preference to TV programmes only.  If you find that you are unable to download other programme types because the default SWF player URL is rejected for verification, repeat the sequence above changing `--rtmp-tv-opts` to `--rtmp-radio-opts`, `--rtmp-livetv-opts` or `--rtmp-liveradio-opts` as necessary.

Although it is not advised, if you want to edit your user options file directly it is located at `$HOME/.get_iplayer/options` for Linux/Unix/OSX or `%USERPROFILE%\.get_iplayer\options` for Windows. There is normally no user options file when get_iplayer is first installed, but the `--prefs-add` command will create one.

### Reverting Your Changes

When you obtain an updated version get_iplayer with working SWF player URL, you should remove the preference(s) by running the command(s) above, changing `--prefs-add` to `--prefs-del`.  

1. Repeat the sequence above replacing the command text with:

    ``` bash
    get_iplayer --prefs-del --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf" 
    ```

	The output should look like:

	```
	INFO: Deleted option 'rtmptvopts' = '--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf'
	INFO: Options file /home/<username>/.get_iplayer/options updated
	```

2. Double check that your preferences were reverted correctly by running this command:

    ``` bash
    get_iplayer --show-options
    ```

    The output should not contain a line with `rtmptvopts` as the option name.

3. If you changed preferences for `rtmpradioopts`, `rtmplivetvopts` or `rtmpliveradioopts`, revert those changes by repeating the command in #1 changing `--rtmp-tv-opts` to `--rtmp-radio-opts`, `--rtmp-livetv-opts` or `--rtmp-liveradio-opts` as necessary.
