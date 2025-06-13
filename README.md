# ESP open SDK Binary
This is an amd64 binary of the Open ESP SDK and was created to build a customized MicroPython on
an Ubuntu system targeting an ESP8266 board.
It's a pain everywhere to get the [ESP Open SDK] (https://github.com/pfalcon/esp-open-sdk) compiling.
First, the sources have moved and that repository haven't been updated. Even with all the patches,
I had to manually hack `gcc/reload1.c` to get it to compile.

You will need `libtool`, `python2.7`, `python2-dev` and `python-pip` on your system for to generate
a MicroPython build. I have tested on Ubuntu 22.04 LTS.

Source the file `use-esp8266-build-system` before compiling MicroPython. This script assumes
`esp-open-sdk/`  is created in your home directory.

# Uploading a sketch to the board.
Do not use the esptool that comes with the SDK, instead the esptool package for Python3.

```
$ sudo pip3 install pyserial
$ sudo pip3 install setuptools wheel pyaes esptool
```

This will install the script `esptool.py' at /usr/local/bin/.

To upload, run: 

`$ /usr/local/bin/esptool.py --port /dev/ttyUSB0 write_flash --flash_size=detect -fm dio 0x00000 build-ESP8266_GENERIC/firmware.bin`

```
ect -fm dio 0x00000 build-ESP8266_GENERIC/firmware.bin 
esptool.py v4.8.1
Serial port /dev/ttyUSB0
Connecting....
Detecting chip type... Unsupported detection protocol, switching and trying again...
Connecting....
Detecting chip type... ESP8266
Chip is ESP8266EX
Features: WiFi
Crystal is 26MHz
MAC: 18:fe:34:cf:86:18
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Auto-detected Flash size: 4MB
Flash will be erased from 0x00000000 to 0x0009cfff...
Flash params set to 0x0240
Compressed 639916 bytes to 428427...
Wrote 639916 bytes (428427 compressed) at 0x00000000 in 37.7 seconds (effective 135.7 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...```
