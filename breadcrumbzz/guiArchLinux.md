# Arch Linux GUI using xmonad

Currently, a simple guide to get a [window manager](https://wiki.archlinux.org/index.php/Window_manager) up and running.



## Install X and xmonad

First install [Xorg](https://wiki.archlinux.org/index.php/Xorg), 
[xinit](https://wiki.archlinux.org/index.php/Xinit), and 
[xterm](https://wiki.archlinux.org/index.php/Xterm). 

```
pacman -S xorg-server xorg-apps xorg-xinit xterm
```

Next install [xmonad](https://wiki.archlinux.org/index.php/Xmonad).

```
pacman -S xmonad xmonad-contrib
```



## Starting and playing with xmonad

Without configuring anything, start xmonad by first identifying its full path 
and running `startx` on it like below.

```
which xmonad
startx /usr/bin/xmonad
```

The screen should be blank. Take the [xmonad tour](http://xmonad.org/tour.html) 
to learn the keybindings.

*Note*: [xmonad keybinds cheatsheet](https://wiki.haskell.org/wikiupload/b/b8/Xmbindings.png)

*Note*: Windowed applications like [firefox](https://www.mozilla.org/en-US/firefox/new/) 
can now be started in xmonad. `pacman -S firefox`.

*Note*: Most errors from `XKEYBOARD` can be ignored when starting a new 
xsession. Deleting `~/.Xauthority` usually clears these errors.



## Other unorganized

* [Xresources](https://en.wikipedia.org/wiki/X_resources)
* [Xresources](https://wiki.archlinux.org/index.php/X_resources)
* emacs
* [Solarized](http://ethanschoonover.com/solarized)
* pacman -S adobe-source-code-pro-fonts


