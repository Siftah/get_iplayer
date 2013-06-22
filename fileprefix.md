## get_iplayer File Prefix Configuration

get_iplayer 2.83 introduced a slightly extended syntax for substitution parameters used with the `fileprefix` option.  It is now possible to define separators in `fileprefix` that are omitted when the associated parameter is empty.  This should be of use to all get_iplayer users, but will be of particular value to XBMC users since XBMC expects particular formats for names of files to be automatically imported.

From [this mailing list post](http://www.mail-archive.com/get_iplayer@lists.infradead.org/msg03745.html):

>A rather trivial question, but hopefully someone can come up with a solution:
>
>My options file has the entry:
>
>fileprefix `<nameshort>-<episodeshort>-<senum>`
>
>Which when I grab an episode of a series gives me exactly what I want.
>
>When I grab a 'one-off' programme, i.e. there is no series/episode, I end up with a file called name--.mp4
>
>Is there some invocation I can use in the options file which will automagically get rid of the trailing '-' characters?

Taking the example above:

	fileprefix <nameshort>-<episodeshort>-<senum>

Each substitution parameter can now have the separator defined as a prefix inside the left angle bracket:

	fileprefix <nameshort><-episodeshort><-senum>

This signifies that the prefix will be omitted if the associated parameter value is empty.

Below are some examples showing how the output file prefix is altered by the changes in get_iplayer 2.83+.  OLD and NEW refer to pre- and post-2.83 behaviour, respectively.

1. The Painted Veil (film, series/episode numbers undefined)

		OLD: The_Painted_Veil---
		NEW: The_Painted_Veil

	Films don't have `<episodeshort>` or `<senum>` defined.

2. Turner's Thames (non-film, series/episode numbers undefined)

		OLD: Turners_Thames---
		NEW: Turners_Thames.s01e01

	Non-film programmes that are one-offs (e.g., standalone documentaries) don't have `<episodeshort>` or `<senum>` defined. Series and episode numbers are forced to 1 in order to distinguish them from films.

3. Dancing on the Edge (non-film, series number undefined)

		OLD: Dancing_on_the_Edge-Episode_1-s00e01
		NEW: Dancing_on_the_Edge-Episode_1-s01e01

	TV series that are one-offs or have yet to be recommissioned don't have a series number, so it is forced to 1. This should keep XBMC happy.

4. Silent Witness (non-film, episode number undefined)

		OLD: Silent_Witness-Change_Part_1-s16e00
		NEW: Silent_Witness-Change_Part_1-s16e00

	There is no difference since when get_iplayer can determine the series number but can't determine an episode number, there is no way to select an arbitrary value for the latter. It will have to be fixed manually.