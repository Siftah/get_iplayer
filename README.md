## get_iplayer: BBC iPlayer Indexing Tool and PVR

## Features

* Downloads TV and radio programmes from BBC iPlayer
* Allows multiple programmes to be downloaded using a single command
* Indexing of most available iPlayer catch-up programmes (not iPlayer Exclusive, Red Button or BBC Three)
* Caching of index (default 4h)
* Regex search on programme name 
* Regex search on programme description and episode title
* Filter search results by channel
* PVR capability (may be used with cron or Task Scheduler)
* HTTP proxy support
* Perl 5.8.8+ required, plus LWP, XML::Simple and XML::LibXML modules
* Runs on Linux/Unix (Ubuntu, Fedora, OpenBSD and others), OS X, Windows (7/8/10 supported, known to run on XP/Vista)

**NOTE: get_iplayer can only search programmes broadcast on BBC linear services within the previous 30 days, even if some are available for more than 30 days on the iPlayer web site. Other programmes must be downloaded directly.**

## Documentation

<https://github.com/get-iplayer/get_iplayer/wiki>
	
## Support

<https://github.com/get-iplayer/get_iplayer/wiki/help>

## Installation

<https://github.com/get-iplayer/get_iplayer/wiki/installation>

## Usage 
  
	get_iplayer --help
	get_iplayer --basic-help
	get_iplayer --long-help

## Examples

* List all TV programmes (`--type=tv` set by default):

	`get_iplayer`

	Search output appears in this format:

		...
		208:  Doctor Who: Series 7 Part 2 - 1. The Bells of Saint John, BBC One, b01rryzz
		209:  Doctor Who: Series 7 Part 2 - 2. The Rings Of Akhaten, BBC One, b01rx0lj
		210:  Doctor Who: Series 7 Part 2 - 3. Cold War, BBC One, b01s1cz7
		...

	Format = index: name - episode, channel, pid 
  
* List all TV programmes with long descriptions:

	`get_iplayer --long`

* List all radio programmes:

	`get_iplayer --type=radio`

* List all TV programmes with "doctor who" in the title/episode:

	`get_iplayer "doctor who"`

* List all TV and radio programmes with "doctor who" in the title/episode:

	`get_iplayer --type tv,radio "doctor who"`

* List all BBC One TV programmes:

	`get_iplayer --channel="BBC One"`

* List all Radio 4 Extra programmes:

	`get_iplayer --type=radio --channel="Radio 4 Extra"`
	
* List all Radio 4 programmes:

	`get_iplayer --type=radio --channel="Radio 4$"`

	*(The `$` regular expression metacharacter matches "Radio 4" only at the end of the channel name, thus avoiding matches against "Radio 4 Extra")*

* Record programme number 208 (index from search results) in HD, with SD fallback if HD not available:

	`get_iplayer --get 208` [default is to download best available]
	
	OR	

	`get_iplayer --get 208 --modes=best`

* Record programme number 208 in lower resolution (640x360):

	`get_iplayer --get 208 --modes=good`

* Record programme number 208 and download subtitles in SubRip (SRT) format:

	`get_iplayer --get 208 --subtitles`

* Record a programme using its iPlayer URL:

	`get_iplayer http://www.bbc.co.uk/iplayer/episode/b01sc0wf/Doctors_Series_15_Perfect/`

* Record a programme using the PID (b01sc0wf) from its iPlayer URL:

	`get_iplayer --pid=b01sc0wf`
  

Notes:

* Sometimes you may not be able to download a listed programme immediately after broadcast (usually available within 24hrs of airing). Some BBC programmes may not be available from iPlayer.
