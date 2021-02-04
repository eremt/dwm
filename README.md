# dwm
This is my build of suckless [dwm](https://dwm.suckless.org). You might also be interested in my builds of [st](https://github.com/eremt/st) and [dmenu](https://github.com/eremt/dmenu).

Patches added:
- [attachaside](http://dwm.suckless.org/patches/attachaside/)

Other than the patches I've added some keybindings:
```bash
# config.def.h
#define MODKEY Mod4Mask

static Key keys[] = {
  /* modifier         key   function    argument */
  { MODKEY|ShiftMask, XK_w, killclient, {0} }, // MOD + SHIFT + W to kill window
};
```

## Requirements
Install the dependencies:

**Debian/Ubuntu**
```bash
sudo apt install xorg build-essential libx11-dev libxft-dev libxinerama-dev
```
**Arch**
```bash
sudo pacman -S xorg xorg-xinit base-devel libx11 libxft libxinerama
```

## Installation
Create a `~/.suckless` directory and clone this repository. Then build and install `dwm`:
```bash
mkdir -p ~/.suckless && \
git clone https://github.com/eremt/dwm ~/.suckless/dwm && \
cd ~/.suckless/dwm && sudo make clean install
```
Clone, build and install `st` and `dmenu`:
```bash
git clone https://github.com/eremt/st ~/.suckless/st && \
cd ~/.suckless/st && sudo make clean install && \
git clone https://github.com/eremt/dmenu ~/.suckless/dmenu && \
cd ~/.suckless/dmenu && sudo make clean install
```

## Running dwm
To start dwm on login add the following lines to your `~/.xinitrc`:
```bash
# ~/.xinitrc
# display status info in the bar
while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
do
  sleep 1
done &
# start dwm
exec dwm
```
and the following to `~/.zprofile`:
```bash
# ~/.zprofile
# startx on login
if [ -z "${DISPLAY}" ] && [ "${XDG_VTNR}" -eq 1 ]; then
  exec startx
fi
```
