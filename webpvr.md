# get_iplayer Web PVR Manager

## About

This is a Web-based search front-end to get\_iplayer which
allows you, through a web browser, to manage the get\_iplayer PVR and
start recordings. You are able to search all of the programmes indexed
by get\_iplayer. It also has a built-in streaming proxy server so you
can play get\_iplayer content from the web browser or using simple HTTP
URLs. It automatically generates OPML and M3U playlists for any
programme type so that media players can use the streams.

**THIS IS BETA CODE!!! DO NOT RUN THIS ON AN UNTRUSTED NETWORK**

## Platforms

I am only testing this on Linux and Windows. However it is reported to work on OS X and Cygwin. I’ve only tested with Firefox 3.5. Ensure you have any ‘NoScript’ type plug-ins disabled).

## Requirements

- The software requires Perl and a number of fairly standard perl modules.
- For Windows you should install the latest [get\_iplayer installer](http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe) which will install everything you need.
- For the other platforms you must have a recent [get\_iplayer](http://www.infradead.org/get_iplayer/get_iplayer)
installed and working.
- [ffmpeg](http://linuxcentre.net/getiplayer/download/) and [rtmpdump](http://savannah.nongnu.org/projects/flvstreamer) are also required if you want to do streaming or recording of flash streams. 
- It is a good idea to install [VLC Media Player](http://www.videolan.org/vlc/) if you want the ‘Play’ links to work in the GUI.

## Download

You can download the latest release version of Web PVR Manager [here](http://www.infradead.org/get_iplayer/latest/get_iplayer.cgi).

The README file with latest usage and instructions for installation are [here](http://www.infradead.org/get_iplayer/README-get_iplayer.cgi.txt).

The change log for both get\_iplayer and Web PVR Manager is [here](http://www.infradead.org/get_iplayer/CHANGELOG-get_iplayer)

## Starting the Web PVR Manager service

You need to run the Web PVR Manager service (unless you plan to install under Apache web server). This service contains its own embedded web server which can run on any free TCP port above 1024.

On Linux/Unix/OSX start it using:

	perl get_iplayer.cgi --port=1935 --getiplayer=/path/to/get_iplayer

Then you point your web browser at [http://127.0.0.1:1935/](http://127.0.0.1:1935/)

On Win32, start it using the menu: `Start -> Programs -> get_iplayer -> Web PVR Manager`.  The default web browser will automatically open to the correct page.

## Usage

**Web GUI** 

There are several different tabs along the top of the page:

- **Search** – Shows you a list of all **available** programmes that match your default options. Use any of the search criteria presented, enter a search term then click the **Search** button below (select the **Advanced Options** tab to get more search options).
- **Recordings** – Shows you a list of all **recorded** programmes that match your default options. Use any of the search criteria presented, enter a search term then click the **Search** button below (click **Advanced Search** to get more search options).
- **PVR List** – Shows you a list of currently saved PVR searches or queued recordings (you can delete them from here also)
- **Run PVR** – Runs the PVR immediately in a new tab – make sure you wait for it to fully complete before closing the browser screen. If you do not close the tab it will automatically run the PVR every 4 hours.
- **Update Software** - Updates to the latest PVR Manager script (if it is writable) – make sure you restart the service after doing so. This feature is unavailable in Windows – use the installer and re-install the get\_iplayer component to get the latest Web PVR Manager.
- **Help** – Sends you here.

There are several different action buttons along the top and bottom of the search results:

- **Record** – select the checkbox next to the programme(s) you want to record and click this for immediate recording in a separate browser tab.
- **Play** – select the checkbox next to the programme(s) you want to playback and click this to download an m3u playlist (you should associate m3u playlists with VLC in your browser for immediate playback).
- **Queue** – select the checkbox next to the programme(s) you want to record and click this to queue them for when the PVR next runs (i.e.by clicking ‘Run PVR’).
- **Add Search to PVR** – Once you have added the search terms to get the list of programmes you wish to regularly record, click this button.
- **Refresh Cache** – You must regularly refresh the programme cache to see new programmes. Clicking this opens another tab that refreshes the list of programmes from the online feeds of the selected programme type web sites. If you leave it open it will auto-refresh every 4 hours unless you override the settings.
- To Record or Play a BBC audio or video URL, paste the URL into the **Quick URL** box with a iPlayer URL in it and click **Play** or **Record**
- You can play back the programme using the **Play** link on each programme. The Play link just generates an m3u playlist with a single programme in it. (you should associate m3u playlists with VLC in your firefox browser for immediate playback).
- You can immediately queue a programme for recording if you simply click the **Queue** link next to any programme.
- You can immediately record a programme (opens a new tab) if you simply click the **Record** link next to any programme.
- You can immediately add a whole series (including future episodes) to the PVR if you simply click the **Add Series** link next to any programme.
- You can search the PVR recordings history instead of the available programmes by selecting **Search History**
- Clicking any programme description text will get its full info
- Clicking any underlined programme text will search only for that clicked text
- Clicking the Thumbnail will go to the episode web site
- You can sort columns by clicking the heading
- Columns can be added and removed by clicking the checkbox in the Columns tab.
- **Apply Settings** applies the options in settings tabs to the current search.
- **Save As Default** saves the options in settings tabs and a few of the standard settings such as Programme Type. The settings are saved as browser cookies.
- Inherits default settings from get\_iplayer if not available in this GUI

**Notes**

- The queued recordings and PVR searches that you add will only actually get recorded when you click ‘Run PVR’.
- Recordings are saved in the directory where you started the service under Linux/Unix/OSX. Under the Windows installer version the files are recorded to the selected ‘iPlayer Recordings’ folder. You can override this in the get\_iplayer default options should you wish.

### Direct Streaming URLs

Web PVR Manager allows you to stream audio and video to media player
software such as vlc, mplayer, ffplay and hardware streamers such as the
Logitech Squeezebox by creating URLs for the following:

- Stream BBC iPlayer programmes directly from the Internet as FLV streams
- Stream any Pre-recorded programme losslessly or by transcoding on-the-fly
- Stream any mp3 files using the localfiles get\_iplayer plugin

The [README](http://www.infradead.org/get_iplayer/README-get_iplayer.cgi.txt) gives examples.

### Automatic Playlist URLs

Web PVR Manager allows you to create M3U playlists on-the-fly from searches to enable you to stream audio and video to media player software such as vlc, mplayer, ffplay and hardware streamers such as the Logitech Squeezebox. These playlist URLs can:

- Create playlists of currently available programmes based on user defined search criteria
- Create playlists of any pre-recorded programme based on user defined search criteria
- Create OPML playlists which can be used to selectively navigate on devices like the Logitech Squeezebox

The [README](http://www.infradead.org/get_iplayer/README-get_iplayer.cgi.txt) gives examples.

### Caveats

- Sometimes takes a while to load page while refreshing caches.
- Only two simultaneous recording tabs can work at any one time (will fix this soon).
- When using the stream, playlist or play links directly, cookies are not sent and the settings are not applied.
