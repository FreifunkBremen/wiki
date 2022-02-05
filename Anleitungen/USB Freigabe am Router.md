### Wie kann ein USB Stick am Router als Laufwerk verwendet werden?
Erstellt am: 08.08.2021 Thema noch nicht abgeschlossen, Einrichtung ok, Zugriff funktionirt novh nicht.

Nun, das ist ganz einfach, folgende 2 Schritte sind notwendig.
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

Dann checken wir mal, ob der Stick da ist. Je nach Routertyp kann der USB Stick sda2 oder sdb1 sdb2 sein.

**_`Eingabe:`_**
~~~
ls -al /dev/sd* 
~~~
OK, USB Stick wird angezeigt. 

**_`Ausgabe:`_**
~~~
brw-------    1 root     root        8,   0 Feb  4 22:21 /dev/sda
brw-------    1 root     root        8,   1 Feb  4 22:21 /dev/sda1
brw-------    1 root     root        8,   2 Feb  4 22:21 /dev/sda2
brw-------    1 root     root        8,   3 Feb  4 22:21 /dev/sda3
brw-------    1 root     root        8,  16 Feb  5 13:56 /dev/sdb
brw-------    1 root     root        8,  17 Feb  5 13:56 /dev/sdb1

~~~
Wenn Probleme auftreten, bitte in den original Anleitungen weiterlesen.
[https://openwrt.org/docs/guide-user/storage/usb-drives](https://openwrt.org/docs/guide-user/storage/usb-drives)

[https://openwrt.org/docs/guide-user/storage/usb-installing](https://openwrt.org/docs/guide-user/storage/usb-installing)

Formatieren :-)

**_`Eingabe:`_**
~~~
mkfs.ext4 /dev/sdb1
~~~

**_`Ausgabe:`_**
~~~
mke2fs 1.44.1 (24-Mar-2018)
/dev/sdb1 contains a exfat file system labelled 'Samsung USB'
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
umount /mnt/sdb1   
touch /mnt/sdb1/USB_DISK_NOT_PRESENT
chmod 555 /mnt/sdb1 
chmod 444 /mnt/sdb1/USB_DISK_NOT_PRESENT
mount /dev/sdb1 /mnt/sdb1
~~~
Die Datei `USB_DISK_NOT_PRESENT` mit 0 Bytes sehe ich nur, wenn kein Stick gesteckt ist, bzw. kein mount erfolgt ist. Die Datei wird nicht auf dem Stick angelegt :-) sondern auf dem Router ohne Stick unter: /mnt/sda1/

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 2.) Symbolischen Link für den Webserver setzten.

Tricky & Dirty, funktioniert aber ;.)

* Per SSH auf dem Router anmelden.
* `cd /lib/gluon/status-page/www/`
* `ln -s /mnt/usb shared`
    * /mnt/usb ist der Ort der Freigabe, der zweite Parameter (hier shared) soll der künftige Name sein.
* Zugriff dann über: http://[2a06:8782:ffbb:1337:c6e9:84ff:fed5:138e]/shared/
    * Also HTTP://   [ipv6 des Routers] /Name-der-Freigabe

Löschen der Freigabe: `rm /lib/gluon/status-page/www/shared` (das letzte /shared ist der Freigabename, den ihr gewählt habt).

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


### 3.) Alternativ: Samba konfigurieren (kann man machen)
Samba fällt in die Kategorie NAS und sorgt dafür, das eine Laufwerksfreigabe erzeugt wird.
Auch hier wieder der Hinweis auf die Originalinstallationsanleitung bei OpenWRT.

[https://openwrt.org/docs/guide-user/services/nas/start](https://openwrt.org/docs/guide-user/services/nas/start)

Zunächst SSH Verbindung über die Konsole zu unserem Router herstellen, die SW Liste aktualisieren und samba installieren.
Alle weiterführende Informationen unter:

[https://openwrt.org/docs/guide-user/services/nas/cifs.server](https://openwrt.org/docs/guide-user/services/nas/cifs.server)

**_`Eingabe:`_**
~~~
opkg update && opkg list | grep -i samba
~~~

**_`Ausgabe:`_**
~~~
...
samba36-client - 3.6.25-12 - Samba 3.6 SMB/CIFS client
samba36-hotplug - 3.6.25-12 - Samba 3.6 SMB/CIFS hotplug
samba36-net - 3.6.25-12 - Samba 3.6 SMB/CIFS net commands
samba36-server - 3.6.25-12 - The Samba software suite is a collection of programs that implements the SMB protocol for UNIX systems, allowing you to serve files and printers to Windows, NT, OS/2 and DOS clients. This protocol is sometimes also referred to as the LanManager or Netbios protocol.
~~~

**_`Eingabe:`_**
~~~
opkg install samba36-server
~~~

**_`Ausgabe:`_**
~~~
Installing samba36-server (3.6.25-12) to root...
Downloading http://downloads.openwrt.org/releases/18.06-SNAPSHOT/packages/mips_24kc/base/samba36-server_3.6.25-12_mips_24kc.ipk
Configuring samba36-server.
~~~

Konfigdatei:  /etc/config/samba



**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

#### 3.1.) Firewall für Samba öffnen
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

Die Einträge in der Konfigdatei /etc/firewall sehen dann so aus.

~~~
config rule 'samba_nsds'
	option name 'Allow-Samba/NS/DS'
	option src 'lan'
	option dest_port '137-138'
	option proto 'udp'
	option target 'ACCEPT'

config rule 'samba_ss'
	option name 'Allow-Samba/SS'
	option src 'lan'
	option dest_port '139'
	option proto 'tcp'
	option target 'ACCEPT'

config rule 'samba_smb'
	option name 'Allow-Samba/SMB'
	option src 'lan'
	option dest_port '445'
	option proto 'tcp'
	option target 'ACCEPT'
~~~

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 4.) Alternativ: FTP-Server konfigurieren (damit Leute was hochladen können)

* per SSH auf dem Knoten einloggen
* `opkg update`
* `opkg install vsftpd`
* Passwort für ftp-Benutzer setzen: `passwd ftp`
* Home-Verzeichnis für ftp-Benutzer auf den USB-Stick setzen:
    * Benutzer-Config mit`vi /etc/passwd` bearbeiten
    * dann in der `ftp`-Zeile das `/home/ftp` durch `/mnt/usb` ersetzen (oder den Ordner, der per FTP erreichbar sein soll)
    * dieser Ordner muss existieren und muss für den ftp-Benutzer lesbar sein. Der Ordner darf aber nicht schreibbar sein!
    * deshalb am besten in diesem Ordner noch einen weiteren Ordner anlegen, der dann für den ftp-Benutzer schreibbar ist:
        * `mkdir /mnt/usb/upload`
        * `chown ftp:ftp /mnt/usb/upload`
* mit `vi /etc/vsftpd.conf` die Config-Datei bearbeiten:
    * `listen=YES` auf `listen=NO` ändern
    * `listen_ipv6=YES` hinzufügen
    * `chroot_local_user=YES` hinzufügen
    * `userlist_enable=YES` hinzufügen
    * `userlist_deny=NO` hinzufügen
    * `userlist_file=/etc/vsftpd/vsftpd.users` hinzufügen
* Liste der erlaubten FTP-Nutzer anlegen: `echo ftp > /etc/vsftpd/vsftpd.users`
* Config-Änderungen anwenden: `/etc/init.d/vsftpd restart`

#### Firewall-Regel für FTP hinzufügen
* mit `vi /etc/config/firewall` die Firewall-Config bearbeiten und ganz unten diese Zeilen einfügen:
```
config rule 'public_ftp'           
        option dest_port '21'               
        option src 'mesh'                   
        option target 'ACCEPT'                 
        option proto 'tcp'                   
        option name 'public_ftp'                
```
* Änderungen der Firewall-Config anwenden: `/etc/init.d/firewall restart`

Jetzt sollte der FTP-Server unter der IP des Knotens erreichbar sein. Man kann sich dann als Benutzer "ftp" einloggen, mit dem Passwort, das am Anfang (bei `passwd ftp`) gesetzt wurde.

Die Firewall-Regeln sind sehr einfach gehalten. Manche FTP-Programme kommen damit nicht klar; dann kann man evtl. noch die Firewall-Regeln so erweitern, wie das unter [[https://forum.openwrt.org/t/configuring-firewall-for-cross-zone-ftp-connections/84567]] beschrieben wird.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


### 5.) Alternativ: WebDAV-Server konfigurieren (damit Leute was hochladen können)

Ist unter [[https://gist.github.com/stokito/5db2aa2cc184717d45600889d8115100]] beschrieben. Hab ich aber nicht ausprobiert :-)

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**
