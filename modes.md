## get_iplayer Recording Modes

BBC iPlayer makes programmes available at several levels of video and audio quality.  get_iplayer represents each video/audio quality level with an alphanumeric code, referred to as a "mode".  You may have seen references to these: "flashvhigh", "flashaudio". etc.  Each mode corresponds to a set of media streams available from the BBC.  You can find details of recording modes later in this document.  

get_iplayer 2.83 and higher use a simplified system of recording mode shortcuts that should be sufficient for most users.  You are encouraged to use the mode shortcuts if at all possible.  You may still specify your own custom mode settings if you wish.

## Shortcuts 

Recording mode shortcuts use a simple system with four possible values: "good", "better", "best" and "default" (synonym for "better").  The mode shortcuts are used as values for the **--modes** parameter of the get_iplayer CLI (command-line interface), the **modes** option in your preferences or the **Recording Modes** field in the get_iplayer WPM (Web PVR Manager).

### You Need to Know This

If you are upgrading from get_iplayer 2.82 or earlier, be aware that the *default* recording mode - the mode used if you do not supply a value - has changed.  Beginning with get_iplayer 2.83, the default recording mode is set to download the best available SD video for TV programmes (flashvhigh).  get_iplayer 2.82 and earlier download lower-quality video (flashhigh) by default.  In practical terms, that means that after you upgrade from 2.82 or earlier your downloads will be nearly twice as large and take nearly twice as long (given constant bandwidth) as with the previous default mode setting.  See the next section for instructions on restoring the pre-2.83 behaviour.

WPM users:  If you saved a previous value of the **Recording Modes** field as your default it will still be honoured after upgrade.  However, after you upgrade to WPM 2.83 or higher you are strongly encouraged to set the **Recording Modes** field to one of the mode shortcuts as described in the next section and set the new value as your default.

### Choosing Your Mode

The easiest way to decide which shortcut to use is to answer a few simple questions:

- Do you want the default behaviour, which is to download the best available SD video for a single TV programme?

	CLI: `get_iplayer --modes=default […]`

	NOTE: `--modes=default` can be omitted for the CLI since it is, well, the default.

	WPM: Enter "default" (without quotes) in **Recording Modes** field and click **Apply Settings**, then record programme.

	NOTE: **Recording Modes** may not be left blank.
	
- Do you *always* want the default behaviour, which is to download the best available SD video for all TV programmes?

	CLI: `get_iplayer --prefs-add --modes=default`

	NOTE: It is not necessary to set this preference for the CLI  since it is, well, the default.

	WPM: Enter "default" (without quotes) in **Recording Modes** field and click **Save As Default**

	NOTE: **Recording Modes** may not be left blank.

- Do you want to download HD video (if available) for a single programme?

	CLI: `get_iplayer --modes=best […]`

	WPM: Enter "best" (without quotes) in **Recording Modes** field and click **Apply Settings**, then record programme.

	NOTE: Best available SD video will be downloaded if HD video not available.

- Do you *always* want to download HD video (if available) for all TV programmes?

	CLI: `get_iplayer --prefs-add --modes=best`

	WPM: Enter "best" (without quotes) in **Recording Modes** field and click **Save As Default**

	NOTE: Best available SD video will be downloaded if HD video not available.
	
- Do you want to revert to pre-2.83 default behaviour and download lower-quality video for a single programme?

	CLI: `get_iplayer --modes=good […]`

	WPM: Enter "good" (without quotes) in **Recording Modes** field and click **Apply Settings**, then record programme.

- Do you *always* want to revert to pre-2.83 default behaviour and download lower-quality video for all TV programmes?

	CLI: `get_iplayer --prefs-add --modes=good`
	 
	WPM: Enter "good" (without quotes) in **Recording Modes** field and click **Save As Default**

#### What About Radio?

get_iplayer downloads the best available quality for all radio programmes regardless of the mode shortcut used.  You can override this behaviour by using specific mode values (see below).

#### Show Me the Modes

See [below](#shortcut-expansions) for details of how shortcuts are expanded into mode lists.

## Recording Mode Details

The characteristics for all recording modes are shown below for reference: [TV](#tv-modes), [Radio](#radio-modes)

The recording quality for programmes is set by one of the mode options shown in the following table.  Note that you can set separate modes for each get_iplayer programme type. If no type-specific mode is defined, the **modes** option (if supplied) will be used.  If you use the **modes** option, take care to supply recording modes appropriate to the  type(s) of programmes you are downloading.  For example, using `--modes=flashhd` in a command to download a radio programme will prevent the download from succeeding.

Mode values are supplied as a comma-separated list of values which get_iplayer processes from the left to right.  The first mode found that matches an available media stream will be used for the download.  If the  download for the first mode fails, subsequent modes will be used.

A few examples:

- Set all recording modes (TV and Radio) explicitly to download best quality available:

		get_iplayer --get 123 --modes=flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow,flashaachigh,flashaacstd,flashaudio,flashaaclow,wma

- Record a single TV programme at the lowest quality available:

		get_iplayer --get 123 --tvmode=flashlow,flashstd,flashhigh,flashvhigh,flashhd

- Make a live radio recording in WMA format, with fallback to AAC format:

		get_iplayer --type=liveradio --liveradiomode=wma,flashaac "Radio 3"

- Record at a lower bit rate for speech radio programmes:

		get_iplayer --get 123 --type=radio --radiomode=flashaaclow

- Set a preference to *only* record the highest-quality (HD and SD) TV programmes, with no fallback to lower-quality video:

		get_iplayer --prefs-add --tvmode=flashhd,flashvhigh


#### Mode Options

|Options file|Command line|Description|
|------------|------------|-----------|
|modes|--modes &lt;mode&gt;,&lt;mode&gt;,...|Recording modes.  See --tvmode and --radiomode for available modes and defaults. Shortcuts: default,good,better(=default),best. Use --modes=best to select highest quality available (incl. HD TV).|
|tvmode|--tvmode &lt;mode&gt;,&lt;mode&gt;,...|TV recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow. Shortcuts: default,good,better(=default),best,rtmp,flash. (Use &#39;best&#39; for HD TV.)|
|radiomode|--radiomode &lt;mode&gt;,&lt;mode&gt;,...|Radio recording modes: flashaachigh,flashaacstd,flashaudio,flashaaclow,wma. Shortcuts: default,good,better(=default),best,rtmp,flash,flashaac. (&#39;default&#39;=flashaachigh,flashaacstd,flashaudio,flashaaclow,wma)|
|livetvmode|--livetvmode &lt;mode&gt;,&lt;mode&gt;,...|Live TV recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow. Shortcuts: default,good,better(=default),best,rtmp,flash. (&#39;default&#39;=flashvhigh,flashhigh,flashstd,flashnormal,flashlow)|
|liveradiomode|--liveradiomode &lt;mode&gt;,&lt;mode&gt;,...|Live Radio recording modes: flashaachigh,flashaacstd,flashaudio,flashaaclow,wma. Shortcuts: default,good,better(=default),best,rtmp,flash,flashaac. (&#39;default&#39;=flashaachigh,flashaacstd,flashaaclow,wma)|

<a name="tv-modes"></a>
### TV Modes

Below are representative values for recordings made with each of the TV recording modes.

|Recording Mode|Access Method|Video Codec|Video Resolution|Video Bitrate|Audio Codec|Audio Bitrate|Overall Bitrate|
|----------------|-------------|-----------|----------------|-------------|-------------|-----------|-------------|---------------|  
|**flashhd**|RTMP streaming|H.264|1280 x 720|2682 kbps|AAC|96 kbps|2781 kbps|  
|**flashvhigh**|RTMP streaming|H.264|832 x 468|1404 kbps|AAC|96 kbps|1505 kbps|  
|**flashhigh**|RTMP streaming|H.264|640 x 360|700 kbps|AAC|96 kbps|801 kbps| 
|**flashstd**|RTMP streaming|H.264|640 x 360|384 kbps|AAC|62 kbps|453 kbps|  
|**flashnormal**|RTMP streaming|H.264|512 x 288|672 kbps|AAC|128 kbps|841 kbps|  
|**flashlow**|RTMP streaming|H.264|512 x 288|300 kbps|AAC|62 kbps|368 kbps|  

*(Source: Beebhack)*

<a name="radio-modes"></a>
### Radio Modes

Below are representative values for recordings made with each of the radio recording modes.

|Recording Mode|Source|Access Method|Audio Codec|Audio Bitrate|Notes|
|--------------|------|-------------|-----------|-------------|-----|
|**flashaachigh**|Radio 3|RTMP streaming|AAC|320 kbps|Radio 3 live only| 
|**flashaacstd**|National Radio|RTMP streaming|AAC|128 kbps|320 kbps (Radio 3 only)|
|**flashaaclow**|National Radio|RTMP streaming|AAC|48 kbps||
|**flashaudio**|Regional and Local Radio|RTMP streaming|MP3|128/80 kbps|Regional radio: 128 kbps AAC live / 128 kbps MP3 catch-up, Local radio: 96 kbps AAC live / 80 kbps MP3 catch-up|
|**wma**|National, Regional and Local Radio|MMS streaming|WMA|96 kbps|320 kbps (Radio 3 only)|

<a name="shortcut-expansions"></a>
### Shortcut Expansions

The tables below detail how recording mode shortcuts are expanded into lists of mode values.

#### TV Shortcuts
|Shortcut|Modes|Notes|  
|--------|-----|-----|  
|**good**|flashhigh,flashstd,flashnormal,flashlow||
|**better**|flashvhigh + 'good'||
|**best**|flashhd + 'better'||
|**default**|synonym for 'better'||
|**flash**|same as 'default'|for backwards compatibility|
|**rtmp**|same as 'default'|for backwards compatibility|

#### Live TV Shortcuts

Same as TV Shortcuts

#### Radio Shortcuts

|Shortcut|Modes|Notes|  
|--------|-----|-----|  
|**good**|flashaachigh,flashaacstd,flashaudio,flashaaclow||
|**better**|same as 'good'||
|**best**|same as 'good'||
|**default**|synonym for 'better'||
|**flash**|flashaachigh,flashaacstd,flashaudio,flashaaclow||
|**rtmp**|same as 'flash'|for backwards compatibility|
|**flashaac**|flashaachigh,flashaacstd,flashaaclow||

#### Live Radio Shortcuts

Same as Radio Shortcuts

## Modes and CDNs

BBC iPlayer programmes may be available from more than one content distribution network (CDN).  A CDN is an external provider of media streaming services and infrastructure.  get_iplayer internally differentiates between available CDNs with a number appended to recording modes.  The metadata for a TV programme might show the following:

	modes:    default: flashhd1,flashhd2,flashhigh1,flashhigh2,flashlow1,flashlow2,flashstd1,flashstd2,flashvhigh1,flashvhigh2,subtitles1

This indicates that the flash* streams are available from two CDNs. Radio programmes are only available from a single CDN:

	modes:    default: flashaaclow1,flashaacstd1,wma1

The CDNs that correspond to the "1" and "2" may be different for each invocation of get_iplayer.  It is not possible to predict which CDN will be be used for a given recording.  In general it is not necessary to specifically designate a CDN when recording a programme.  If, for example, get_iplayer cannot download the flashhd1 stream, it will roll over to the flashhd2 stream and retry the download.  

**NOTE:** get_iplayer does not roll over to another CDN when recording live streams.

There may be times when the #1 CDN is not responding properly or rejecting connections.  You can force the use of the #2 CDN by explicitly setting your recording modes with the "2" appended.  An example:

	get_iplayer --get 123 --tvmode=flashhd2,flashvhigh2

Be aware that the #2 CDN in your second attempt may correspond to the problematic #1 CDN from the previous download attempt, so a few retries may be required to get a connection to the working CDN.

## External Programs

The table below shows the external programmes required to download and - if applicable - convert and tag files produced from each combination of recording mode and output format used by get_iplayer.

|Type|Mode|Format|rtmpdump|ffmpeg|mplayer|atomicparsley|id3v2/MP3::Tag|
|----|----|------|--------|------|-------|-------------|--------------|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>&#160;|mp4<br/>mp4<br/>mp4<br/>mp4<br/>avi<br/>mp4<br/>(h264/aac)|X|X|---|X|---|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --raw)|flv<br/>(h264/aac)|X|---|---|---|---|
|TV|flashhd<br/>flashvhigh<br/>flashhigh<br/>flashstd<br/>flashnormal<br/>flashlow<br/>(with --mkv)|mkv<br/>(h264/aac)|X|X|---|---|---|
|Radio|flashaudio|mp3|X|---|X|---|X|
|Radio|flashaudio<br/>(with --raw)|flv<br/>(mp3)|X|---|---|---|---|
|Radio|flashaachigh<br/>flashaacstd<br/>flashaaclow|m4a<br/>(aac)|X|X|---|X|---|
|Radio|flashaachigh<br/>flashaacstd<br/>flashaaclow<br/>(with --raw)|flv<br/>(aac)|X|---|---|---|---|
|Radio|flashaachigh<br/>flashaacstd<br/>flashaaclow<br/>(with --aactomp3)|mp3|X|X|---|---|X|
|Radio|wma|wma|---|---|X|---|---|
|Podcast|podcast|mp3|---|---|---|---|---|

*(Source: linuxcentre.net)*