## get_iplayer Recording Modes

BBC iPlayer makes programmes available a different levels of video and audio quality.  get_iplayer represents each video/audio quality level with an alphanumeric code, referred to as a "mode".  


|Options file|Command line|Description|
|------------|------------|-----------|
|modes|--modes &lt;mode&gt;,&lt;mode&gt;,...|Recording modes.  See --tvmode and --radiomode for available modes and defaults. Shortcuts: default,good,better(=default),best. Use --modes=best to select highest quality available (incl. HD TV).|
|tvmode|--tvmode &lt;mode&gt;,&lt;mode&gt;,...|TV recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow. Shortcuts: default,good,better(=default),best,rtmp,flash. (Use &#39;best&#39; for HD TV.|
|radiomode|--radiomode &lt;mode&gt;,&lt;mode&gt;,...|Radio recording modes: flashaachigh,flashaacstd,flashaudio,flashaaclow,wma. Shortcuts: default,good,better(=default),best,rtmp,flash,flashaac. (&#39;default&#39;=flashaachigh,flashaacstd,flashaudio,flashaaclow,wma)|
|livetvmode|--livetvmode &lt;mode&gt;,&lt;mode&gt;,...|Live TV recording modes: flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow. Shortcuts: default,good,better(=default),best,rtmp,flash. (&#39;default&#39;=flashvhigh,flashhigh,flashstd,flashnormal,flashlow)|
|liveradiomode|--liveradiomode &lt;mode&gt;,&lt;mode&gt;,...|Live Radio recording modes: flashaachigh,flashaacstd,flashaudio,flashaaclow,wma. Shortcuts: default,good,better(=default),best,rtmp,flash,flashaac. (&#39;default&#39;=flashaachigh,flashaacstd,flashaaclow,wma)|


### TV Recording Modes

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

### Radio Recording Modes

Below are representative values for recordings made with each of the radio recording modes.

|Recording Mode|Access Method|Audio Codec|Audio Bitrate|Notes|
|--------------|-------------|-----------|-------------|-----|
|**flashaachigh**|RTMP streaming|AAC|320 kbps|Radio 3 live only| 
|**flashaacstd**|RTMP streaming|AAC|128 kbps|-|
|**flashaaclow**|RTMP streaming|AAC|48 kbps|-|
|**flashaudio**|RTMP streaming|MP3|128 kbps|-|
|**wma**|MMS streaming|WMA|96 kbps|320 kbps (Radio 3 only)|

<a name="external-programs"></a>
### External Programs

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