# Ly - a TUI display manager (for Void Linux)
[![CodeFactor](https://www.codefactor.io/repository/github/cylgom/ly/badge/master)](https://www.codefactor.io/repository/github/cylgom/ly/overview/master)
![Ly screenshot](https://user-images.githubusercontent.com/5473047/42466218-8cb53d3c-83ae-11e8-8e53-bae3669f959c.png "Ly screenshot")

Ly is a lightweight TUI (ncurses-like) display manager for Linux and BSD.

## Patches added in fork
- runit service instead of systemd one by @qub1750ul
- it language patch by @termgod
- made some very minor change so that it actually works on void

## Errors
- Shutdown and Reboot doesn't work. If someone would be kind enough to help me then I would really appreciate it. Thanks.

## Dependencies
 - a C99 compiler (tested with tcc and gcc)
 - a C standard library
 - make
 - pam
 - pam-devel
 - libxcb
 - xorg
 - xorg-xauth
 - mcookie
 - tput
 - shutdown

## Support
The following desktop environments were tested with success
 - budgie
 - cinnamon
 - deepin
 - enlightenment
 - gnome
 - i3
 - kde
 - lxde
 - lxqt
 - mate
 - sway
 - xfce
 - pantheon

Ly should work with any X desktop environment, and provides
basic wayland support (sway works very well, for example).

## systemd?
Unlike what you may have heard, Ly does not require `systemd`,
and was even specifically designed not to depend on `logind`.
You should be able to make it work easily with a better init,
changing the source code won't be necessary :)

## Cloning and Compiling
Clone the repository
```
git clone https://github.com/raaron773/ly-void.git
```

Fetch submodules
```
make github
```

Compile
```
make
```

Test in the configured tty (tty2 by default)
or a terminal emulator (but desktop environments won't start)
```
sudo make run
```

Install Ly and the provided systemd service file
Then, install Ly and the runit service file
```
sudo make install
```

Now enable the runit service to make it spawn on startup
```
sudo ln -s /etc/sv/ly-runit-service /var/service/
```

You can disable getty-tty2
```
sudo rm /var/service/agetty-tty2
```

## Configuration
You can find all the configuration in `/etc/ly/config.ini`.
The file is commented, and includes the default values.

## Controls
Use the up and down arrow keys to change the current field, and the
left and right arrow keys to change the target desktop environment
while on the desktop field (above the login field).

## Tips
The numlock and capslock state is printed in the top-right corner.
Use the F1 and F2 keys to respectively shutdown and reboot.
Take a look at your .xsession if X doesn't start, as it can interfere
(this file is launched with X to configure the display properly).

## PSX DOOM fire animation
To enable the famous PSX DOOM fire described by [Fabien Sanglard](http://fabiensanglard.net/doom_fire_psx/index.html),
just uncomment `animate = true` in `/etc/ly/config.ini`. You may also
disable the main box borders with `hide_borders = true`.

## Additional Information
The name "Ly" is a tribute to the fairy from the game Rayman.
Ly was tested by oxodao, who is some seriously awesome dude.
