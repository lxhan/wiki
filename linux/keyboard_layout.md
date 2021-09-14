## Which key is pressed

```sh
xev
```

## Create .Xmodmap in home directory

```sh
vi ~/.Xmodmap
```

## Add this to swap left alt and left control

```sh
clear control
clear mod1
keycode 37 = Alt_L Meta_L
keycode 64 = Control_L
add control = Control_L Control_R
add mod1 = Alt_L Meta_L
```

## And this to swap escape and caps lock

```sh
remove Lock = Caps_Lock
keysym Escape = Caps_Lock
keysym Caps_Lock = Escape
add Lock = Caps_Lock
```

## To have the settings take immediate effect run the following command

```sh
xmodmap ~/.Xmodmap
```

