# SpectralSuite

To build ensure the 'public.sdk', 'plugininterfaces' and 'vstgui' 
folders from the 
Steinburg VST SDK are in the 'shared' folder

On Mac set an alias in ~/.zshrc for 'projucer' pointing to the projucer executable.
E.g: `alias projucer=~/Documents/Personal/JUCE/Projucer.app/Contents/MacOS/Projucer`


### Making a new plugin
The boilerplate code for a new plugin is handled for you with a python script. This uses python 3.12 or higher.
```bash
--> py makeSpectral.py -h
usage: makeSpectral.py [-h] -p PATH -n NAME [-d DESCRIPTION] [-v {True,False}]

Automate SpectralSuite boilerplate for new plugin.

options:
  -h, --help            show this help message and exit
  -p PATH, --path PATH  The relative or absolute path to the directory containing new plugin
  -n NAME, --name NAME  The name of the new plugin
  -d DESCRIPTION, --description DESCRIPTION
                        The description of the new plugin
  -v {True,False}, --verbose {True,False}
```
```bash
--> py makeSpectral.py -p NewThing/ -n "NEWNAME" -d "NEWDESC" -v True
--> ls NewThing/
NEWNAME.jucer		NEWNAMEParameters.cpp	NEWNAMEProcessor.h
NEWNAMEAudioPlugin.cpp	NEWNAMEParameters.h	UiContainer.cpp
NEWNAMEAudioPlugin.h	NEWNAMEProcessor.cpp	UiContainer.h
```

### Building plugins for release 
Build must be performed on Linux, MacOS or Windows.

#### MacOS
##### Prerequisites
Matching the version numbers may not be required. 
Ruby (2.7.4) to run the build scripts
XCode (15.4) 
MacOS intel (14.6.1)
Projucer (7)
[Packages](http://s.sudre.free.fr/Software/Packages/about.html) (1.2.9) to build the installer.

##### Steps
Update the project version in `SpectralSuiteBuild` `Base.jucer` file. 
In the preprocessor definitions increment the `VersionCode`.
Update `CHANGES.md` with the latest changes.

Then on the terminal naviate the `SpectralSuiteBuild` and run:
`ruby ssutil.rb`

This should update all projucer files with the version number and code. 
Start a build using xcode command line tools.
Copy the AU and VST3 files to a `release` folder in top level repository dir. 
Build a package that can be used for installing. This will be located in
`SpectralSuiteBuild/package/MacOS-SpectralSuite-vX.X.X.pkg`

#### Linux
##### Prerequisites

All essentials for compilation and folowing list of commands and libraries. You have to check Linux Dependencies file under the docs folder. In brief enough to enter `make` under the build folders.

```bash
    sudo apt update
    sudo apt install libasound2-dev libjack-jackd2-dev \
        ladspa-sdk \
        libcurl4-openssl-dev  \
        libfreetype6-dev \
        libx11-dev libxcomposite-dev libxcursor-dev libxcursor-dev libxext-dev libxinerama-dev libxrandr-dev libxrender-dev \
        libwebkit2gtk-4.1-dev \
        libglu1-mesa-dev mesa-common-dev
```
Configuration is ready, you can just run compilation with the `make` command under each the LinuxMake folder to reproduce all the necessary outputs such as vst3 or au files.

#### Windows 
##### Prerequisites
Visual Studio 2022
Powershell

##### Steps
Open Developer Powershell
Navigate to `SpectralSuiteBuild`.
Then run `ssutil.ps1`


