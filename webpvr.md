# get_iplayer Web PVR Manager

## About

The Web PVR Manager (WPM) is a Web-based search front-end to get_iplayer which allows you, through a web browser, to manage the get_iplayer PVR and start recordings. You are able to search all of the programmes indexed by get_iplayer. It also has a built-in streaming proxy server so you can play get_iplayer content from the web browser or using simple HTTP URLs. It automatically generates OPML and M3U playlists for any programme type so that media players can use the streams.

**THIS IS BETA CODE!!! DO NOT RUN THIS ON AN UNTRUSTED NETWORK**

## Installation

See the [get_iplayer installation page](installation) for instructions on how to install and run WPM.  Bear in mind that WPM is a front end for the get_iplayer command-line interface (CLI), so you must install the CLI, its related Perl modules and the necessary external applications along with WPM.  In particular, note that [ffmpeg](http://ffmpeg.org) and [rtmpdump](http://rtmpdump.mplayerhq.hu/) are required for streaming or recording of the Flash streams that comprise the bulk of BBC iPlayer content.

Windows users should download and run the latest [get_iplayer installer](http://www.infradead.org/get_iplayer_win/get_iplayer_setup_latest.exe), which will set up everything you need.  You can launch WPM from *get_iplayer -> Web PVR Manager* on the Start menu or the *Web PVR Manager* tile in Windows 8.

It is also recommended to install [VLC Media Player](http://www.videolan.org/vlc/) to use with the **Play** links (see below).

## Usage

### Page Tabs

There are several different tabs along the top of the page:

- **Search** – Shows you a list of all **available** programmes that match your default options. Use any of the search criteria presented, enter a search term then click the **Search** button below (select the **Advanced Search** tab to get more search options).
- **Recordings** – Shows you a list of all **recorded** programmes that match your default options. Use any of the search criteria presented, enter a search term then click the **Search** button below (click **Advanced Search** to get more search options).
- **PVR List** – Shows you a list of currently saved PVR searches or queued recordings (you can delete them from here also)
- **Run PVR** – Runs the PVR immediately in a new tab – make sure you wait for it to fully complete before closing the browser screen. If you do not close the tab it will automatically run the PVR every 4 hours.
- **Update Software** - Updates to the latest PVR Manager script (if it is writable) – make sure you restart the service after doing so. This feature is unavailable in Windows – use the installer and re-install the get_iplayer component to get the latest Web PVR Manager.
- **Help** – Sends you here.

### Action Buttons

There are several different action buttons along the top and bottom of the search results:

- **Search** – Enter your search term in the *Search* field and click this button to execute the search.  You and target your search at a field other than *Name* by changing the value of *Search in*.  Additional search options may found in the **Advanced Search** tab. You can search the PVR recordings history instead of the available programmes by selecting *Search History* in the search panel

> **HEY! OVER HERE!** - With the default settings WPM will only search TV programmes.  Select the *BBC Radio* checkbox to add radio programmes to the search results.

- **Record** – Select the checkbox next to the programme(s) you want to record and click this for immediate recording in a separate browser tab.

>**HEY! OVER HERE!** - In Linux/Unix/OSX recordings are saved by default in the directory where you started the WPM service. With the Windows installer version of WPM recordings are saved by default in the `iPlayer Recordings` folder on your desktop. You can override this in your get_iplayer preferences, or you may enter a new location in the *Override Recordings Folder* field in the **Recording** settings tab.

- **Play** – Select the checkbox next to the programme(s) you want to playback and click this to download an m3u playlist (you should associate m3u playlists with VLC in your browser for immediate playback).

- **Queue** – Select the checkbox next to the programme(s) you want to record and click this to queue them for when the PVR next runs (i.e.by clicking ‘Run PVR’).

- **Add Search to PVR** – Once you have added the search terms to get the list of programmes you wish to regularly record, click this button.

>**HEY! OVER HERE!** - The queued recordings and PVR searches that you add will only actually be recorded when you click the **Run PVR** button at the top of the page.

- **Refresh Cache** – You must regularly refresh the programme cache to see new programmes. Clicking this opens another tab that refreshes the list of programmes from the online feeds of the selected programme type web sites. If you leave it open it will auto-refresh every 4 hours unless you override the settings.

	**NOTE:** It may take a while to reload page when refreshing caches.

- **Quick URL** - To record or play a BBC iPlayer audio or video URL, paste the URL into the *Quick URL* box and click **Play** or **Record**


### Programme Links

#### Actions

- **Play** - Play back a programme by clicking its *Play* link. The *Play* link generates an m3u playlist with a single programme in it. You can associate m3u playlists with VLC for immediate playback.

- **Queue** - Queue a programme for recording by clicking its *Queue*.

- **Record** - Immediately record a programme (opens a new tab) by clicking its *Record* link.

	**NOTE:** Only two recording tabs can work at any one time.

- **Add Series** - Add a programme's whole series (including future episodes) to the PVR by click its *Add Series*.


#### Information

- Click the description text to retrieve full metadata for a programme

- Click any underlined text to search only for that clicked text, e.g., a series name or content category.

- Click a thumbnail image to go to the associated episode web site

- Sort columns by clicking the headings

- Add or remove columns in the search results by selecting checkboxes in the Columns settings tab

## Settings

Settings are grouped into 5 tabs: Advanced Search, Display, Columns, Recording and Streaming.  Hover over any form field with your mouse to see a tooltip with a brief description of its purpose.

>**HEY! OVER HERE!** - WPM does not download HD TV (where available) by default out of consideration for users with limited internet bandwidth.  If you wish to download HD TV, change the value of *Recording Modes* in the **Recording** tab to "best" (without quotes).  Use the **Save As Default** button to make the setting permanent (see below).

The settings correspond to options for the get_iplayer CLI.  See [this page](manpage) for a full list.  Not all get_iplayer options are available to the WPM.  For those options, get_iplayer uses either its default values or values that have been saved to its user options file with `get_iplayer --prefs-add` (examples [here](documentation#Saving%20Settings)).

When you change settings, use the buttons beneath the settings tabs to apply them:

- **Apply Settings** applies the options in settings tabs to the current search.

- **Save As Default** saves the options in settings tabs and a few of the standard settings such as Programme Type. The settings are saved as browser cookies.

- **NOTE:** When using the stream, playlist or play links directly, cookies are not sent and the settings are not applied.

## Streaming

### Direct Streaming URLs

Web PVR Manager allows you to stream audio and video to media player
software such as VLC, mplayer, ffplay and hardware streamers such as the
Logitech Squeezebox by creating URLs for the following:

- Stream BBC iPlayer programmes directly from the Internet as FLV streams
- Stream pre-recorded programmes losslessly or by transcoding on-the-fly
- Stream mp3 files using the localfiles get_iplayer plugin

The [README](https://raw.github.com/dinkypumpkin/get_iplayer/master/README-get_iplayer.cgi.txt) gives examples.

### Automatic Playlist URLs

Web PVR Manager allows you to create M3U playlists on-the-fly from searches to enable you to stream audio and video to media player software such as VLC, mplayer, ffplay and hardware streamers such as the Logitech Squeezebox. These playlist URLs can:

- Create playlists of currently available programmes based on user defined search criteria
- Create playlists of pre-recorded programmes based on user defined search criteria
- Create OPML playlists which can be used to selectively navigate on devices like the Logitech Squeezebox

The [README](https://raw.github.com/dinkypumpkin/get_iplayer/master/README-get_iplayer.cgi.txt) gives examples.

## CGI Deployment

The [README](https://raw.github.com/dinkypumpkin/get_iplayer/master/README-get_iplayer.cgi.txt) contains instructions.

*Source: linuxcentre.net*