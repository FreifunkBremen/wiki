### Wie kann ein USB Stick am Router als Laufwerk verwendet werden?
Erstellt am: 08.08.2021

Nun, das ist ganz einfach, folgende 3 Schritte sind notwendig.
## Inhalt
[[_TOC_]]

Das Vorgehen ist an die OpenWRT Anleitung angelehnt.

[https://openwrt.org/docs/guide-user/storage/usb-drives-quickstart](https://openwrt.org/docs/guide-user/storage/usb-drives-quickstart)

[https://openwrt.org/docs/guide-user/storage/usb-installing](https://openwrt.org/docs/guide-user/storage/usb-installing)

Es wird ein vorbereiteter USB Stick benötig ( Hier wurde eine Samsung USB 3.1 mit 65Gb verwendet)
Zugang zum Router via SSH-Konsole. Verwendeter Router TP-Link Archer C7 mit zwei USB Buchsen (USB1, USB2).
Der USB Stick wird in USB1 gesteckt, zwischen den USB Buchsen sind zwei LED, wovon dann die untere Leuchtet, der Stick ist nun elektrisch mit dem Router verbunden.

### 1.) USB Treiber nachinstallieren
Im ersten Schritt die Treiber installieren, damit der Stick erkannt wird. 

**_`Eingabe:`_**
~~~
opkg update && opkg install block-mount e2fsprogs kmod-fs-ext4 kmod-usb-storage kmod-usb2 kmod-usb3
~~~
**_`Ausgabe:`_**
~~~
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_base
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/Packages.sig
Signature check passed.
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/luci/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_luci
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/luci/Packages.sig
Signature check passed.
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/packages/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_packages
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/packages/Packages.sig
Signature check passed.
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/routing/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_routing
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/routing/Packages.sig
Signature check passed.
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/telephony/Packages.gz
Updated list of available packages in /var/opkg-lists/openwrt_telephony
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/telephony/Packages.sig
Signature check passed.
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen4/ar71xx/generic/Packages.gz
Updated list of available packages in /var/opkg-lists/modules
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen4/ar71xx/generic/Packages.sig
Signature check passed.

Installing block-mount (2019-03-28-ff1ded63-5) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen4/ar71xx/generic/block-mount_2019-03-28-ff1ded63-5_mips_24kc.ipk
Installing e2fsprogs (1.44.1-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/e2fsprogs_1.44.1-2_mips_24kc.ipk
Installing libuuid (2.32-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/libuuid_2.32-2_mips_24kc.ipk
Installing libblkid (2.32-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/libblkid_2.32-2_mips_24kc.ipk
Installing libcomerr (1.44.1-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/libcomerr_1.44.1-2_mips_24kc.ipk
Installing libss (1.44.1-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/libss_1.44.1-2_mips_24kc.ipk
Installing libext2fs (1.44.1-2) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/libext2fs_1.44.1-2_mips_24kc.ipk
Installing kmod-fs-ext4 (4.9.211-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen4/ar71xx/generic/kmod-fs-ext4_4.9.211-1_mips_24kc.ipk
Installing kmod-usb-storage (4.9.211-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen4/ar71xx/generic/kmod-usb-storage_4.9.211-1_mips_24kc.ipk
Installing kmod-scsi-core (4.9.211-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen4/ar71xx/generic/kmod-scsi-core_4.9.211-1_mips_24kc.ipk
Package kmod-usb2 (4.9.211-1) installed in root is up to date.
Installing kmod-usb3 (4.9.211-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/modules/gluon-ffhb-2019.1.2+bremen4/ar71xx/generic/kmod-usb3_4.9.211-1_mips_24kc.ipk
Configuring kmod-scsi-core.
Configuring kmod-usb-storage.
Configuring libuuid.
Configuring libblkid.
Configuring block-mount.
this file has been obsoleted. please call "/sbin/block mount" directly
Configuring kmod-usb3.
Configuring libcomerr.
Configuring kmod-fs-ext4.
Configuring libss.
Configuring libext2fs.
Configuring e2fsprogs.
root@ffhb-a42bb0de8272-C7v2-00:
~~~

Hinweis Merken: **block-mount**, this file has been obsoleted. please call "/sbin/block mount" directly.

Dann checken wir mal, ob der Stick da ist.

**_`Eingabe:`_**
~~~
ls -al /dev/sd* 
~~~
OK, USB Stick wird angezeigt. 

**_`Ausgabe:`_**
~~~
brw-------    1 root     root        8,   0 Aug  7 17:04 /dev/sda
brw-------    1 root     root        8,   1 Aug  7 17:04 /dev/sda1
~~~
Wenn Probleme auftreten, bitte in den original Anleitungen weiterlesen.
[https://openwrt.org/docs/guide-user/storage/usb-drives](https://openwrt.org/docs/guide-user/storage/usb-drives)

[https://openwrt.org/docs/guide-user/storage/usb-installing](https://openwrt.org/docs/guide-user/storage/usb-installing)

Formatieren :-)

**_`Eingabe:`_**
~~~
mkfs.ext4 /dev/sda1
~~~

**_`Ausgabe:`_**
~~~
mke2fs 1.44.1 (24-Mar-2018)
/dev/sda1 contains a exfat file system labelled 'Samsung USB'
Proceed anyway? (y,N) **y**
Creating filesystem with 15664140 4k blocks and 3916304 inodes
Filesystem UUID: e5234b4f-3680-496a-9aa5-4b2e57992587
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424

Allocating group tables: done
Writing inode tables: done
Creating journal (65536 blocks):
done
Writing superblocks and filesystem accounting information: done
~~~

Für andere Datenträger (FAT, NTFS, SSD) werden ggf. andere oder zusätzliche Treiber benötigt.
Weitere Infos unter: [https://openwrt.org/docs/guide-user/storage/usb-drives](https://openwrt.org/docs/guide-user/storage/usb-drives)

Bis zu diesem Punkt hat alles funktioniert. Hier ein paar ergänzende Anmerkungen:
- Mountverzeichnis ist /mnt/sda1, dies kann natürlich mit anderen Parametern geändert werden.
- Ich sehe das Verzeichnis nicht / nicht mehr.
  - ist das rebootfest?
  - ist das updatefest?
  - automount?
  - no mount Anzeige hergestellt?
  - refresh des Anzeigefensters durchgeführt?

NoMountAnzeige, altes Linuxwissen.
An den Mountpunkt wird eine Verzeichnisstruktur des Datenträgers eingehängt. Was an diesem Punkt vorher war, wird ausgeblendet.
Also erstelle ich am Mountpunkt eine Datei mit aussagekräftigem Namen.
~~~
umount /mnt/sda1   
touch /mnt/sda1/USB_DISK_NOT_PRESENT
chmod 555 /mnt/sda1 
chmod 444 /mnt/sda1/USB_DISK_NOT_PRESENT
mount /dev/sda1 /mnt/sda1
~~~
Die Datei `USB_DISK_NOT_PRESENT` mit 0 Bytes sehe ich nur, wenn kein Stick gesteckt ist, bzw. kein mount erfolgt ist. Die Datei wird nicht auf dem Stick angelegt :-) sondern auf dem Router ohne Stick unter: /mnt/sda1/

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 2.) Samba konfigurieren
Samba fällt in die Kategorie NAS und sorgt dafür, das eine Laufwerksfreigabe erzeugt wird.
Auch hier wieder der Hinweis auf die Originalinstallationsanleitung bei OpenWRT.

[https://openwrt.org/docs/guide-user/services/nas/start](https://openwrt.org/docs/guide-user/services/nas/start)

Zunächst SSH Verbindung über die Konsole zu unserem Router herstellen, die SW Liste aktualisieren und samba installieren.
Alle weiterführende Informationen unter:

[https://openwrt.org/docs/guide-user/services/nas/cifs.server](https://openwrt.org/docs/guide-user/services/nas/cifs.server)

**_`Eingabe:`_**
~~~
opkg update && opkg install samba4
~~~

**_`Ausgabe:`_**
~~~

~~~


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 3.) Firewall öffnen
Hier ein paar Vorschläge, um Löcher in die Firewall zu bekommen. Die Konfiguration bitte in `firewall.user` vornehmen, damit die Konfig updatesicher ist. 

~~~
uci -q delete firewall.samba_nsds
uci set firewall.samba_nsds="rule"
uci set firewall.samba_nsds.name="Allow-Samba/NS/DS"
uci set firewall.samba_nsds.src="lan"
uci set firewall.samba_nsds.dest_port="137-138"
uci set firewall.samba_nsds.proto="udp"
uci set firewall.samba_nsds.target="ACCEPT"
uci -q delete firewall.samba_ss
uci set firewall.samba_ss="rule"
uci set firewall.samba_ss.name="Allow-Samba/SS"
uci set firewall.samba_ss.src="lan"
uci set firewall.samba_ss.dest_port="139"
uci set firewall.samba_ss.proto="tcp"
uci set firewall.samba_ss.target="ACCEPT"
uci -q delete firewall.samba_smb
uci set firewall.samba_smb="rule"
uci set firewall.samba_smb.name="Allow-Samba/SMB"
uci set firewall.samba_smb.src="lan"
uci set firewall.samba_smb.dest_port="445"
uci set firewall.samba_smb.proto="tcp"
uci set firewall.samba_smb.target="ACCEPT"
uci commit firewall
/etc/init.d/firewall restart
~~~


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**
