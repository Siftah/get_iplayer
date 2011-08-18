## How to Build the get_player Windows installer (VERSION 4.3)

### Prerequisites

1. **Strawberry Perl**

	Source: [http://strawberryperl.com](http://strawberryperl.com)

	Version: 5.12.3.0

	The installer is built with the Strawberry Perl distribution that is in your system path.  If you are using a different version, you may need to uninstall it and temporarily install the appropriate version.  Note that Strawberry Perl 5.12+ provides a mechanism to switch between versions without uninstalling.

2. **Perl Modules**

	Additional modules must be installed into the Perl distibution used to build the installer:  

	* MP3::Info (1.13)    - Used in localfiles plugin
	* MP3::Tag (1.24)     - Used to enhance MP3 tagging
	* PAR::Packer (1.010) - Used to build installer
	
	The modules may be installed with the CPAN client provided by Strawberry Perl.

3. **NSIS**

	Source: [http://nsis.sourceforge.net](http://nsis.sourceforge.net)

	Version: 2.46

	Select the **Full** installation option to install all components.

4. **NSIS Plugins**

	Source: [http://nsis.sourceforge.net/Category:Plugins](http://nsis.sourceforge.net/Category:Plugins)

	The installer requires the following NSIS plugins:

	* Locate
	* Nsis7z
	* ZipDLL

	Information on installing NSIS plugins: 
	[http://nsis.sourceforge.net/How\_can\_I\_install\_a\_plugin](http://nsis.sourceforge.net/How\_can\_I\_install\_a\_plugin)

5. **7-Zip**

	Source:  [http://www.7-zip.org](http://www.7-zip.org)

	Version: 9.20 (select 32-bit .exe installer)

	The installer build scripts use the command-line interface to 7-Zip to compress/expand archive files.  However, it is not necessary to install the separate statically-linked version of the 7-Zip (7za.exe).  The GUI version has its own command-line interface.

### Build Setup

In the instructions below, replace with `C:\work` with an appropropriate location for your system

1. **Download get_player Source Distribution**

	This can be a clone of the infradead git repository or a downloaded snapshot.

	Location: `C:\work\get_player`

2. **Check Build Configuration**

	The files below should be in: `C:\work\get_player\windows`

	* `get_iplayer_setup.nsi` - NSIS installer script
	* `make-init.cmd`         - common initialisation code for other scripts
	* `make-installer.cmd`    - main installer build script (calls make-perlfiles.cmd)
	* `make-perlfiles.cmd`    - builds archive of Perl support files for installer
	* `make-perltgz.cmd`      - converts archive of Perl support files to tarball

	`make-init.cmd` sets the locations of Strawberry Perl, NSIS, and 7-Zip used for the build.  Edit the relevant values if necessary.

3. **Create Build Folder**

	Create an empty folder to use for building the installer:

	`C:\>MKDIR C:\work\installer`

### Installer Build

1. Open a command prompt and make the build folder the current directory

	`C:\>CD C:\work\installer`

	The installer may be built in any directory, but the build folder must be the current directory for your command prompt.

2. Run the installer build script

	`C:\work\installer>C:\work\get_iplayer\windows\make-installer`

	The build script creates 4 files in the build directory:

	* `get_iplayer_setup-4.3.exe` - get_player installer application
	* `perlfiles.zip`             - archive of Perl support files included in the installer
	* `perlpar.exe`               - PAR (Perl ARchive) file used to create perlfiles.zip
	* `make-installer.log`        - log of output from build script

	In the event of an error, the temporary folder used by the script (`make-installer.tmp`) will remain in the build directory.

3. There is no step 3

#### Notes

* Subsequent invocations of `make-installer.cmd` will use an existing `perlfiles.zip` if it is found in the current directory.  To force the Perl support archive to be complete rebuilt, add `/makeperl` to the command:

	`C:\work\installer>C:\work\get_iplayer\windows\make-installer /makeperl`

* `perlfiles.zip` must be generated in Windows in order for the proper Win32 modules to be included in the archive.  However, the archive may be used to build the installer on Linux/OSX (see below).  To that end, a separate script (`make-perlfiles.cmd`) may be used to generate only the Perl support archive.  It is also invoked by `make-installer.cmd` to build the archive.

* Subsequent invocations of `make-perlfiles.cmd` will use an existing `perlpar.exe` if it is found in the current directory.  To force the Perl support archive to be complete rebuilt, add `/makepar` to the command:

	`C:\work\installer>C:\work\get_iplayer\windows\make-perlfiles /makepar`

	Invoking `make-installer.cmd` with `/makeperl` will have the same effect.
	
	In the event of an error, the temporary folder used by the script (`make-perlfiles.tmp`) will remain in the build directory.

* Both `make-installer.cmd` and `make-perlfiles.cmd` respond to a single `/?` parameter with a usage message showing all the parameters that may be passed.  However, the additional parameters are currently only useful for use in development and testing and thus will not be described here.
	
#### Linux/OSX

* A shell script (`get_iplayer/make-nsis.sh`) was written to build the `get_iplayer` Windows installer on Linux/OSX.  However, it expects to find the Perl support archive in the form of a tarball (.tar.gz).  Since tarball support is ubiquitous in the Unix realm, this aspect of `make-nsis.sh` has been left as-is.  If you should need to build the installer on another platform, you can create the tarball in Windows and transfer it to the other system.  After building the Perl support archive (see above), execute an additional script:

	`C:\work\installer>C:\work\get_iplayer\windows\make-perltgz`
	
	The script looks for `perlfiles.zip` in the current directory and copies its contents to `perlfiles.tar.gz`.

* Building the installer on Linux/OSX is similar to building in Windows.  Assuming you have the get_iplayer source in `$HOME/get_iplayer` and are using `$HOME/installer` as your build folder:

	Copy `perlfiles.tar.gz` into the build folder

	`# cp $WHEREVER/perlfiles.tar.gz $HOME/installer`
	
	Make the build folder your current directory:
	
	`# cd $HOME/installer`
	
	Execute the build script:
	
	`# $HOME/get_iplayer/make-nsis.sh`
	
	The installer application will be copied into the current directory.  As in Windows, the installer may be built in any folder, but the build folder must be the current directory for your shell.
	
### Installer Distribution

*TBD*
