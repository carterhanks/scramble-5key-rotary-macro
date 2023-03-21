# Nullbits Scramble V1 OLED Rotary Encoder 5-Key VIA-Compatible Macro Keypad (Or `ORV` - OLED Rotary VIA - for short)

Finally a Nullbits Scramble macro keyboard build with firmware that supports VIA, OLED, rotary encoder, and maintains 5-key operation within a custom 3D-printable case.

With some configuration in your system on your end, you can simply flash the firmware, load the layout in VIA, and be ready to go. If you're a little bit more savvy, you can use this as a great starting point for configuring your keys and layers to be exactly how you would like them.

Full disclosure: I did use someone else's base keymap.c file, and modified it to have all of the functionality to make this particular build work. I also modified a case that somebody else created for the plain scramble with 6 keys to accept the OLED display. 

# What is Needed:
- QMK Toolbox to flash .hex file firmware to the V1 Scramble (see the Nullbits Scramble Repo if you need help on that process)
- VIA Configurator (https://www.usevia.app should be all that you need)
- Any case (or other method) for mounting and wiring the OLED display remotely
- Little bit of brain work and configuration on your system

# Layout:
- Top row (when USB port is on the left) is configured as `1, 2, and encoder click being 3` in terms of label/key corrilation
- Bottom row (when USB port is on the left) is configured as `4, 5, and 6` in terms of label/key corrilation
- This was created on/for the V1 Scramble - however I have included the `elf` (and `map`) file which I believe should work to do the same thing for the Scramble V2 (however I am not sure on this, so you may want to do some more research to confirm this before you flash/add it to your V2 Scramble).

# OLED Display:
- Displays current layer as well as binds for each of the keys in that layer
- Code in keymap.c file must be configured if you want to change key labels - note that character count matters here. You'll notice that all labels are the same amount of characters. That is your minimum and maximum number of characters (21 characters total IIRC). Once this is done you can compile in your QMK environment and reflash the firmware in QMK Toolbox.
- Note that the OLED display must be wired separately from the board and not soldered directly to it in order to utilize all 5 keys. You could easily leave the display attached to the board and configure the two unused keys as `KC_NO` or blank in the VIA configurator for a 3-key plus encoder layout. You would simply replace the labels in the `keymap.c` file with blank spaces/however you would like to otherwise.

# Rotary Encoder:
- The rotary encoder is set by default to scroll through layer configurations on the Scramble once you flash the firmware. In the `Media` layer, you can toggle the encoder's ability to adjust volume by pressing key 1 (top left when the USB port os on the left). The label of key 1 will switch from `DISABLED` to `ENABLED` once you press it, and the encoder will now function as volume control. Press key 1 again and the opposite will occur. You will now have the ability to scroll between layers once again.
- Key number 3 in VIA config and layer labels refers to depressing the encoder, and yes - depressing the encoder while on the `GAMING` layer mid-assasination on COD will allow you to gracefully rage-quit the game.
- The encoder's rotation functionality must be configured from within the `keymap.c` file.

# Changing Configuration:
- As you may have caught onto by now - all of the key press configurations and macros will be configured in VIA (https://www.usevia.app) and can be loaded in from the Layout JSON file.
- If you want to change layer names and key labels, you will have to do so inside of the `keymap.c` file and then compile based on the QMK firmware docs instructions from within your MSYS/QMK environment. This information is pretty easy/intuitive to find.
- Aside from all of that - you will have to modify the VIA macros with your preferred method of opening apps for things like opening chrome, or playing games like COD, Apex Legends, and Liftoff. I simply am telling it to open the Windows Run window, type in the direct path to the game's location on my computer, and hit enter. You will have to find those exact paths from within the applications properties, and replace the strings inside of VIA with your specific file location in order to make that work. Or you can set shortcut key-binds to the games via a shortcut on your desktop and launch the games that way. Simply right-click the shortcut, select properties, and then look for somewhere within those tabs to add a shortcut. Selet the line and press the single key you would like to bind it with, and you should then see a key command for Control + Alt + `your selected key` populated in the box. Apply your new settings, adjust the macro in VIA, and give it a try.

# The Build:
- If you use the 3d-printed case that I have included in the file, you will have to drill a hole in the end cap in order to accomodate the wires passing through from the PCB out to the OLED.
- The case was a little bit snug top to bottom (when looking at the board with USB on the left) after printing. I lightly sanded down the edges of the PCB and it slid in well. But you could also increase the top to bottom dimention by around 0.5-1mm in your slicer before printing and fix this.
- I also felt that it would be wise to remove a little bit of material from the inside of the case in order to make room for the OLED display wires coming off of the PCB while the PCB was slid into the case. You will see what I mean when you print it. You may be able to get tricky and work around this somehow though also.
- I used some cable sleeve and heat shrink to cover the exposed wires for protection and aesthetic. This is optional. You'll also need some countersunk M3 or similar screws to mount the plate to the end of the case.
- If you print the case yourself, then it should be obvious that suports are required.
- I will likely be making some changes to the case file in order to fix the tolerences, add a hole to the end door, and add an option that won't need supports here in the near future as well. I will upload it here and adjust these instructions once I do so.
- Be sure to mark/follow your OLED wires precisely so that you get your connections are correct from the PCB to the display. I used some blue painters tape and a sharpee to keep them straight.

# Enjoy!

Be sure to add your builds to the Scramble section or Build Chat of the Nullbits discord if you utilize any part of this! I would love to see it.
