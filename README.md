# Usus USB-AC54
This driver supports Ralink / Mediatek mt766u, mt7632u and mt7612u chipsets.

In particular, the driver supports several USB dongles such as Netgear-A6210,
ASUS USB-AC54, ASUS USB-AC55, ASUS USB-N53 and EDUP EP-AC1601. 

Linux kernel version up to 4.15 (as used in Mint 19.1) has been tested.

To build the driver, follow these steps:

    $ git clone https://github.com/kaduke/Netgear-A6210
    $ cd Netgear-A6210
    $ make
    $ sudo make install


The supported chipsets can be present in other devices. To include additional 
devices, you need to add corresponding VendorID, DeviceID into the file 
"rtusb_dev_id.c"

{USB_DEVICE(0x0B05, 0x1833), .driver_info = RLT_MAC_BASE}, /* ASUS USB-AC54 */

yields a working WiFi in Mint 19.1

but note the comments here:
https://forum.level1techs.com/t/solved-netgear-6210-wifi-adapter-not-installing/132183/22


