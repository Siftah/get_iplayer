## get_iplayer Recording Modes

The BBC iPlayer service makes programmes available in different levels of video and audio quality.  


|Recording Mode|Access Method|Video Codec|Video Resolution|Video Bitrate|Video Quality|Audio Codec|Audio Bitrate|Overall Bitrate|
|----------------|-------------|-----------|----------------|-------------|-------------|-----------|-------------|---------------|  
|**flashhd**|RTMP streaming|H.264|1280 x 720|2682 kbps|better than DVD|AAC|96 kbps|2781 kbps|  
|**flashvhigh**|RTMP streaming|H.264|832 x 468|1404 kbps|better than VHS|AAC|96 kbps|1505 kbps|  
|**flashhigh**|RTMP streaming|H.264|640 x 360|700 kbps|Near VHS|AAC|96 kbps|801 kbps|
|**flashstd**|RTMP streaming|H.264|640 x 360|384 kbps|Below VHS|AAC|62 kbps|453 kbps|  
|**flashnormal**|RTMP streaming|H.264|640 x 360|672 kbps|Below VHS|AAC|128 kbps|835 kbps|  
|**flashlow**|RTMP streaming|H.264|512 x 288|300 kbps|Below VHS|AAC|62 kbps|368 kbps|  

|Recording Mode|Access Method|Video Codec|Video Resolution|Video Bitrate|Video Quality|Audio Codec|Audio Bitrate|Overall Bitrate|
|----------------|-------------|-----------|----------------|-------------|-------------|-----------|-------------|---------------|  
|**flashaachigh**|RTMP streaming|H.264|1280 x 720|2682 kbps|better than DVD|AAC|96 kbps|2781 kbps|  
|flashaacstd|RTMP streaming|H.264|832 x 468|1404 kbps|better than VHS|AAC|96 kbps|1505 kbps|  
|flashaaclow|RTMP streaming|H.264|640 x 360|700 kbps|Near VHS|AAC|96 kbps|801 kbps|
|flashaudio|RTMP streaming|H.264|640 x 360|384 kbps|Below VHS|AAC|62 kbps|453 kbps|  
|wma|RTMP streaming|H.264|640 x 360|672 kbps|Below VHS|MP3 44kHz CBR|128 kbps|835 kbps|  
|flashlow|RTMP streaming|H.264|512 x 288|300 kbps|Below VHS|AAC|62 kbps|368 kbps|  

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

