# ATtiny

This repository contains a set of "cores" which adds support for some members of the Atmel AVR ATtiny family
of microcontrollers to the Arduino IDE.

The following micro controllers are supported:

- ATtiny 25 (8 pin)
- ATtiny 45 (8 pin)
- ATtiny 85 (8 pin)
- ATtiny 24 (14 pin)
- ATtiny 44 (14 pin)
- ATtiny 84 (14 pin)

## Installation and usage on Windows

### For non-USB ATtiny packages

Following the [installation guide](http://hlt.media.mit.edu/?p=1695) to install the core files and follow
[this guide](http://hlt.media.mit.edu/?p=1706) to find out how to build the circuit.

Also check out this video from Make which explains how to setup and use this core.

(http://www.youtube.com/watch?v=30rPt802n1k)

### For the Tiny85 microUSB Board and clones

The above installation instructions mostly apply as well, but you have to use this URL for the Arduino IDE's
additional boards manager URL instead:

(https://github.com/dok-net/attiny/raw/master/package_dok-net_attiny_index.json)

Next, from the 2.04 release of the [micronucleus project](https://github.com/micronucleus/micronucleus/tree/2.04),
download the ZIP archive of the micronucleus release to your local workstation, uncompress it and open the
`windows_driver_installer` folder. Please follow the instructions for Windows USB driver installation given
in the README.md contained therein.

Boards like the Digispark and its many clones come preloaded with a bootloader that allows uploading sketches
via the USB connector that these boards contain.
This bootloader should itself by updated after the initial setup of the host PC, if only because the newer
version preserves significantly more flash RAM for use by the Arduino sketches. Is has to be mentioned that
there is a risk of running into some sort of failure during this process, which would disable your board for
programming via USB until it is successfully reprogrammed via ISP, so please take note that you take this
step at your own risk.

Now, in order to update the bootloader, locate the micronucleus.exe uploader, either in the ZIP archive you
downloaded for the driver installation, on in your local AppData directory where the Arduino IDE stores the
board support packages.
Then, in that same ZIP archive or in [the dok-net attiny project](https://github.com/dok-net/attiny/bin) you
will find ready-made update files. Now, with the Tiny85 microUSB board disconnected, run this from a command
line:

`micronucleus.exe --run upgrade-t85_default`

Next, within 60s of starting the uploader, connect the Tiny85 microUSB board to your PC. You will see the
upload log progress, a success message, then you should give the Tiny85 some time to reprogram itself before
unplugging it, your PC usually gives some sort of indication that the USB device has reset.
Don't remove it from your PC to early, as stated above, failure to reprogram the bootloader correctly will
probably leave the device corrupted and unusable and require reprogramming with an ISP, which voids the
whole point of using the ATtiny on a microUSB board in the first place.
