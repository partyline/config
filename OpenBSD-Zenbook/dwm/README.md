Settings for the window manager dwm on my [ASUS Zenbook UX305LA](https://www.asus.com/Notebooks/ASUS-ZenBook-UX305LA/specifications/)

## patches

I use only those three patches (© their respective authors)

* [noborder](http://dwm.suckless.org/patches/noborder): removes the border when only one window is visible.
* [attachaside](http://dwm.suckless.org/patches/attachaside): attaches new windows to the right, in the stacking area.
* [pertag](http://dwm.suckless.org/patches/pertag): allows to use a different layout on each workspace.


The `dwm-6.1-attachaside-tagfix.diff` patch had to be fixed to apply without errors, see  `dwm-6.1-attachaside-tagfix-fixed.diff`. For simplicity, the three patches have been combined in `dwm-6.1-combined.diff`.

### How to apply on OpenBSD

```sh
make -C /usr/ports/x11/dwm clean clean=packages
make -C /usr/ports/x11/dwm patch
cp config.h /usr/ports/pobj/dwm-6.1/dwm-6.1/
patch /usr/ports/pobj/dwm-6.1/dwm-6.1/dwm.c dwm-6.1-combined.diff
make -C /usr/ports/x11/dwm rebuild
make -C /usr/ports/x11/dwm reinstall
make patch
```

## config.h

UI preferences (colors). Add a bunch of functions to use/emulate the function keys (set volume and brightness, toggle touchpad) and a shortcut to take a screenshot.

* __fn + f11__: decrease volume
* __fn + f12__: increase volume
* __fn + f10__: mute
* __win + f5__: decrease luminosity
* __win + f6__: increase luminosity
* __win + printscr__: take a screenshot

```
cp config.h /usr/ports/pobj/dwm-6.1/dwm-6.1/
```

## Scripts

Just throw them in your `$HOME/bin`

* `hwinfo`: displays the CPU frequency and temperature, the remaining charge of the battery and fire an alert when battery is almost discharged.
* `luminosity`: uses `xrandr(1)` to modify the screen luminosity. This is a software modification, unfortunately `xbacklight(1)` is not working.
* `toggle-touchpad`: connects/disconnects the touchpad.
* `screenshot`: takes a screenshot and saves it to the specified `Sdir`. Requires `import` from `ImageMagick`.
