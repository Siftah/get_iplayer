## When SWF Verification Attacks

BBC Flash media servers use SWF verification, which means they verify that you are accessing media streams with an approved SWF (Flash player) file. get_iplayer contains such a SWF player URL, which it passes to rtmpdump to use in the verification process. Very occasionally, BBC servers will stop accepting the SWF player URL used by get_iplayer and you will be unable to download programmes.  This usually manifests as a series of rtmpdump errors in the get_iplayer output log similar to:

``` text
ERROR: WriteN, RTMP send error 10054 (42 bytes)
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
```

You can override the default URL with a working value until get_iplayer has been updated, as described below.  When the need arises, new SWF player URLs will be disseminated via the [get_iplayer mailing list](http://lists.infradead.org/mailman/listinfo/get_iplayer) and this page will be updated.  The URL values below are current as of date of publication.

### get_iplayer

Override the default SWF player URL for each programme type by setting a preference in your user options file.  This must be done at a command prompt with the get_iplayer CLI. For example, to override the SWF player URL used for TV programmes:

1. Get thee to a command prompt
    * Linux/Unix: Open a window with your favourite terminal emulator
    * OSX: Open Terminal from /Applications/Utilities in Finder
    * Windows XP/Vista/7: Open *All Programs -> get_iplayer -> Get_iPlayer* from Start menu
    * Windows 8 Metro stylee: Click *Get_iPlayer* tile

2. Copy the command below and paste it at the command prompt, then press Return to execute:

``` bash
get_iplayer --prefs-add --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf" 
```

The command must be entered (or pasted) at a command prompt exactly as shown, all on one line.  The output should look like:

``` text
INFO: Added option 'rtmptvopts' = '--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf'
INFO: Options file /home/<username>/.get_iplayer/options updated
```

The command above applies the new preference to TV programmes.  If you find that you are unable to download other programme types because the default SWF player URL is rejected for verification, run the command above changing `--rtmp-tv-opts` to `--rtmp-radio-opts`, `--rtmp-livetv-opts` or `--rtmp-liveradio-opts` as necessary.

When you obtain an updated get_iplayer with working SWF player URL, you should remove the preference(s) by running the command(s) above, changing `--prefs-add` to `--prefs-del`.

In case you need to find your user options file, it is located at `$HOME/.get_iplayer/options` for Linux/Unix/OSX or `%USERPROFILE%\.get_iplayer\options` for Windows. There is normally no user options file when get_iplayer is first installed, but the `--prefs add` command will create one.

### Get iPlayer Automator

Override the default SWF player URL for each programme type by setting a preference in your user options file.  This must be done with the get_iplayer CLI.  However, because the get_iplayer CLI is: a) embedded in the GiA application bundle; b) uses a non-default profile location in GiA, the override command is different from that shown above. For example, to override the SWF player URL used for TV programmes:

1. Open Terminal from /Applications/Utilities in Finder

2. Copy the command below and paste it at the command prompt (cursor location in Terminal), then press Return to execute:

``` bash
/usr/bin/perl "/Applications/Get iPlayer Automator.app/Contents/Resources/get_iplayer.pl" --prefs-add  --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf" --profile-dir "$HOME/Library/Application Support/Get iPlayer Automator"
```
**NOTE:** If you do not have GiA installed in /Applications, adjust the path to get_iplayer.pl accordingly.

The command must be entered (or pasted) at a command prompt exactly as shown, all on one line. The output should look like:

``` text
INFO: Added option 'profiledir' = '/Users/<username>/Library/Application Support/Get iPlayer Automator/'
INFO: Added option 'rtmptvopts' = '--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf'
INFO: Options file /Users/<username>/Library/Application Support/Get iPlayer Automator/options updated
```

The command above applies the new preference to TV programmes.  If you find that you are unable to download other programme types because the default SWF player URL is rejected for verification, run the command above changing `--rtmp-tv-opts` to `--rtmp-radio-opts`, `--rtmp-livetv-opts` or `--rtmp-liveradio-opts` as necessary.

When you obtain an updated GiA with working SWF player URL, you should remove the preference(s) by running the command(s) above, changing `--prefs-add` to `--prefs-del`.

In case you need to find your user options file, it is located at `/Users/<username>/Library/Application Support/Get iPlayer Automator/options` for GiA.  There is normally no user options file for get_iplayer in GiA, but the `--prefs add` command will create one.

##### Esoterica Corner

The `profiledir` preference setting will have not have any effect on GiA.  It is just a by-product of how the command above is formulated.  To set just the `rmtmptvopts` preference would require the slightly more convoluted:

``` bash
(export GETIPLAYERUSERPREFS="$HOME/Library/Application Support/Get iPlayer Automator" GETIPLAYERSYSPREFS="$HOME/Library/Application Support/Get iPlayer Automator" && /usr/bin/perl "/Applications/Get iPlayer Automator.app/Contents/Resources/get_iplayer.pl" --prefs-add --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf")
```