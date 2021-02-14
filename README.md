# Hackintosh Laptop
# Xiaomi Mi Notebook Pro 2020 Enhanced

Quick reference guide to get hackintoshing on the Xiaomi Mi Notebook Pro 2020 Enhanced working.

1. Go through Dortania Guide to get an idea what you're getting yourself into
    (https://dortania.github.io/getting-started/)

2. Prepare your USB by following the Dortania guide

3. Go to the amazing github repo of Daliansky to grab the necessary EFI files.
    (https://github.com/daliansky/XiaoMi-Pro-Hackintosh)
   The repo also contains files for previos models of the Xiaomi Mi Notebook Pro.
   Choose the appropriate model and follow his guide.

3. Check your EFI folder and set your Serial Number etc.
   - Do not forget to check the appropriate kext for AirportItlwm > Catalina or Big Sur  (Or use Itlwm with Heliport)
   - Enable or Disable the unused kext as required in the config.plist.
   - Set your Serial Number and info in the config.plist.

4. Go through the guides in 1 and 2 again and see if you missed anything.

5. Reboot your system and press F2 to go to Bios.
    On the First tab, go to the last line and change the setting to change to English from Chinese
    Go to the security tab and set a supervisor password > needed to disable secure boot
    Go to the boot tab and enable boot from USB
    Save your settings and reboot.
    
6. Plug in your USB and boot. Press F12 and select the USB to boot from.
    This should bring you to the macOS setup.
    Follow Dortania guide to install macOS

7. Once you're able to boot into macOS, mount the EFI partition of the mac drive using https://github.com/corpnewt/MountEFI

8. Copy the EFI partition from your USB to the EFI partition you just mounted

9. Eject the USB and reboot.

10. Head back to Bios using F2 and change the boot order by bringing the "Opencore" bootloader to the top of the list. Save and reboot
 
11. If you boot back into macOS, congratulations!


# Disabling CFG_Lock

Be careful! any mistake here may brick your device! No one else is responsible if you do so!

1. Follow Dortania's guide to get the offset value

2. Get RU.efi from https://ruexe.blogspot.com/ (This version worked for me: RU 5.25.0379 Beta)

3. Go to Bios and disable secure boot & remove bios password

4. Follow this thread to make bootable usb and unlock CFG Lock:
    https://www.reddit.com/r/hackintosh/comments/hz2rtm/cfg_lockunlocking_alternative_method/

    - Format usb as FAT32 or FAT with MBR (Master Boot Record)
    - Rename "ru.efi" to "bootx64.efi" and copy it to the usb into: <USB>/EFI/BOOT/bootx64.efi
    - Reboot and select the USB after pressing F12 at boot.
    - Press enter to close the welcome screen
    - Press: "ALT" + "="
    - Search the List and find CUPSetup and press enter
    - Using the offset value found in 1, go to that registry > follow row first, then column
    - Confirm this is the correct value and press 0 to remove the lock.
    - Press Enter to confirm
    - Press: "Ctrl" + "W" to save
    - Press: "ALT" + "Q" to quit
 
 5. Reboot into your Opencore and press space to VerifyMsrE2

This is just a quick guide to point you in the right direction! Researching the other resources are more fun and satisfying.
