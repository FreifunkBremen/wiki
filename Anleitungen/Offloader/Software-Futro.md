### Welche SW braucht ein Futro?

Ich installiere gerne ein paar nüzliche Pakete nach, ein Futro hat viel Platz zum Spielen.
Zunächst häufig benötigte Treiber.

~~~
opkg update
opkg install kmod-usb-storage block-mount block-hotplug kmod-fs-ext4 kmod-fs-vfat kmod-nls-cp437 kmod-nls-iso8859-1
opkg install kmod-usb-core kmod-usb2 kmod-usb-hid --force-depends
opkg install kmod-usb-net kmod-usb-net-asix kmod-r8169 kmod-usb-storage kmod-usb-storage-extras blkid swap-utils block-mount --force-depends
opkg install kmod-fs-reiserfs kmod-fs-ext4 kmod-fs-vfat kmod-nls-cp437 kmod-nls-cp850 kmod-nls-cp852 kmod-nls-iso8859-1 kmod-nls-iso8859-15 kmod-scsi-core kmod-fs-ext4 e2fsprogs --force-depends
opkg install usbutil swap-utils  kmod-nls-cp1250 kmod-nls-cp1251 kmod-nls-cp437 kmod-nls-cp775 kmod-nls-cp850 kmod-nls-cp852 kmod-nls-cp866 
opkg install kmod-nls-iso8859-1 kmod-nls-iso8859-13 kmod-nls-iso8859-15 kmod-nls-iso8859-2 kmod-nls-koi8r kmod-nls-utf8 
opkg install kmod-usb-core kmod-usb2 kmod-usb-hid kmod-usb-net kmod-usb-net-asix kmod-usb-net-dm9601-ethernstall 

~~~
Die open aufgeführten Installationspakete sehen wie folgt auf:

~~~
root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg update

Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/base/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_base
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/base/Packages.sig
Signature check passed.
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/luci/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_luci
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/luci/Packages.sig
Signature check passed.
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/packages/Packages.gz
*** Failed to download the package list from http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/packages/Packages.gz

Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/routing/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_routing
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/routing/Packages.sig
Signature check passed.
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/telephony/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_telephony
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/telephony/Packages.sig
Signature check passed.
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/Packages.gz
Updated list of available packages in /var/opkg-lists/modules
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/Packages.sig
Signature check passed.
Collected errors:
 * opkg_download: Failed to download http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/packages/Packages.gz, wget returned 8.
 

root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg install kmod-usb-storage block-mount block-hotplug kmod-fs-ext4 kmod-fs-vfat kmod-nls-cp437 kmod-nls-iso8859-1

Package kmod-usb-storage (4.14.167-1) installed in root is up to date.
Package block-mount (2019-03-28-ff1ded63-5) installed in root is up to date.

Unknown package 'block-hotplug'.
Package kmod-fs-ext4 (4.14.167-1) installed in root is up to date.

Installing kmod-fs-vfat (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-fs-vfat_4.14.167-1_x86_64.ipk

Installing kmod-nls-utf8 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-utf8_4.14.167-1_x86_64.ipk

Package kmod-nls-cp437 (4.14.167-1) installed in root is up to date.
Package kmod-nls-iso8859-1 (4.14.167-1) installed in root is up to date.
Configuring kmod-nls-utf8.
Configuring kmod-fs-vfat.
Collected errors:
 * opkg_install_cmd: Cannot install package block-hotplug.


root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg install kmod-usb-core kmod-usb2 kmod-usb-hid --force-depends

Package kmod-usb-core (4.14.167-1) installed in root is up to date.
Package kmod-usb2 (4.14.167-1) installed in root is up to date.

Installing kmod-usb-hid (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-usb-hid_4.14.167-1_x86_64.ipk

Installing kmod-input-evdev (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-input-evdev_4.14.167-1_x86_64.ipk

Installing kmod-hid (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-hid_4.14.167-1_x86_64.ipk

Installing kmod-hid-generic (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-hid-generic_4.14.167-1_x86_64.ipk
Configuring kmod-input-evdev.
Configuring kmod-hid.
Configuring kmod-hid-generic.
Configuring kmod-usb-hid.

root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg install kmod-usb-net kmod-usb-net-asix kmod-r8169 kmod-usb-storage kmod-usb-storage-extras blkid swap-utilsblock-mount --force-depends

Installing kmod-usb-net (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-usb-net_4.14.167-1_x86_64.ipk

Installing kmod-usb-net-asix (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-usb-net-asix_4.14.167-1_x86_64.ipk

Package kmod-r8169 (4.14.167-1) installed in root is up to date.
Package kmod-usb-storage (4.14.167-1) installed in root is up to date.

Installing kmod-usb-storage-extras (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-usb-storage-extras_4.14.167-1_x86_64.ipk

Installing blkid (2.32-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/base/blkid_2.32-2_x86_64.ipk

Installing swap-utils (2.32-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/x86_64/base/swap-utils_2.32-2_x86_64.ipk

Package block-mount (2019-03-28-ff1ded63-5) installed in root is up to date.
Configuring kmod-usb-net.
Configuring kmod-usb-net-asix.
Configuring swap-utils.
Configuring blkid.
Configuring kmod-usb-storage-extras.

root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg install kmod-fs-reiserfs kmod-fs-ext4 kmod-fs-vfat kmod-nls-cp437 kmod-nls-cp850 kmod-nls-cp852 kmod-nls-iso8859-1 kmod-nls-iso8859-15 kmod-scsi-core kmod-fs-ext4 e2fsprogs --force-depends

Installing kmod-fs-reiserfs (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-fs-reiserfs_4.14.167-1_x86_64.ipk

Package kmod-fs-ext4 (4.14.167-1) installed in root is up to date.
Package kmod-fs-vfat (4.14.167-1) installed in root is up to date.
Package kmod-nls-cp437 (4.14.167-1) installed in root is up to date.

Installing kmod-nls-cp850 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-cp850_4.14.167-1_x86_64.ipk

Installing kmod-nls-cp852 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-cp852_4.14.167-1_x86_64.ipk

Package kmod-nls-iso8859-1 (4.14.167-1) installed in root is up to date.

Installing kmod-nls-iso8859-15 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-iso8859-15_4.14.167-1_x86_64.ipk

Package kmod-scsi-core (4.14.167-1) installed in root is up to date.
Package kmod-fs-ext4 (4.14.167-1) installed in root is up to date.
Package e2fsprogs (1.44.1-2) installed in root is up to date.
Configuring kmod-fs-reiserfs.
Configuring kmod-nls-cp850.
Configuring kmod-nls-cp852.
Configuring kmod-nls-iso8859-15.

root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg install usbutil swap-utilskmod-nls-cp1250 kmod-nls-cp1251 kmod-nls-cp437 kmod-nls-cp775 kmod-nls-cp850 kmod-nls-cp852 kmod-nls-cp866

Unknown package 'usbutil'.
Package swap-utils (2.32-2) installed in root is up to date.

Installing kmod-nls-cp1250 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-cp1250_4.14.167-1_x86_64.ipk

Installing kmod-nls-cp1251 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-cp1251_4.14.167-1_x86_64.ipk

Package kmod-nls-cp437 (4.14.167-1) installed in root is up to date.

Installing kmod-nls-cp775 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-cp775_4.14.167-1_x86_64.ipk

Package kmod-nls-cp850 (4.14.167-1) installed in root is up to date.
Package kmod-nls-cp852 (4.14.167-1) installed in root is up to date.

Installing kmod-nls-cp866 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-cp866_4.14.167-1_x86_64.ipk
Configuring kmod-nls-cp1250.
Configuring kmod-nls-cp1251.
Configuring kmod-nls-cp775.
Configuring kmod-nls-cp866.
Collected errors:
 * opkg_install_cmd: Cannot install package usbutil.

root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg install kmod-nls-iso8859-1 kmod-nls-iso8859-13 kmod-nls-iso8859-15 kmod-nls-iso8859-2 kmod-nls-koi8r kmod-nls-utf8

Package kmod-nls-iso8859-1 (4.14.167-1) installed in root is up to date.

Installing kmod-nls-iso8859-13 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-iso8859-13_4.14.167-1_x86_64.ipk

Package kmod-nls-iso8859-15 (4.14.167-1) installed in root is up to date.

Installing kmod-nls-iso8859-2 (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-iso8859-2_4.14.167-1_x86_64.ipk

Installing kmod-nls-koi8r (4.14.167-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen1/x86/64/kmod-nls-koi8r_4.14.167-1_x86_64.ipk

Package kmod-nls-utf8 (4.14.167-1) installed in root is up to date.
Configuring kmod-nls-iso8859-13.
Configuring kmod-nls-iso8859-2.
Configuring kmod-nls-koi8r.

root@FUTRO-2 S550-2 ffhb-0019997a6f26 Mobil:~# opkg install kmod-usb-core kmod-usb2 kmod-usb-hid kmod-usb-net kmod-usb-net-asix kmod-usb-net-dm9601-ethernstall

Package kmod-usb-core (4.14.167-1) installed in root is up to date.
Package kmod-usb2 (4.14.167-1) installed in root is up to date.
Package kmod-usb-hid (4.14.167-1) installed in root is up to date.
Package kmod-usb-net (4.14.167-1) installed in root is up to date.
Package kmod-usb-net-asix (4.14.167-1) installed in root is up to date.
Unknown package 'kmod-usb-net-dm9601-ethernstall'.
Collected errors:
 * opkg_install_cmd: Cannot install package kmod-usb-net-dm9601-ethernstall.

~~~

Ein paar nützliche Zusatzprogramme

~~~
opkg update
OPKG install htop iperf3 e2fsprogs fdisk
opkg install znc znc-mod-fail2ban znc-mod-flooddetach znc-mod-log znc-mod-webadmin znc-webskin-ice
opkg install openvpn-openssl openvpn-easy-rsa

~~~

