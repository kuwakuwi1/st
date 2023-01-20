# st - simple terminal

st is a simple terminal emulator for X which sucks less. Way better than xterm or urxvt, and more lightweight.
6 times more lightweight than alacritty, and yet already support ligatures and many more.

<details>
  <summary>Screenshots</summary>

  *st with fish shell:*

  [![st with fish shell](https://i.postimg.cc/7hr3bbcB/Screenshot-2023-01-20-07-42-09.png)](https://postimg.cc/qhQh5Bpn)

  *neovim(astronvim) on st with font ligatures:*
  [![Screenshot-2023-01-20-06-57-45.png](https://i.postimg.cc/fR94XrgJ/Screenshot-2023-01-20-06-57-45.png)](https://postimg.cc/HrdP1Bmg)

</details>

<br />

### Available patches / features

* [Alpha](https://st.suckless.org/patches/alpha/) : This patch allows users to change the opacity of the background. Note that you need an X composite manager (e.g. compton, xcompmgr) to make this patch effective.
* [Scrollback](https://st.suckless.org/patches/scrollback/) : Enables us to scroll up in terminal using Shift + [PageUp, PageDown] or (in this repo) using Scrollwheel or touchpad.
* [Font Ligatures](https://st.suckless.org/patches/ligatures/) : Add support for font ligatures in our terminal.
* [Clipboard](https://st.suckless.org/patches/clipboard/) : This trivial patch sets CLIPBOARD on selection.
* [font2](https://st.suckless.org/patches/font2/) : This patch allows to add spare font besides default.
* [Desktop Entry](https://st.suckless.org/patches/desktopentry/) : This enables to find st in a graphical menu and to display it with a nice icon

## Requirements

In order to build st you need the Xlib header files.
in Ubuntu, it's already shipped by default, but just to make sure, run:
```
sudo apt install libx11-dev
```

## Installation

Edit config.mk to match your local setup (st is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install st (if
necessary as root):

```bash
sudo make clean install
```

## Running st

Run `st` from terminal or search st from start menu.

If you did not install st with make clean install, you must compile
the st terminfo entry with the following command:

```bash
tic -sx st.info
```

See the man page for additional details.

### Keyboard Shortcut
Action      | Key Combination
---         | ---
Copy        | `ctrl` + `shift` + `c`
Paste       | `ctrl` + `shift` + `v`
Zoom In     | `ctrl` + `shift` + `PageUp`
Zoom Out    | `ctrl` + `shift` + `PageDown`
Reset Zoom  | `ctrl` + `shift` + `Home`

### Colorscheme patch
The colorscheme patch is a custom patch, it is not the ones from [colorscheme](https://st.suckless.org/patches/colorschemes/)
It is `solarized.dark` exported from https://terminal.sexy with a different bg and fg color.
Also the `defaultfg`, `defaultbg` and `defaultcs` are not `static`s, otherwise it won't compile.

### Previous available patches

* [Fix Keyboard Input](https://st.suckless.org/patches/fix_keyboard_input/) : Add a few previously undefined keys.
Removed as this was used for additional keys for zooming.

## Modification
If you want to edit the config, then edit the config.mk or config.def.h (not the config.h, because it's automatically generated when compiling (make install command) 

### Adding Patches from suckless.org
Applying patches from https://st.suckless.org/patches/ use:
```
# download the patch and place it in patches folder
curl -O --output-dir patches https://st.suckless.org/patches/<name-of-patch>.diff
# Add custom patch
patch -Np1 -i patches/<name-of-patch>.diff
or
patch < <name-of-patch>.diff
```

## Credits

* Forked from [Shorai/st](https://github.com/Shourai/st)
* Original st website [https://st.suckless.org/](https://st.suckless.org/)
* Based on Aurélien APTEL aurelien.aptel@gmail.com bt source code.
