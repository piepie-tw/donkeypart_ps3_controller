The code for this part was copied from [Tawn Kramer's](https://github.com/tawnkramer/donkey) fork of donkeycar.

# PS3/PS4/XBox One Joystick Controller

The default web controller may be replaced with a one line change to use a physical joystick part for input. This uses
the OS device /dev/input/js0 by default. In theory, any joystick device that the OS mounts like this can be used. In
practice, the behavior will change depending on the model of joystick ( Sony, or knockoff ), or XBox controller
and the Bluetooth driver used to support it. The default code has been written and tested with
 a [Sony brand PS3 Sixaxis controller](https://www.amazon.com/Dualshock-Wireless-Controller-Charcoal-playstation-3).
 Other controllers may work, but will require alternative Bluetooth installs, and tweaks to the software for correct
 axis and buttons.

## Install donkeycar & overwrite Joystick

1. Connect your bluetooth controller to the raspberry pi. See the Bluetooth section below.
```bash
cd ~
git clone https://github.com/piepie-tw/donkeypart_ps3_controller/

cd ~
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout 1b548b9
sed -i "s/'tensorflow @/#'tensorflow @/g" setup.py

cp ~/controller.py ~/donkeycar/donkeycar/parts/controller.py

time pip3 install -e .[pi]
```
