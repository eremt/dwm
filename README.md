# dwm
This is my build of [dwm](https://dwm.suckless.org/).


## Requirements
In order to build dwm you need the Xlib header files.

Debian:
```
apt install xorg build-essential libx11-dev libxft-dev libxinerama-dev
```
Arch:
```
pacman -S xorg xorg-xinit base-devel libx11 libxft libxinerama
```

## Installation
Edit config.mk to match your local setup (dwm is installed into the `/usr/local` namespace by default).

Afterwards enter the following command to build and install dwm (if necessary as root):
```
make clean install
```

## Running dwm
Add the following line to your `~/.xinitrc` to start dwm using startx:
```
exec dwm
```
In order to display status info in the bar, you can do something like this in your `~/.xinitrc`:
```
while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
do
  sleep 1
done &
exec dwm
```
