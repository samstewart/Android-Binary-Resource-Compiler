Developed and tested on Linux. Its a shell script that requires the Android SDK to be installed with the tools directory in the PATH variable.

###INTRO

Android Binary Resource Compiler (abrc). This is a command-line
script to compile resources such as NinePatch PNGs and layout XML
files to Android binary format. The compiled resources named in the
command are extracted and saved out into a separate location. This
script was developed as an alternative to using Eclipse and "unzip" to
compile and extract NinePatch PNGs during the creation of custom
Android UI themes.

###USAGE
abrc usage
abrc help 
abrc [options] compile <project dir> <output dir> <resource file1> <resource file2> ...
abrc [options] setup <project dir>

###OPTIONS:

-v Enable verbose output
-o Overwrite files without prompting

###COMPILE

The compile operation compiles the resources in the <project dir>
location. This can be any Android Eclipse project directory which
contains the resources you wish to compile and extract. You can also
use this script's "setup" syntax to create a minimal project without
using Eclipse. See the SETUP section below for more information.

The named resource files <resource file1> <resource file2>, etc., are
then extracted into the <output directory>. Parent path components in
the resource file names are preserved and also determine the extracted
location within the output directory.

###Example:

Consider the following path in "MyProject" which contains, among other
things, the statusbar_background.9.png file. This file is in the format
created by draw9patch program.

MyProject/res/drawable-mdpi/statusbar_background.9.png

The following command compiles the resources in MyProject and writes
the output to the MyTheme/framework-res directory using the leading
path components of the specified resource file(s). I.e., In this
example the resulting output file is
MyTheme/framework-res/res/drawable-mdpi/statusbar_background.9.png

abrc compile MyProject MyTheme/framework-res res/drawable-mdpi/statusbar_background.9.png

###SETUP

The setup operation is completely optional. It creates a minimal
project skeleton for compiling resources. Eclipse projects can also
be used in the compile step above.

abrc setup MyProject
The above command creates the following directory structure/files:

MyProject/res/drawable
MyProject/res/drawable-mdpi
MyProject/res/drawable-hdpi
MyProject/res/layout
MyProject/AndroidManifest.xml
Copy your resources into the appropriate location within the project
and then use the compile operation to compile and extract the binary
files.