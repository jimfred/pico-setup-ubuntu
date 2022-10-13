# pico-setup-ubuntu
For Ubuntu 22.04.1 LTS
The original pico-setup was intended to run on a R-Pi and worked somewhat on Ubuntu.

In Ubuntu in the `~/Downloads` do a `wget https://raw.githubusercontent.com/jimfred/pico-setup-ubuntu/master/pico_setup.sh`, fix file permissions and run and address issues listed below:

Things that didn't work completely on Ubuntu:
- Visual Studio code didn't install - Ubuntu wanted to install `snap install code --classic` instead of using `apt`.
Three extensions still need to be installed:
  ```
  code --install-extension marus25.cortex-debug
  code --install-extension ms-vscode.cmake-tools
  code --install-extension ms-vscode.cpptools
  ```
- udev rules are needed for openocd (for debug and for serial)
Fixes problems seen as:
"error: Can't find a picoprobe device! Please check device connections and permissions." 
and problems opening `/dev/ttyACM0` serial port
- The gdb-multiarch, version 12.0.90, had a bug that caused the debugger to throw an assertion whenever the target program paused, resulting in an error in the Debug Console
  ```
  build/gdb-wIRHdd/gdb-12.0.90/gdb/value.c:1731: internal-error: value_copy: Assertion arg->contents != nullptr' failed.
  ``` 
  Solution here: https://forums.raspberrypi.com/viewtopic.php?t=333992#p2045778. I think it's risky to automate this reliably in all situations.
- minicom didn't install
