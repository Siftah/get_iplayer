# Documentation

## Table of Contents

* [Searching](#Searching)
* [Recording](#Recording)
* [Live Recording](#Live%20Recording)
* [Searching the Future Programme Schedule](#Searching%20the%20Future%20Programme%20Schedule)
* [Searching the Recording History](#Searching%20the%20Recording%20History)
* [Indexing and Caching Features](#Indexing%20and%20Caching%20Features)
* [Updating get\_iplayer](#Updating%20get_iplayer)
* [Streaming](#Streaming)
* [Live Streaming](#Live%20Streaming)
* [Saving Settings](#Saving%20Settings)
* [Using a Web Proxy](#Using%20a%200Web%20Proxy)
* [Option Presets and Shortcuts](#Option%20Presets%20and%20Shortcuts)
* [Subtitles](#Subtitles)
* [More Programme Information](#More%20Programme%20Information)
* [Filenames and Directories](#Filenames%20and%20Directories)
* [Custom Commands](#Custom%20Commands)
* [PVR Usage](#PVR%20Usage)
* [Substitution Parameters](#Substitution%20Parameters)
* [External Programs](#External%20Programs)
* [Metadata Tagging](#Metadata%20Tagging)
* [Notes](#Notes)

## Command Usage

The full get\_iplayer man page listing all available options can be viewed **[[here|manpage]]**. 

For basic help run:

    get_iplayer -h

For advanced and extended options run:

    get_iplayer --long-help

## Examples

<a name="Searching"></a>
### Searching

**[[Click Here for All Search Options|manpage#Search-Options]]**

List all tv programmes (either from BBC site or cached):

    get_iplayer

List all tv programme names matching 'news':

    get_iplayer news

List all Radio programme names matching 'news':

    get_iplayer --type=radio news

List all Live TV and Radio channels/programmes:

    get_iplayer --type=livetv,liveradio

List all tv programmes with long descriptions:

    get_iplayer --long

List all tv programmes showing only ‘pid’, 'name’ and ‘episode'

    get_iplayer --listformat="<pid>: <name>-<episode>"

Search all tv programmes for the word ‘hello' in the 'episode' and ‘channel' fields

    get_iplayer --fields=episode,channel hello

List all tv programmes with categories containing the word ‘News’ and on channel ‘BBC One’

    get_iplayer --channel="BBC One" --category=News

List all tv programmes added to the cache since 24 hours ago:

    get_iplayer --since=24

List all available categories for BBC Radio and BBC TV programmes:

    get_iplayer --list=categories --type=tv,radio

List all available radio channels:

    get_iplayer --list=channel --type=radio

List all BBC TV programmes and BBC podcasts

    get_iplayer --type=podcast,tv

List all programmes with categories not containing the string ‘child’ on BBC One:

    get_iplayer --exclude-category=child --channel="bbc one"

List all programme metadata and available streaming modes for programme with index number 123:

    get_iplayer --info 123

<a name="Recording"></a>
### Recording

**[[Click Here for All Recording Options|manpage#Recording-Options]]**

Essentially, you can just add `--get` to any of the above searches to record the matching programmes.

Record programme number 123 (see index list):

    get_iplayer --get 123

Record Radio programme number 10123 (see index list):

    get_iplayer --get 10123

Record programme number 123 and save in ‘/home/user/tv-files/’:

    get_iplayer --get 123 --output "/home/user/tv-files/"

Record Radio programme number 10123 and tv programme number 324 (see index list):

    get_iplayer --get 10123 324

Record Podcasts matching ‘Moyles’:

    get_iplayer --type=podcast --get "Moyles"

Record all tv programmes with ‘blue peter’ in the title/episode:

    get_iplayer --get "blue peter"

Record all tv programmes with ‘blue peter’ in the title/episode, and programme index 123:

    get_iplayer --get "blue peter" 123

Record all programmes with URL that contains a programme ID (pid) b002a23a (i.e. the URL of the programme page on BBC iPlayer):

    get_iplayer --pid b002a23a
    get_iplayer "http://www.bbc.co.uk/iplayer/episode/b002a23a"

Record a video from the BBC embedded media player such as [Learning Zone](http://www.bbc.co.uk/learningzone/clips/), [BBC Archive](http://www.bbc.co.uk/archive/index.shtml) or the [BBC News site](http://news.bbc.co.uk/1/hi/video_and_audio/default.stm) (i.e. the URL of the page that contains the player):

    get_iplayer "tv:http://news.bbc.co.uk/1/hi/uk_politics/8104086.stm"
    get_iplayer --type=tv "http://news.bbc.co.uk/1/hi/uk_politics/8104086.stm"

Record all programmes with ‘comedy’ in the title, episode or long description:

    get_iplayer --long --get comedy

Record all programmes with categories containing ‘music’:

    get_iplayer --get --category=music


Record a TV programme trying flashhigh, flashstd and flashlow modes in order until one succeeds (`--rtmpdump` is not required if your options tell get\_iplayer where rtmpdump is located). 

    get_iplayer --type=tv --get 123 --modes=flashhigh,flashstd,flashlow --rtmpdump="/path/to/rtmpdump"

**Note:** Possible modes are (in increasing order of quality): flashlow, flashnormal, flashstd, flashhigh, flashvhigh, flashhd. See [this page] (http://beebhack.wikia.com/wiki/IPlayer_TV#Comparison_Table) for more details. Use the `--info` option to see what modes are available for a programme.

Record a radio programme trying flashaudio then flashaac modes in order until one succeeds (`--rtmpdump` is not required if your options tell get\_iplayer where rtmpdump is located). 

    get_iplayer --type=radio --get 12345 --modes=flashaudio,flashaac --rtmpdump="/path/to/rtmpdump"

**Note:** Possible modes are (in increasing order of quality): flashaaclow, flashaudio, flashaacstd, flashaachigh. Use the `-–info` option to see what modes are available for a programme.


<a name="Live Recording"></a>
### Live Recording

**[[Click Here for All Recording Options|manpage#Recording-Options]]**

*Note: Please upgrade to rtmpdump 2.3 or later for reliable live streaming.*

List LiveTV:

    get_iplayer --type=livetv

Record a Live BBC iPlayer TV programme (e.g. BBC2):

    get_iplayer --type=livetv --get "BBC Two"
    get_iplayer --type=tv "http://www.bbc.co.uk/iplayer/playlive/bbc_two"
    get_iplayer --type=tv --pid="bbc_two"

Record a High Quality Live BBC iPlayer Radio programme (e.g. BBC Radio 1):

    get_iplayer --type=liveradio --get "Radio 1"
    get_iplayer --type=radio "http://www.bbc.co.uk/iplayer/playlive/bbc_radio_one"
    get_iplayer --type=radio --pid=bbc_radio_one

<a name="Searching the Future Programme Schedule"></a>
### Searching the Future Programme Schedule

**[[Click Here for All Search Options|manpage#Search-Options]]**

It is possible to index, search and queue recordings for specific programmes that have not yet been made available. This is currently only available on BBC TV and Radio modes and only searches for up to 13 days in advance. Note that some of the programmes in the BBC schedules are never released on iPlayer and therefore will never get recorded even if you can find them in the search results. Note that the refreshing can take quite a bit longer with `--refresh-future` specified.

Refresh the cache with future schedules (e.g. for tv). You must do this otherwise you will not be able to search for future programmes:

    get_iplayer --type=tv --refresh-future --refresh

Save the refreshing of future programmes into your default settings (a good idea if you want the above to be automatic):

    get_iplayer --add-prefs --refresh-future

To search for a programme additionally in the future just use any of the usual search commands but adding --future:

    get_iplayer 'Eastenders' --future

You cannot record a programme in the future but you can queue it in the PVR for recording when it becomes available (if at all). In this example the index of the search results for a future episode of eastenders was ’123′:

    get_iplayer --pvrqueue --type=tv 123

<a name="Searching the Recording History"></a>
### Searching the Recording History

**[[Click Here for All Search Options|manpage#Search-Options]]**

The recording history is a text database of the programmes you have recording since you started using get\_iplayer. It’s primary purpose is to prevent get\_iplayer from downloading the same programme more than once. You can search the recordings history much like the normal programme types.

Search for ""Doctor Who" in the history

    get_iplayer --history "Doctor Who""

Show detailed programme metadata for all recorded programmes matching “Doctor Who” in the history

    get_iplayer --history "Doctor Who" --info

Download thumbnails for all recorded programmes matching “Doctor Who” in the history

    get_iplayer --history "Doctor Who" --thumbnailonly

Download thumbnails for all recorded programmes matching “Doctor Who” in the history and where the media file hasn’t been deleted.

    get_iplayer --history "Doctor Who" --thumbnailonly --skipdeleted

<a name="Indexing and Caching Features"></a>
### Indexing and Caching Features

**[[Click Here for All Config Options|manpage#Config-Options]]**

Refresh the tv programme cache (this happens after 4hrs automatically - see --expiry option):

    get_iplayer --refresh

Manually refresh the programme cache for all types:

    get_iplayer --refresh --type=all

Manually refresh the radio programme cache:

    get_iplayer --refresh --type=radio

Set the expiry of the caches (in seconds):

    get_iplayer --add-prefs --expiry=3600

Exclude adding matching channels to the programme cache (i.e. these channels won’t be indexed and therefore indexing/refreshing will be faster):

    get_iplayer --refresh-exclude="cbeebies,cbbc" --type=tv --refresh

Include  ONLY these channels in the programme cache (i.e. only these channels will be indexed and therefore indexing/refreshing will be faster):

    get_iplayer --refresh-include="bbc" --type=tv --refresh

<a name="Updating get_iplayer"></a>
### Updating get\_iplayer

**[[Click Here for All Config Options|manpage#Config-Options]]**

#### Updating on Linux, OS X, Unix, cygwin, etc

If you installed by simply downloading the get\_iplayer script then you can just run:

    get_iplayer --update

Optionally force updating the script and the plugins:

    get_iplayer --update --plugins-update --force

If you installed using a package manager then please see the Install page for further details:

#### Updating on Windows (Installer method)

Download the latest Installer and re-run it. You can then uninstall the get\_iplayer component and then re-install that component. The same goes for each of the other components if you so wish.

<a name="Streaming"></a>
### Streaming

**[[Click Here for All Output Options|manpage#Output-Options]]**

Stream a programme in mplayer or xine while recording it to disk (does not yet work in win32). Works for flash modes and podcasts):

    get_iplayer --stdout --get 123 | mplayer -cache 3072 -
    get_iplayer --stdout --get 123 | xine stdin:/

Stream a programme in mplayer/vlc/ffplay while not recording it to disk:

    get_iplayer --stream 123 --player="mplayer -cache 3072 -"
    get_iplayer --stream 123 | mplayer -cache 3072 -
    get_iplayer --stream 123 --player="vlc -"
    get_iplayer --stream 123 --player="ffplay -"

<a name="Live Streaming"></a>
### Live Streaming

**[[Click Here for All Output Options|manpage#Output-Options]]**

*Note: Please upgrade to rtmpdump 2.3 or later for reliable live streaming.*

Stream a live BBC iPlayer TV programme to mplayer while not recording it to disk (e.g. BBC 2):

    get_iplayer --stream --type=livetv "BBC Two" --player="mplayer -cache 512 -"
    get_iplayer --stream --type=tv "http://www.bbc.co.uk/iplayer/playlive/bbc_two" --player="mplayer -cache 512 -"
    get_iplayer --stream --type=tv "http://www.bbc.co.uk/iplayer/playlive/bbc_two" | mplayer -cache 512 -
    get_iplayer --stream --type=tv --pid="bbc_two" | mplayer -cache 512 -

Stream a live BBC iPlayer radio programme to mplayer while not recording it to disk (e.g. BBC Radio 1):

    get_iplayer --stream --type=liveradio "Radio 1" --player="mplayer -cache 64 -"
    get_iplayer --stream --type=radio "http://www.bbc.co.uk/iplayer/playlive/bbc_radio_one" | mplayer -cache 64 -
    get_iplayer --stream --pid='bbc_radio_one' | mplayer -cache 64 -

<a name="Using a Web Proxy"></a>
### Using a Web Proxy

**[[Click Here for All Recording Options|manpage#Recording-Options]]**

If you are behind a web proxy you can use the following to specify it:

    get_iplayer --proxy=http://[username:password@]<server:<port

All modes other than http will not work through a web proxy. To make only the meta-data web requests go through the proxy add the –partial-proxy option. This will only work if your network allows direct access to the streaming port (e.g. port 1935).

<a name="Saving Settings"></a>
### Saving Settings

**[[Click Here for All Config Options|manpage#Config-Options]]**

Default user settings can be added, removed or changed as follows:

Save or update proxy settings and verbose mode as user defaults (in `~/.get_iplayer/options` or `%USERPROFILE%\.get_iplayer\options` in Windows):

    get_iplayer --prefs-add --verbose --proxy=http://proxy.domain.com:3128

Additionally save programme type settings (this will only update the specified options – existing options will be retained):

    get_iplayer --prefs-add --type=radio,tv

Remove a specific option from those saved (e.g. --proxy):

    get_iplayer --prefs-del --proxy=http://proxy.domain.com:3128

Show all saved default options:

    get_iplayer --prefs-show

Completely clear all saved default options:

    get_iplayer --prefs-clear

System-wide defaults can be saved in `/etc/get_iplayer/options` on Linux/Unix/OSX/Cygwin platforms and `%ALLUSERSPROFILE%\get_iplayer\options` in Windows. The format is as follows:

    <option key> <option value>

The option key is the option name with hyphens removed.  For example, `--file-prefix` becomes `fileprefix`.  Boolean options have a value of 0 (off) or 1 (on). Example entries:

    output /path/for/output
    fileprefix <name>-<episode>
    raw 1

<a name="Option Presets and Shortcuts"></a>
### Option Presets and Shortcuts

**[[Click Here for All Config Options|manpage#Config-Options]]**

User defined groups of options can be added, removed or changed. They are referred to by the ‘preset name’ as follows:

Save or update several options (–hide and –since) in the preset named ‘my\_preset’ (in `~/.get_iplayer/presets/my_preset` or `%USERPROFILE%\.get_iplayer\presets\my_preset` in Windows):

    get_iplayer --preset=my_preset --prefs-add --hide --since=24

Additionally save programme type for preset named ‘my\_preset’ (this will only update the specified preset options – existing preset options will be retained):

    get_iplayer --preset=my_preset --prefs-add --type=radio,tv

Remove a specific option from those saved in the preset named ‘my\_preset’ (e.g. `--since=24`):

    get_iplayer --preset=my_preset --prefs-del --since=24

Show \*allsaved options in preset named ‘my\_preset’:

    get_iplayer --preset=my_preset --prefs-show

Completely clear all saved options in preset named ‘my\_preset’:

    get_iplayer --preset=my_preset --prefs-clear

Use the preset named ‘my\_preset’ to search for items with names containing the word ‘News’:

    get_iplayer --preset=my_preset News

Here is a more useful example. I would like to have a preset that shows me the BBC iPlayer TV programmes added to my cache in the last 24hrs, hide ones I’ve already downloaded, exclude some channels and exclude childrens’ and wales programme categories. So to add the preset I type:

    get_iplayer --prefs-add --preset=last24 --type=tv --since=24 --hide --versionlist=default --exclude-category=child,wales --exclude-channel=alba,cbbc,cbeebies,parliament

Now, to run the preset at any time I simply type:

    get_iplayer --preset=last24

<a name="Subtitles"></a>
### Subtitles

**[[Click Here for All Recording Options|manpage#Recording-Options]]**

Record programme number 123 with subtitles (if available) and optionally insert a subtitle delay of 5 seconds:

    get_iplayer --subtitles --suboffset 5000 --get 123

(Re)download subtitles only (if available):

    get_iplayer --subsonly --get 123

<a name="More Programme Information"></a>
### More Programme Information

**[[Click Here for All Display Options|manpage#Display-Options]]**

#### Programme Detailed Stream Information

Display the Various stream URLs for programme index 123:

    get_iplayer --streaminfo 123

#### Full Program Information Display

Display the programme metadata for index 123:

    get_iplayer --info 123

#### Metadata Files

The programme metadata can be additionally downloaded using the –metadata=[TYPE] option. Where [TYPE] is one of xbmc, xbmc\_movie, freevo, generic.

Save all the metadata after a successful download into an xml file:

    get_iplayer --metadata=generic --get 123

Save ONLY the metadata for a specific search into an xml file (and don’t record the programme). This is useful if you forgot to get the metadata when recording.

    get_iplayer --metadata-only --metadata=generic 123

#### Thumbnail

 A programme thumbnail can be automatically downloaded using the –thumbnail option.

    get_iplayer --thumbnail --get 123

Save all the thumbnail(s) ONLY for a specific search (and don’t record the programme). This is useful if you forgot to get the thumbnail when recording.

    get_iplayer --thumbnail-only 123

#### Update Your Entire Recording Collection with Thumbnails, Metadata and Subtitles

As long as your programmes remain in the directory they were originally recorded into you can retrospecitvely download the thumbnail, metadata or subtitles of the shows in your recordings history.

Get all thumbnails for files that still exist (in this case for programmes matching ‘Doctor Who’):

    get_iplayer --thumbnail-only --history --skipdeleted "Doctor Who"

Get all the metadata files (in generic format) for files that still exist:

    get_iplayer --metadata-only --metadata=generic --history --skipdeleted

Get all subtitles for files that still exist (Note that you can only get subs if the programme is still available on iPlayer):

    get_iplayer --subs-only --history --skipdeleted

<a name="Filenames and Directories"></a>
### Filenames and Directories

**[[Click Here for All Output Options|manpage#Output-Options]]**

#### Filenames

Use a filename prefix format with [substitution parameters](#Substitution-Parameters):

    --file-prefix="<name>-<episode>-<longname>-<version>-<pid>"

Use a filename prefix format with [substitution parameters](#Substitution-Parameters) suited to XBMC, Boxee and MythTV:

    --file-prefix="<nameshort><-senum><-episodeshort>"

**NOTE:** Hyphens *inside* the angle brackets will only be used if the associate substitution parameter has a non-empty value.

#### Valid Characters

Several options exist for controlling what characters are allowed in filenames.

Allow use of spaces in filenames (by default these are converted to ‘\_’).

    --whitespace

Use only filenames valid for DOS/Windows FAT filesystem.

    --fatfilename

#### Recording to Specific Directories

Use a specific directory for all programmes recorded:

    --output="/home/user/recordings/"

Override the above for all radio (or tv) programmes recorded:

    --outputradio="/home/user/recordings-radio/"
    --outputtv="/home/user/recordings-tv/"

#### Subdirectories

Use a subdirectory for each programme name:

    --subdir

Use a subdirectory format with [substitution parameters](#Substitution-Parameters):

    --subdir-format="<nameshort>-<seriesnum>"

<a name="Custom Commands"></a>
### Custom Commands

**[[Click Here for All Output Options|manpage#Output-Options]]**

Run a custom user command after a successful recording using [substitution parameters](#Substitution-Parameters):

    get_iplayer --get 123 --command 'echo "<index>,<filename>,<name>,<episode>,<desc>,<available>,<longname>,<duration>,<versions>,<version>,<thumbnail>,<channel>,<categories>,<type>,<pid>"'

Using the command option to background transcode your recorded video to mp4 format:

    get_iplayer --get 123 --command "mencoder -ovc lavc -lavcopts vcodec=mpeg4 -oac lavc -lavcopts abitrate=128 -o <filename>.mp4 <filename> -quiet &"

<a name="PVR Usage"></a>
### PVR Usage

**[[Click Here for All PVR Options|manpage#PVR-Options]]**

The PVR functionality allows you to record any number of iPlayer programmes using any combination of search terms that you would normally run on the command line. The PVR searches are saved in `~/.get_iplayer/pvr/` or `%USERPROFILE%\.get_iplayer\pvr\` in Windows.

You can add, delete and list the PVR searches. This feature allows you to run multiple batch recordings from a scheduler such as Unix crond (and possibly the Windows scheduler). A tutorial is on how to set up and use the PVR with crond is [here](dont-want-to-miss-that-programme-on-iplayer-over-christmas.html).

Add a new PVR search for a specific programme (i.e. ‘series link’):

    get_iplayer --pvr-add=Top_Gear --type=tv "Top Gear"

Add a new PVR search (using more search options):

    get_iplayer --pvr-add=bbc1_comedy_tv_progs --category=comedy --type=tv --output=/path/to/my/pvr/recordings/ --channel="BBC One"

Add a new one-off recording PVR search. This will effectively queue the programmes for recording and delete the PVR search after completion:

    get_iplayer --pvr-queue --type tv 123 231 32 "Blue Peter"

Add a new one-off recording PVR search for a specific PID:

    get_iplayer --pvr-queue --pid=tv:b01a2b3c

List the PVR searches already added:

    get_iplayer --pvr-list

Remove a PVR search:

    get_iplayer --pvr-del=Top_Gear

Disable a PVR search:

    get_iplayer --pvr-disable=Top_Gear

Re-enable a PVR search:

    get_iplayer --pvr-enable=Top_Gear

Run the PVR (this really should be added to your scheduler such as cron):

    get_iplayer --pvr

<a name="Scheduling the PVR"></a>
### Scheduling the PVR

**[[Click Here for All PVR Options|manpage#PVR-Options]]**

#### Linux / Unix / MacOSX

Add this line to add to user’s crontab (use ‘crontab -e’ to edit) – this will run all of the PVR jobs every hour:

    0 * * * * /path/to/get_iplayer --pvr 2>> /tmp/get_iplayer.log

Optionally, to notify by email when programmes have been recorded, add this to the top of your crontab (this will catch the stdout from the cron job and send to the specified email address):

    MAILTO=me@mydomain.com

Or, run the PVR Scheduler from the command line. This will fire off the PVR every hour as long as the command is running:

    get_iplayer --pvrscheduler 3600

#### Windows

With the latest installer there will be an entry in the Start menu to ‘Run PVR Scheduler Now’. This will start a command window which will fire off the PVR every 4 hours. Alternatively if, you wish to use the Windows Scheduler see [this guide](http://www.beebotron.org/helper_get_iplayer_help.php) for full instructions.

<a name="Substitution Parameters"></a>
### Substitution Parameters

The following substitutions may be available to certain options such as –command and –fileprefix. To see a list of all available parameters for a specific programme use the –info option.

    <index>         = Index number
    <name>          = Programme short name
    <seriesnum>     = Series number
    <nameshort>     = Programme name with series number stripped.
    <episode>       = Episode info
    <episodenum>    = Episode number
    <episodeshort>  = programme episode with episode number stripped.
    <senum>         = Series and episode numbers in the s##e## format.
    <desc>          = Long description
    <descshort>     = Short description
    <descmedium>    = Medium description
    <versions>      = Comma separated list of versions
    <version>       = Selected version e.g 'signed'
    <thumbnail>     = Programme thumbnail url
    <web>           = Programme url
    <channel>       = Programme channel
    <categories>    = Categories
    <type>          = Type: tv, podcast, or radio
    <mode>          = Mode used to record programme
    <filename>      = Filename of recorded file
    <filepart>      = Filename of partially recorded file
    <dir>           = Directory of file
    <fileprefix>    = Filename prefix of file
    <symlink>       = Filename of any symlink file if specified
    <ext>           = Filename pxtension of file
    <duration>      = Duration in HH:MM:SS or seconds
    <available>     = Date/Time made available or remaining
    <dldate>        = Date when the file was obtained in YYYY-MM-DD format
    <dltime>        = Time when the file was obtained in HH:MM:SS format
    <timeadded>     = Time when programme was added to cache (epoch format)
    <expiry>        = Time when programme will expire from web
    <expiryrel>     = Telative time when programme will expire from web
    <firstbcast>    = Time when programme was first broadcast
    <firstbcastrel> = Relative time when programme was first broadcast
    <lastbcast>     = Time when programme was last broadcast
    <lastbcastrel>  = Relative time when programme was last broadcast

<a name="External Programs"></a>
### External Programs

**[[Click Here for All External Program Options|manpage#External-Program-Options]]**

Several external programs can be used by get\_iplayer. The required programs for each mode and type are listed **[[here|installation#External%20Program%20Requirements]]**. The following options are used to specify the exact path so that get\_iplayer knows where they are. If they are already in $PATH then there is no need to specify them:

    --rtmpdump
    --ffmpeg
    --mplayer
    --atomicparsley
    --id3v2

e.g. to save the ffmpeg location to your default settings in Windows (you don’t need to do this if you use the get\_iplayer installer):

    get_iplayer --add-prefs --ffmpeg="C:\Program Files\get_iplayer\ffmpeg\bin\ffmpeg.exe"

e.g. to save the ffmpeg location to your default settings in Linux/OS X (you don’t need to do this if the ffmpeg directory is in $PATH):

    get_iplayer --add-prefs --ffmpeg="/usr/bin/ffmpeg"

<a name="Metadata Tagging"></a>
### Metadata Tagging

**[[Click Here for All Metadata Tagging Options|manpage#Tagging-Options]]**

get\_iplayer adds metadata tags to output files in MP4, M4A and MP3 format.  Details on metadata tagging can be found **[[here|tagging]]**.

<a name="Notes"></a>
### Notes

The first time you run the script it will access the BBC website XML feeds and create an index of all programmes currently available.

<a name="Todo"></a>
### Todo

These still need documenting:

	--multimode
	–-email
	–-series
	–-tree
	–-terse
	–-thumbsize[cache]
	–-hide
	–-force
	–-overwrite
