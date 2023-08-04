Download the folder 'Luci_Keeb' and copy it to /zmk-config/app/boards/shields
This will allow you to build the keyboard with the command from the 'app' directory:
 - west build -b nice_nano -- -DSHIELD=Luci_Keeb_right
 - west build -b nice_nano -- -DSHIELD=Luci_Keeb_left
Instructions: https://zmk.dev/docs/development/build-flash
To change the name of the build directory, each file and reference to Luci_Keeb will need to be changed



To change the Bluetooth Name you can change it here:
 - Luci_Keeb/Kconfig.defconfig: Line 4 'default "Luci_Keeb"'



Look at Luci_Keeb/Luci_Keeb.dtsi to change which pins you are connecting each row to (row-gpios)
Check the 'Luci_Keeb_left.overlay' and 'Luci_Keeb_right.overlay' to set the col-gpios for the sides respectivaly



The .keymap file has a basic setup for your first layer + an additional reset layer to: 
 - &sys_reset = Same as shorting the reset pin to gnd on the nano
 - &bootloader = Puts the nano into the bootloader for flashing
 - (https://zmk.dev/docs/behaviors/reset)
 
 - &bt BT_CLR = Clears the bluetooth connections, usefull to trouble shoot if it wont connect
 - &bt BT_SEL 0 = Select the bluetooth profile '0', can store upto 5 profiles '0,1,2,3,4'
 - (https://zmk.dev/docs/behaviors/bluetooth)

 - &mo LOWER = Momentarly moves to the 'LOWER' layer defined in the keymap
 - (https://zmk.dev/docs/behaviors/layers)



Added Examples of aditional behaviours:
 - &td0 = Calls the 'Tap Dance' behaviour defined above the keymap for double taps
 - (https://zmk.dev/docs/behaviors/tap-dance)

 - &CrlAltDel = Macro to press the 3 keys togeather
 - (https://zmk.dev/docs/behaviors/macros)
