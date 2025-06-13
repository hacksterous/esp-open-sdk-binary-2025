# esp-open-sdk-binary-2025
This is an amd64 binary of the Open ESP SDK and was created to build a customized MicroPython on
an Ubuntu system targeting an ESP8266 board.
It's a pain everywhere to get the [ESP Open SDK] (https://github.com/pfalcon/esp-open-sdk) compiling.
First, the sources have moved and that repository haven't been updated. Even with all the patches,
I had to manually hack `gcc/reload1.c` to get it to compile.

You will need `libtool`, `python2.7`, `python2-dev` and `python-pip` on your system for to generate
a MicroPython build. I have tested on Ubuntu 22.04 LTS.

Source the file `use-esp8266-build-system` before compiling MicroPython. This script assumes
`esp-open-sdk/`  is created in your home directory.
