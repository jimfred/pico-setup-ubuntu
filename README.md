# pico-setup-ubuntu
For Ubuntu 22.04.1 LTS
The original pico-setup was intended to run on a R-Pi and worked somewhat on Ubuntu.
Things that didn't work completely on Ubuntu:
- Visual Studio code didn't install - Ubuntu wanted to install a snap instead of using apt
- udev rules are needed for openocd (for debug and for serial)
- The gdb-multiarch, version 12.0.90, had a bug that caused the debugger to throw an assertion whenever the target program paused. Solution here: https://forums.raspberrypi.com/viewtopic.php?t=333992#p2045778
