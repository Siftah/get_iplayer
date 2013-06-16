## get_iplayer FAQ


### Q1) On Unix/Linux/MacOSX why can I not record or stream the flash versions of programmes?

get_iplayer needs flvstreamer installed to be able to do this:

> ​1) Download flvstreamer for your OS from
> [here](http://linuxcentre.net/getiplayer/download/)
>  2) Rename the file: mv flvstreamer-whatever $HOME/flvstreamer
>  3) make it executable: chmod 755 $HOME/flvstreamer
>  4) Tell get_iplayer where to find it by saving it in the prefs:
> get_iplayer –prefs-add –flvstreamer $HOME/flvstreamer

### Q2) Why do all my recorded files have the .flv extention?

For get_iplayer to automatically convert these flash video files you
need to have ffmpeg installed. If you do have ffmpeg installed but not
in the path then try telling get_iplayer where it is by using the
option –ffmpeg=/path/to/ffmpeg. Some older versions of ffmpeg fail to
convert flv to mp4 or avi properly and will just leave the flv file
intact.

### Q3) In Windows Vista I cannot see the downloaded files in the get_iplayer Download Folder.

On the top toolbar of the get_iplayer Download file window there is an
option that says ‘compatibility files’ click that and you should then
see them.

### Q4) In iphone mode, why does the programme not record or stream when the programme is clearly available on the iPlayer web page?

The BBC separately encodes the iPhone versions of the programmes.
Sometimes they just take longer than the flash versions to become
available. In some cases a few programmes don’t quite make it.

### Q5) Can I record or stream BBC iPlayer content from outside of the UK.

For TV mostly not; the BBC simply check that you have a UK based IP
address before allowing you to get access to the download credentials.
However, some of the iPlayer radio, live radio and podcast content is
available outside of the UK. The iPlayer radio is typically streamed at
lower quality than in the UK.

### Q6) Does rtmpdump still work with newer get_iplayer versions?

This tool is never formally tested with get_iplayer there can be no
guarantees that it will work at all. You really should use flvstreamer
instead for recording or streaming BBC iPlayer content. There were legal
threats to Sourceforge with the hosting of rtmpdump in the past (it was
taken offline by Sourceforge in May 2009) because adobe complained that
it ‘can be used to download copyrighted works’.

### Q7) Why is it 1980 again? What are all these DOS commands?

Don’t fret – Margaret Thatcher is not back in power and you haven’t
really experienced a tardis-like time warp. get_iplayer is a
‘command-line’ application. It doesn’t yet have an officially supported
graphical user interface although a few developers are independently
working on them. Command line applications can be very simple to use.
Read the documentation page for simple examples.

### Q8) Do I need a UK TV license to record or stream iPlayer TV or Radio?

No. You only need a UK TV license to receive, record or stream live or
near-live TV (includes channels from any country by whatever means!)

### Q9) Why on win32 do I get recv error ’10060′ or ‘ERROR: ReadPacket, failed to read RTMP packet header’ when trying to stream flash modes?

Try downloading and running the latest [get_iplayer Windows
Installer](http://linuxcentre.net/get_iplayer/contrib/get_iplayer_setup_latest.exe)
(v2.61) and run it again to reinstall flvstreamer. This problem was
caused by an incorrect socket timeout bug in flvstreamer prior to
versions 2.1a.

### Q10) Why do I get this: ERROR: Invalid option in C:Documents and SettingsAll Users/get_iplayer/options: ‘itvnothread = 1′

If you installed the get_iplayer automated installer v2.0+ before
August 5th 2009 then you will have seen this error. To fix it please
edit the C:Documents and SettingsAll Usersget_iplayeroptions
file using wordpad and remove the line ‘itvnothread 1′ then save.
Alternatively, just run the installer again.

### Q11) What modes should I use to get the highest quality recording or streaming?

The following modes will give you the highest quality BBC iPlayer TV
(starting with the highest): **–modes
flashhd,flashvhigh,flashhigh,iphone,flashlow,flashstd,flashnormal,n95_wifi,n95_3g**.
To see details of these modes and their bitrates [see this page on
beebhack](http://beebhack.wikia.com/wiki/IPlayer_TV#Comparison_Table).
For iPlayer Radio these modes are the highest quality (starting with the
highest): **–modes flashaac,iphone,flashaudio,realaudio,wma**. Estimates
of the resulting file sizes can be seen by using the –info option
instead of –get.

### Q12) Why are the ITV, Hulu, Channel4, Five plug-ins not working?

These plug-ins are no longer supported. Please don’t request support for
them.

### Q13) How do I report a bug or issue with get_iplayer or Web PVR Manager?

It is best to describe the problem as a comment on the web page for the
tool. If the trace is very long I suggest emailing to iplayer2 (at sign)
linuxcentre.net. Please always include the program versions, the
platform you are using and the command you are running. If is often
helpful to add the –verbose option when sending any text output.

### Q14) With Windows7 and Vista why do I get “Exception: STATUS_ACCESS_VIOLATION”?

See Q15.

### Q15) With Windows 7 and Vista why can I not record programmes and get an FLVstreamer error saying “Failed to open file! C:/Program Files/get_iplayer/Downloads/….” ?

Vista and Windows 7 appear to not allow applications to save data into
system folders (which is a good thing). To work around this you should
tell get_iplayer to use a different recording location e.g.:
 ‘get_iplayer –add-prefs
–output=C:Users[myusername]DesktopRecordings’. Then create the
new folder that you have selected. Better still just run the latest
installer as this is all done automatically.

### Q16) I get an error saying “ERROR: Duplicate Option Defined ‘itvnothread’ -> ‘mmsnothread’ and ‘itvnothread’”, how do I fix this ?

This is because you have a very old version of the obsolete ITV plugin
on your system. Simply delete the plugin file and it will be corrected.
The ITV plugin is usually found in ‘~/.get_iplayer/plugins/itv.plugin’
or ‘C:Documents and
Settings[myusername].get_iplayerpluginsitv.plugin’.

### Q17) Why can I only see the last few hundred lines in the get_iplayer window under Windows?

You need to set the size of the command buffer as follows on the
get_iplayer window: (1) Right-click in the top left corner of the title
bar and choose Properties. (2) Select the Layout tab, (3) Set the width
and height in the Screen Buffer Size section to something nice and big.

### Q18) On Windows, why do my recordings often fail part of the way though?

It could be that your anti-virus / anti-malware / anti-spyware /
personal firewall / file-sharing blocker is getting in the way of the
RTMP connection. Try disabling this software (at your own risk) to see
if it makes any difference. I have had reports specifically that ‘AVG
link scanner’ causes this problem.

### Q19) Why does get_iplayer keep retrying the recordings every minute?

This is because the BBC have started to roll-out ‘SWF verification’
feature on their content delivery networks. This feature is not (and
never will be) supported by flvstreamer (the tool that get_iplayer uses
to record flash streams). flvstreamer disconnects after the flash server
disconnects the client after a timeout which is currently set to around
1 minute. After this get_iplayer, as usual, tries to resume the
programme recording. This shouldn’t cause any problems except for the
obvious increased resume attempts which can add a second or two overhead
per attempt..

### Q20) Why does iPlayer TV streaming fail after a minute?

See Q19. This is currently broken. There may be improved support for
streaming of non-live programmes in the future. Unfortunately for the
time being you will have to record it before watching it.
