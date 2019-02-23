# Asus USB-AC54
<img src="https://cdn.rawgit.com/TobiasVanDyk/Netgear-A6210/master/asusac54.jpg" width="300" height="300" />

The <b><a href="https://www.asus.com/Networking/USB-AC54/">ASUS USB-AC54</a></b> is a dual-band 802.11ac Wi-Fi adapter with a USB 3.0 connection that brings high-performance wireless networking support to desktop and notebook PCs. The USB-AC54 features a USB 3.0 connection with support for wireless data rates up to 400 Mbps at 2.4 GHz and 867 Mbps at 5 GHz with compatible routers. Suitable for use with both desktop and notebook PCs, the USB-AC55 features a dual internal antenna design for great wireless network coverage with minimal desktop clutter.
### Features
* 5th generation 802.11ac chipset gives you dual-band 2.4 GHz / 5 GHz for up to super-fast 867 Mbps
* 256QAM technology increases wireless-N data rate from 300 Mbps to 400 Mbps for 33% faster performance
* Selectable 5 GHz /2 .4 GHz dual bands increase signal clarity for better HD multimedia
* USB 3.0 connection for high-performance wireless networking with desktop and notebook PCs

### General
This driver supports Ralink / Mediatek mt766u, mt7632u and mt7612u chipsets.

In particular, the driver supports several USB dongles such as Netgear-A6210,
ASUS USB-AC54, ASUS USB-AC55, ASUS USB-N53 and EDUP EP-AC1601. 

<b> Linux kernel version up to 4.15 (as used in Mint 19.1) has been tested. </b>

<i> Note that I did use ukuu to install Linux kernels 4.19 and 4.20 in Mint 19.1, which has support for the Mediatek MT76* devices. The Asus AC54 did not work with these kernels.</i>

The supported chipsets can be present in other devices. To include additional 
devices, you need to add corresponding VendorID, DeviceID into the file 
"rtusb_dev_id.c"

### {USB_DEVICE(0x0B05, 0x1833), .driver_info = RLT_MAC_BASE}, /* ASUS USB-AC54 */ 

yields a working Asus USB-AC54 WiFi in Linux Mint 19.1

To compile and install the driver follow the steps below but also note the comments here:

https://forum.level1techs.com/t/solved-netgear-6210-wifi-adapter-not-installing/132183/22

It needs a sudo service network-manager restart

to connect

### To install in Mint 19.1:
    $ sudo apt-get install git build-essential linux-headers-generic
    $ sudo apt-get install make gcc libelf-dev
    $ git clone -b port-to-4.15 https://github.com/kaduke/Netgear-A6210
    $ cd Netgear-A6210

Now replace the rtusb_dev_id.c in the common folder with the file in this archive
        $ make
        $ sudo make install
        $ sudo reboot

After reboot:
        $ sudo service network-manager restart

### dmesg gives:

[   51.552023] -->RTUSBVendorReset

[   51.571905] <--RTUSBVendorReset

[   51.572539] .

[   51.577846] .

[   51.583154] .

[   51.588462] .

[   51.593770] .

[   51.599077] .

[   51.604390] .

[   51.609697] .

[   51.615005] .

[   51.620320] .

[   51.625628] .

[   51.635633] andes_usb_chk_crc

[   51.657138] andes_usb_reset_wmt

[   51.677730] -->RTUSBVendorReset

[   51.697686] <--RTUSBVendorReset

[   51.698009] fw version:0.0.00 

[   51.698009] build:1

[   51.698009] build time:

[   51.698010] 2

[   51.698010] 0

[   51.698010] 1

[   51.698011] 4

[   51.698011] 0

[   51.698011] 6

[   51.698011] 2

[   51.698012] 4

[   51.698012] 1

[   51.698012] 8

[   51.698012] 3

[   51.698013] 0

[   51.698013] _

[   51.698013] _

[   51.698013] _

[   51.698014] _

[   51.698014] fw for E3 IC

[   51.698015] ilm length = 59312(bytes)

[   51.698015] dlm length = 32068(bytes)

[   51.698209] loading fw

[   51.698542] .

[   51.703986] .

[   51.709430] .

[   51.715281] .

[   51.721593] .

[   51.727852] .

[   51.734108] .

[   51.740233] .

[   51.761720] cfg_mode=5

[   51.761805] Key1Str is Invalid key length(0) or Type(0)

[   51.761811] Key2Str is Invalid key length(0) or Type(0)

[   51.761818] Key3Str is Invalid key length(0) or Type(0)

[   51.761824] Key4Str is Invalid key length(0) or Type(0)

[   51.761976] USBAggregation = 1

[   51.761977] 1. Phy Mode = 31

[   51.761978] NVM is Efuse and its size =1d[1e0-1fc] 

[   51.771284] get_chl_grp:illegal channel (167)

[   51.771284] get_chl_grp:illegal channel (167)

[   51.771285] get_chl_grp:illegal channel (169)

[   51.771285] get_chl_grp:illegal channel (169)

[   51.771286] get_chl_grp:illegal channel (171)

[   51.771286] get_chl_grp:illegal channel (171)

[   51.771286] get_chl_grp:illegal channel (173)

[   51.771287] get_chl_grp:illegal channel (173)

[   51.772094] Country Region from e2p = 11e

[   51.776133] mt76x2_get_external_lna_gain::LNA type=0x11, BLNAGain=0x0, ALNAGain0=0xffffff84, ALNAGain1=0xffffff84, ALNAGain2=0xffffff84

[   51.776133] 2. Phy Mode = 31

[   51.776134] 3. Phy Mode = 31

[   51.776218] andes_usb_fw_init

[   51.836149] AntCfgInit: primary/secondary ant 0/1

[   51.836150] andes_load_cr:cr_type(2)

[   51.836660] ChipStructAssign(): MT76x2 hook !

[   51.836662] ---> InitFrequencyCalibration

[   51.836663] InitFrequencyCalibrationMode:Unknow mode = 3

[   51.836664] InitFrequencyCalibration: frequency offset in the EEPROM = 177

[   51.836664] <--- InitFrequencyCalibration

[   51.836671] RTMPSetPhyMode: channel is out of range, use first channel=1 

[   51.836672] RTMPSetPhyMode: Update for STA

[   51.837994] MCS Set = ff ff 00 00 01

[   51.838043] 80211> re-init bands...

[   51.838044] 80211> CurTxPower = 20 dBm

[   51.838045] ====> Radar Channel 52

[   51.838046] ====> Radar Channel 54

[   51.838046] ====> Radar Channel 56

[   51.838047] ====> Radar Channel 60

[   51.838048] ====> Radar Channel 62

[   51.838048] ====> Radar Channel 64

[   51.838049] ====> Radar Channel 100

[   51.838050] ====> Radar Channel 104

[   51.838051] 80211> TxStream = 2

[   51.838056] Chan 167 (frq 5835):	not allowed!

[   51.838057] Chan 169 (frq 5845):	not allowed!

[   51.838058] Chan 171 (frq 5855):	not allowed!

[   51.838059] Chan 173 (frq 5865):	not allowed!

[   51.838060] Chan 184 (frq 4920):	not allowed!

[   51.838061] Chan 188 (frq 4940):	not allowed!

[   51.838062] Chan 192 (frq 4960):	not allowed!

[   51.838062] Chan 196 (frq 4980):	not allowed!

[   51.838063] Chan 208 (frq 6040):	not allowed!

[   51.838064] Chan 212 (frq 6060):	not allowed!

[   51.838065] Chan 216 (frq 6080):	not allowed!

[   51.838066] RTMPDrvOpen(1):Check if PDMA is idle!

[   51.838108] RTMPDrvOpen(2):Check if PDMA is idle!

[   51.880116] 80211> CFG80211_OpsPmksaFlush ==>

[   51.899876] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   51.953623] TX0 power compensation = 0x38

[   51.954058] TX1 power compensation = 0x38

[   59.031194] 80211> Connect bssid 7c:8b:ca:df:29:40

[   59.085888] PeerBeaconAtJoinAction(): HT-CtrlChannel=11, CentralChannel=>9

[   59.085889] PeerBeaconAtJoinAction(): Set CentralChannel=9

[   59.085890] AdjustChannelRelatedValue(): Input BW=1, rf_channel=9, vht_bw=1, Channel=11, vht_cent_ch=9!

[   59.155668] mt76x2_reinit_agc_gain:original agc_vga0 = 0x5c, agc_vga1 = 0x5c

[   59.155669] mt76x2_reinit_agc_gain:updated agc_vga0 = 0x5c, agc_vga1 = 0x5c

[   59.155827] mt76x2_reinit_hi_lna_gain:original hi_lna0 = 0x27, hi_lna1 = 0x27

[   59.155827] mt76x2_reinit_hi_lna_gain:updated hi_lna0 = 0x27, hi_lna1 = 0x27

[   59.155948] original vga value(chain0) = 5c

[   59.155988] original vga value(chain1) = 5c

[   59.156176] mt76x2_calibration(channel = 9)

[   60.257740] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[   60.289492] Rcv Wcid(1) AddBAReq

[   60.289494] Start Seq = 00000003

[   70.935826] RTMP_TimerListRelease: release timer obj ffffa65cc3f14cb8!

[   70.940034] 80211> KeyDel STA(7C:8B:CA:DF:29:40) ==>

[   70.940035] 80211> STA Key Del -- DISCONNECT

[  141.452703] 80211> Connect bssid 24:00:ba:fb:d6:70

[  141.548800] PeerBeaconAtJoinAction(): HT-CtrlChannel=100, CentralChannel=>100

[  141.548803] PeerBeaconAtJoinAction(): Set CentralChannel=100

[  141.548808] AdjustChannelRelatedValue(): Input BW=0, rf_channel=100, vht_bw=1, Channel=100, vht_cent_ch=100!

[  141.616773] mt76x2_reinit_agc_gain:original agc_vga0 = 0x54, agc_vga1 = 0x54

[  141.616776] mt76x2_reinit_agc_gain:updated agc_vga0 = 0x54, agc_vga1 = 0x54

[  141.616952] mt76x2_reinit_hi_lna_gain:original hi_lna0 = 0x2c, hi_lna1 = 0x2c

[  141.616954] mt76x2_reinit_hi_lna_gain:updated hi_lna0 = 0x2c, hi_lna1 = 0x2c

[  141.617083] original vga value(chain0) = 54

[  141.617129] original vga value(chain1) = 54

[  141.617309] mt76x2_calibration(channel = 100)

[  142.911941] Rcv Wcid(1) AddBAReq

[  142.911945] Start Seq = 00000000

[  145.990734] Rcv Wcid(1) AddBAReq

[  145.990737] Start Seq = 00000000

tobias@Mint-Skylake:~$ 


