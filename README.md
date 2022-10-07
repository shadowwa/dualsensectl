# DualSense Control
- _Latest version 0.3_

Linux tool for controlling Sony PlayStation 5 DualSense controller.

    Usage: dualsensectl [options] command [ARGS]

    Options:
      -l                                       List available devices
      -d DEVICE                                Specify which device to use
      -h --help                                Show this help message
      -v --version                             Show version
    Commands:
      power-off                                Turn off the controller (BT only)
      battery                                  Get the controller battery level
      lightbar STATE                           Enable (on) or disable (off) lightbar
      lightbar RED GREEN BLUE [BRIGHTNESS]     Set lightbar color and brightness (0-255)
      player-leds NUMBER                       Set player LEDs (1-5) or disabled (0)
      microphone STATE                         Enable (on) or disable (off) microphone
      microphone-led STATE                     Enable (on) or disable (off) microphone LED


### Building (gcc)

    ./
    ~ sudo make && sudo make install

### Download sources:
Arch Linux - AUR: [dualsensectl] (https://aur.archlinux.org/packages/dualsensectl)
Arch Linux - AUR: [dualsensectl-git] (https://aur.archlinux.org/packages/dualsensectl-git/) -- GIT version
Debian/Ubuntu - DEB: [dualsensectl] ---
openSUSE - RPM: [dualsensectl] (https://software.opensuse.org/download/package?package=dualsensectl&project=hardware)
Fedora - RPM: [dualsensectl] (https://copr.fedorainfracloud.org/coprs/birkch/dualsensectl/)
Mageia - RPM: ---

### Dependencies

## GENERIC (Gcc/PkgConf)
* gcc
* dbus-1
* hidapi-hidraw

## Arch Linux
* gcc
* dbus
* hidapi

## Debian/Ubuntu
* gcc
* dbus
* libdbus-1-3
* libdbus-1-dev
* libhidapi-hidraw0

## openSUSE
* gcc
* gcc-c++
* dbus-1
* dbus-1-devel
* libhidapi-devel
* libhidapi-hidraw0

## Fedora
* gcc
* gcc-c++
* dbus
* dbus-devel
* hidapi
* hidapi-devel

## Mageia
* gcc 
* gcc-c++
* dbus
* lib64dbus-devel
*  lib64hidapi-devel 
* lib64hidapi0 

### udev rules (Optional)
- _No longer neccessary to set manually_ . . .

Also installed by Steam, so you may already have it configured. If not, create `/etc/udev/rules.d/70-dualsensectl.rules`:

    # PS5 DualSense controller over USB hidraw
    KERNEL=="hidraw*", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0ce6", MODE="0660", TAG+="uaccess"

    # PS5 DualSense controller over bluetooth hidraw
    KERNEL=="hidraw*", KERNELS=="*054C:0CE6*", MODE="0660", TAG+="uaccess"
