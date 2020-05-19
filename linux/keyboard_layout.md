# Keboard layout

1. Which key is pressed

   ```bash
   xev
   ```

2. Create .Xmodmap in home directory

   ```bash
   vi ~/.Xmodmap
   ```

3. Add this to swap left alt and left control

   ```text
   clear control
   clear mod1
   keycode 37 = Alt_L Meta_L
   keycode 64 = Control_L
   add control = Control_L Control_R
   add mod1 = Alt_L Meta_L
   ```

4. And this to swap escape and caps lock

   ```text
   remove Lock = Caps_Lock
   keysym Escape = Caps_Lock
   keysym Caps_Lock = Escape
   add Lock = Caps_Lock
   ```

5. To have the settings take immediate effect run the following command

   ```text
   xmodmap ~/.Xmodmap
   ```

