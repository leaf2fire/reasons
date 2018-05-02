# Arch Linux GUI using xmonad

[Xorg](https://wiki.archlinux.org/index.php/Xorg)

pacman -S xorg-server xorg-apps

[xinit](https://wiki.archlinux.org/index.php/Xinit)
[xterm](https://wiki.archlinux.org/index.php/Xterm)

pacman -S xorg-xinit xterm

[xmonad](https://wiki.archlinux.org/index.php/Xmonad)

pacman -S xmonad xmonad-contrib

which xmonad
startx /usr/bin/xmonad

[xmonad basics](http://xmonad.org/tour.html)
[xmonad cheatsheet](https://wiki.haskell.org/wikiupload/b/b8/Xmbindings.png)


[Xresources](https://en.wikipedia.org/wiki/X_resources)
[Xresources](https://wiki.archlinux.org/index.php/X_resources)



zsh
[urxvt](https://wiki.archlinux.org/index.php/Rxvt-unicode)
pacman -S urxvt-perls
https://github.com/muennich/urxvt-perls

emacs

[Solarized](http://ethanschoonover.com/solarized)

pacman -S firefox

pacman -S adobe-source-code-pro-fonts


TODO
set zsh
enable copy and paste between and within windows


If source window of copy is closed, copy buffer becomes null.
fixed with remote-clipboard?

default - option-popup, readline, searchable-scrollback, selection, selection-popup


urxvt-eval
urxvt-kuake

List of keybinds.
C-f forward
C-b back
C-n next
C-p prev
C-a front
C-e back
C-M-c copy
C-M-v paste