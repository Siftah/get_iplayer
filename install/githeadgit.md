## Git HEAD - Using Git (all platforms)

"Git HEAD" is the latest development version of get_iplayer from the Git repository. There may be occasions when you wish to use the Git HEAD version of get_iplayer in order to test bug fixes or new features.

1. Clone the get_iplayer repository

		git clone git://github.com/dinkypumpkin/get_iplayer

	Alternate repository:

		git clone git://git.infradead.org/get_iplayer.git

2. The get_iplayer code will now be in a sub directory named `get_iplayer`:

        cd get_iplayer

3. Ensure you are working on the master branch

        git checkout master

4. Back up and replace existing CLI/WPM

	You may run both the CLI and WPM directly from the cloned repository. If you wish to update your existing installation:

	**Linux/Unix/OS X:** Proceed from step #2 in the CLI and WPM [[manual installation procedures|manual]].  If you are replacing a package installation, it is recommended that you first remove the get_iplayer package (but leave external programs installed), then follow the manual installation procedure to install the Git HEAD version to /usr/local/bin (or similar).

	**Windows:** See the instructions [[here|githeadwin]].


