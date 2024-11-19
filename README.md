# SpectralSuite

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
