BBC Flash media servers use SWF verification, which means they verify that you are accessing media streams with an approved SWF (Flash player) file. get_iplayer contains a SWF player URL, which it passes to rtmpdump to use in the verification process. Very occasionally, BBC servers will stop accepting the SWF player URL used by get_iplayer.  When that occurs, you can override the default URL with a working value until get_iplayer has been updated.  When the need arises, new SWF player URLs will be disseminated via the [get_iplayer mailing list](http://lists.infradead.org/mailman/listinfo/get_iplayer) and this page will be updated.  The URL values below are current as of date of publication.

You can override the default SWF player URL for each programme type by setting a preference in your user options file.  This must be done with the get_iplayer CLI.  For example, to override the SWF player URL used for TV programmes:

```
get_iplayer --prefs-add --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf" 
```

The command must entered (or pasted) at a command prompt exactly as shown, all on one line.  

This example above sets the `rtmp-tv-opts` preference in your user options file (`$HOME/.get_iplayer/options` for Linux/Unix/OSX, `%USERPROFILE%\.get_iplayer\options` for Windows).

The command above applies the new preference to TV programmes.  If you find that you are unable to download other programme types, run the command again changing `--rtmp-tv-opts` to `--rtmp-radio-opts`, `--rtmp-livetv-opts` or `--rtmp-liveradio-opts` as necessary.

#### Get iPlayer Automator

Because get_iplayer is: a) embedded in the GiA application bundle; b) uses a non-default profile location, the process is slightly more complicated.

1. Open Terminal from /Applications/Utilities in Finder

2. Copy the command below and paste at the command prompt (cursor location) in Terminal, the press Return to  execute

```
/usr/bin/perl "/Applications/Get iPlayer Automator.app/Contents/Resources/get_iplayer.pl" --profile-dir "$HOME/Library/Application Support/Get iPlayer Automator/" --prefs-add --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf"
```

The output should look something like:

```
INFO: Added option 'profiledir' = '/Users/<username>/Library/Application Support/Get iPlayer Automator/'
INFO: Added option 'rtmptvopts' = '--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf'
INFO: Options file /Users/<username>/Library/Application Support/Get iPlayer Automator//options updated
```


This example sets the `rtmp-tv-opts` preference in your user options file (`/Users/<username>/Library/Application Support/Get iPlayer Automator/options`)

`$HOME/Applic/options` for Linux/Unix/OSX, `%USERPROFILE%\.get_iplayer\options` for Windows).


