# URxvt

___

### Install and cosmetics

1. Install (debian)

  ```sh 
  sudo apt-get install rxvt-unicode
  ```
  
2. Create ~/.Xresources
```sh
vi ~/.Xresources
```

3. In .Xresources file change font
```
URxvt.font: xft:monospace:size=10
```

4. Then load new config and do it everytime you change it
```sh 
xrdb ~/.Xresources
```

5. Optionally remove the scrollbar
```
URxvt.scrollBar: false
```

6. Default copy command is 
`Ctrl + Alt + c`
and default paste is 
`Shift + Insert`
or 
`Ctrl + Alt + v`

### Useful plugins

1. [Basic plugins you need are here](https://github.com/bookercodes/awesome-urxvt)
2. Default location for plugins
`~/urxvt/ext`
or as it was said in other sources
`/usr/lib/urxvt/perl`
In the case of (Ubuntu 18.04 and i3wm) first option is working fine
3. Copy source url and download it into **ext** folder
```sh
wget https://raw.githubusercontent.com/effigies/urxvt-perl/master/fullscreen
```
4. In _Xresources_ load the plugin
```
URxvt.perl-ext-common: fullscreen
```
and bind key
```
URxvt.keysym.F11: perl:fullscreen:switch
```
5. Tabbedex particular case
[git link](https://github.com/mina86/urxvt-tabbedex)
- install
```
curl https://raw.githubusercontent.com/mina86/urxvt-tabbedex/master/install | sh
```
- test before loading
```
urxvt -pe tabbedex
```
- after testing add it as usual perl plugin
- default keybinding:
| Key | Description |
|-----|-------------|
| Shift + Down | New tab |
| Shift + Up | Rename tab |
| Shift + Left | Go to left tab |
| Shift + Right | Go to right tab |
| Ctrl + Left | Move tab to the left |
| Ctrl + Right | Move tab to the right |
| Ctrl + d | Close tab |

___
## Useful links
- [urxvt tips and tricks](https://wiki.archlinux.org/index.php/Rxvt-unicode/Tips_and_tricks)
- [archwiki perl extensions](https://wiki.archlinux.org/index.php/rxvt-unicode#Perl_extensions)
- [series of articles about urxvt](https://addy-dclxvi.github.io/post/configuring-urxvt/)
___

My urxvt config (21.05.2019)
```
! general
URxvt.font: xft:Hasklug Nerd Font:style=Regular:size=12, xft:DejaVu Sans:pixelsize=10
URxvt.scrollBar: false

!! colorscheme
*foreground: #D7D0C7
*background: #151515

!black
*color0:     #101010
*color8:     #404040
!red
*color1:     #E84F4F
*color9:     #D23D3D
!green
*color2:     #B8D68C
*color10:    #A0CF5D
!yellow
*color3:     #E1AA5D
*color11:    #F39D21
!blue
*color4:     #7DC1CF
*color12:    #4E9FB1
!magenta
*color5:     #9B64FB
*color13:    #8542FF
!cyan
*color6:     #6D878D
*color14:    #42717B
!white
*color7:     #dddddd
*color15:    #dddddd

! plugins
URxvt.perl-ext-common: default,fullscreen,tabbedex,keyboard-select,url-select

! plugin config
URxvt.keyboard-select.clipboard: true
URxvt.url-select.autocopy: true
URxvt.url-select.launcher: /usr/bin/xdg-open

! key bindings
URxvt.keysym.F11: perl:fullscreen:switch
URxvt.keysym.M-Escape: perl:keyboard-select:activate
```
