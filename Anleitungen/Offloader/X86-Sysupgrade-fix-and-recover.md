## Inhalt:
X86 Images Fixen
[[_TOC_]]


#### Aktuelle Änderungen

Ab 2020.1 wird die Imagegröße wieder angepasst von 256Mb auf 128Mb.
 - Für uns heisst das: vorher Backup erstellen, Datensicherung Konfig Sicherung. Nach dem Update geht es mit allen Installationen von vorne los.
 
Nach 2019: Das X86 Image kann gar nichts mehr. Es geht nicht mal mehr ein Ping -4 google.de. Ein X86 Offloader ist dann wirklich OFF und loaded nur noch. Alle Anleitungen funktionieren dadurch aktuell nicht.
EVTL. müssen erst ein paar Dienste wieder konfiguriert werden: DNS, Firewall.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


#### Kaputt

Wenn du auf dieser Seite gelandet bist, ist meistens etwas schief gegangen. Keiner Sorge, das lässt sich fixen. Bei X86 - Systemen ist die Festplatte größer als die Systempartition. Die X86 Images belegen ungefähr 50Mb Plattenplatz auf der Disk. Der restliche Plattenplatz ist unpartitioniert und steht zum Spielen bereit. Dieser Platz lässt sich für andere Anwendungen nutzen und muss nur eingerichtet (oder wieder gerettet) werden. Dazu kann die vorhandene Partition vergrößert werden oder eine weitere Partition erstellt werden.
Anm. Linux-Partitionen vergrössert man in der Regel nicht, es wird eine neue Partition in das vorhandene System eingehängt.
Der Autoupdater sollte deaktiviert werden, das verhindert Überraschungen.

Leider sind die Erweiterungen nicht upgradefest. Ein sysupgrade erzeugt immer wieder die Originalgröße des Images und löscht alle anderen Partitionen. Ein Fix in Gluon ist in Arbeit. Tip: Diese Spielereien können auch in einer VM Umgebung geübt werden. Mit der Umstellung auf LEDE wird sich die Partitionsgröße ändern, damit sind unsere Spielereien dann sowieso hinüber. Deshalb Backups anlegen und was ich behalten möchte, in einem Installationsscript ablegen, das erspart später viel Arbeit.

Wichtige Anmerkung zum Umstieg von Offloadern auf LEDE. Bisher wurde der beliebte FUTRO mit X86-generic bespielt. Nach dem Sysupgrade auf LEDE wird jedoch i386_pentium4 verwendet. Läuft die Kiste nur als Offloader, ist das kein Problem. Spielen wir mit der Kiste, (IRC Bouncer, ICE-Cast Server usw.) haben wir ein Problem. Es gibt deutlich weniger Pakages im Repro. Mit dem Wechsel auf X86_64 besteht das Problem nicht, hier werden alle Pakete angeboten. Wer Bastelt, bitte den Sysupgrade auf https://downloads.bremen.freifunk.net/firmware/testing/sysupgrade/gluon-ffhb-2017.1.4+bremen1+-x86-64-sysupgrade.img.gz setzen. Bei mir war ein Wechsel auf einem Futro S550-2 problemlos möglich.

Fall 1: Die vorhandene Partition wurde vergrößert und ein sysupgrade durchgeführt. Hier ist nichts mehr zu Retten, die Pertition wurde verkleinert. Für die Zukunft, nicht am Original rumfummeln und zusätzliche Partitionen immer einhängen.

Fall 2: Es war eine dritte Partition /sda3 erstellt und gemounted. Diese ist nun nach einem sysupgrade verschwunden.
Es kann Hilfe geben, wir gehen wie folgt vor:

- Das X86 System ist im Freifunk Online und wir können uns per Konsole auf einer der ipv6 Adressen Anmelden.

~~~
root@ffhb-0019997a7220:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                   47636     11100     35556  24% /
/dev/root                47636     11100     35556  24% /
tmpfs                   450700        92    450608   0% /tmp
tmpfs                      512         0       512   0% /dev
~~~
- Speichercheck, es ist genügend Speicher frei.

~~~
root@ffhb-0019997a7220:~# fdisk -l
-ash: fdisk: not found
~~~
- ok, fdisk nachinstallieren
- Die Liste ist immer wieder aktuell zu halten

~~~
root@ffhb-0019997a7220:~# opkg update (ist dieses nicht erfolgreich, s.u. opkg-update-fix)
~~~
- opkg update Fehlerfrei, hier gehts weiter. Ein paar Pakete nachinstallieren.

~~~
opkg install kmod-usb-storage block-mount block-hotplug kmod-fs-ext4 kmod-fs-vfat kmod-nls-cp437 kmod-nls-iso8859-1 e2fsprogs fdisk
~~~

~~~
root@ffhb-0019997a7220:~# fdisk -l

Disk /dev/sda: 971.6 MiB, 1018773504 bytes, 1989792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa7bc71bb

Device     Boot Start    End Sectors Size Id Type
/dev/sda1  *      512   8703    8192   4M 83 Linux
/dev/sda2        9216 107519   98304  48M 83 Linux
~~~
- Die Bestätigung, /dev/sda3 ist weg. Wird sda3 angezeigt, weiter mit block detect (weiter unten)
- Wiederherstellen der verlorenen Partition

~~~
root@ffhb-0019997a7220:~# fdisk /dev/sda

Welcome to fdisk (util-linux 2.25.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.
~~~

- Command (m for help): m (listet alle Möglichkeiten auf, wir starten mit n, alle defaults mit Enter übernehmen, der freie Platz wird die neue Partition)

~~~
Command (m for help): n
Partition type
   p   primary (2 primary, 0 extended, 2 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (3,4, default 3):
First sector (8704-1989791, default 108544):
Last sector, +sectors or +size{K,M,G,T,P} (108544-1989791, default 1989791):

Created a new partition 3 of type 'Linux' and of size 918.6 MiB.

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Re-reading the partition table failed.: Device or resource busy

The kernel still uses the old table. The new table will be used at the next reboot or after you run partprobe(8) or kpartx(8).

root@ffhb-0019997a7220:~# reboot
~~~
- Die verlorene Partition ist wieder da, diese können wir nun mounten.

~~~
mkdir -p /mnt/sda3
mount -t vfat /dev/sda3 /mnt/sda3 
umount /mnt/sda3   #make sure the disk isn't mounted before doing this
touch /mnt/sda3/USB_DISK_NOT_PRESENT
chmod 555 /mnt/sda3
chmod 444 /mnt/sda3/USB_DISK_NOT_PRESENT
mount -t /dev/sda3 /mnt/sda3
~~~
- Ist das mounten erfolglos, muss die Partition neu formatiert werden.
- Das ist eher selten der Fall und unsere Daten sind trotzdem futsch.
- War das mounten erfolgreich, sind alle Daten der alten Partition wieder da.
- Folgender Versuch, diskcheck!
- Einige Tools refreshen nicht, z.B. WINSCP, immer Aktualisieren Ctrl-R etc.

~~~
root@ffhb-0019997a7220:~# e2fsck -p /dev/sda3
e2fsck: Bad magic number in super-block while trying to open /dev/sda3
/dev/sda3:
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
~~~
- ok, hätte klappen können, unformatierte Partition, also Formatieren!

~~~
root@ffhb-0019997a7220:~# mkfs.ext4 /dev/sda3
mke2fs 1.42.12 (29-Aug-2014)
Creating filesystem with 235156 4k blocks and 58880 inodes
Filesystem UUID: 3c147685-20ee-4730-8526-2aee8412868a
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376

Allocating group tables: done
Writing inode tables: done
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done
~~~
- Check, ob Partition wieder automatisch gemountet wird.

~~~
root@ffhb-0019997a7220:~# block detect
config 'global'
        option  anon_swap       '0'
        option  anon_mount      '0'
        option  auto_swap       '1'
        option  auto_mount      '1'
        option  delay_root      '5'
        option  check_fs        '0'

config 'mount'
        option  target  '/mnt/sda1'
        option  uuid    '57f8f4bc-abf4-655f-bf67-946fc0f9f25b'
        option  enabled '0'

config 'mount'
        option  target  '/mnt/sda2'
        option  uuid    '57f8f4bc-abf4-655f-bf67-946fc0f9f25b'
        option  enabled '0'

config 'mount'
        option  target  '/mnt/sda3'
        option  uuid    '3c147685-20ee-4730-8526-2aee8412868a'
        option  enabled '0'
~~~
- Alle Einträge in der fstab vorhanden, booten oder mounten und die Platte ist wieder eingehängt.

~~~
root@ffhb-0019997a7220:~# mount /dev/sda3 /mnt/sda3
~~~

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

#### opkg-update-fix
Bei einigen Gluonversionen konnten keine Pakete installiert werden. Einfach den DNS auf 8.8.8.8 setzen. (Alternative DNS: 8.8.4.4, 9.9.9.9 - 9.9.9.12)

/etc/opkg.conf anpassen: Nur einen Teil pro Zeile einfügen.
Konsole:
~~~ 
echo "nameserver 8.8.8.8">>/etc/resolv.conf
/etc/init.d/gluon-wan-dnsmasq restart
~~~
Konsole über UCI Befehle
~~~
uci add_list gluon-wan-dnsmasq.@static[0].server=8.8.8.8
uci add_list gluon-wan-dnsmasq.@static[1].server=8.8.4.4
uci commit gluon-wan-dnsmasq
/etc/init.d/gluon-wan-dnsmasq restart
~~~

Über SCP editieren: /etc/resolv.conf
~~~
search lan
nameserver 8.8.8.8 8.8.4.4
nameserver 2001:4860:4860::8888 2001:4860:4860::8844

~~~

Alternativ die Pakete direkt installieren, d.h. per scp ins /tmp Verzeichnis kopieren.
~~~
root@ffhb-0019997a7220:~# opkg install openssl
Unknown package 'openssl'.
Collected errors:
 * opkg_install_cmd: Cannot install package openssl.
~~~
- manuelle Installation (Eintrag Prüfen: http://downloads.openwrt.org/chaos_calmer/15.05.1/x86/generic/packages/base/)

~~~
root@ffhb-0019997a7220:~# opkg install http://downloads.openwrt.org/chaos_calmer/15.05.1/x86/generic/packages/base/libevent2-openssl_2.0.22-1_x86.ipk
Downloading http://downloads.openwrt.org/chaos_calmer/15.05.1/x86/generic/packages/base/libevent2-openssl_2.0.22-1_x86.ipk.
Installing libevent2-openssl (2.0.22-1) to root...
Installing libopenssl (1.0.2g-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/openwrt/chaos_calmer/15.05.1/x86/generic/packages/base/libopenssl_1.0.2g-1_x86.ipk.
Installing zlib (1.2.8-1) to root...
Downloading http://downloads.bremen.freifunk.net/opkg/openwrt/chaos_calmer/15.05.1/x86/generic/packages/base/zlib_1.2.8-1_x86.ipk.
Configuring zlib.
Configuring libopenssl.
Configuring libevent2-openssl.

root@ffhb-0019997a7220:~# opkg install http://downloads.openwrt.org/chaos_calmer/15.05.1/x86/generic/packages/base/openssl-util_1.0.2g-1_x86.ipk --force-depends
Downloading http://downloads.openwrt.org/chaos_calmer/15.05.1/x86/generic/packages/base/openssl-util_1.0.2g-1_x86.ipk.
Installing openssl-util (1.0.2g-1) to root...
Configuring openssl-util.
~~~
- Wenn das alles nicht geht, die benötigten Pakete direkt aus dem Repro ziehen und ins /tmp schubsen, manuell installieren.
- Klappt das immer noch nicht, schau im IRC oder auf einem Freifunk Treffen vorbei.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

#### Update Januar 2018
Mit dem Umstieg auf LEDE können die Pakete von folgenden Seiten geladen werden:
HTTP 	https://downloads.lede-project.org/releases/packages-17.01/x86_64/
FTP 	ftp://ftp.halifax.rwth-aachen.de/lede/releases/packages-17.01/x86_64/

Eine Paketliste findet sich hier: https://lede-project.org/packages/table/start
Da auf der Flashkarte des FUTRO viel Platz ist (wir haben ja /mnt/sda3), habe ich einfach das verlinkte Pakage Verzeichnis dorthin kopiert und installiere meine benötigten Pakete einfach direkt von dort.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

#### Update Februar 2018
Die Pakage-Repros zwischen OpenWRT und LEDE sind verlinkt. Die Inhalte (Pakete)  zwischen 32 & 64 Bit sind angepasst.
~~~
https://downloads.openwrt.org/snapshots/packages/x86_64/packages/
https://downloads.lede-project.org/snapshots/packages/x86_64/packages/
~~~
Die Dateiablage ist identisch.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

#### Update Dezember 2022
Die Datei /etc/opkg/distfed.conf anpassen, ändere alle Links von HTTPS auf HTTP, dann klappt die SW Aktualisierung ohne SSL!

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Offloader auf X86-64 Image updaten
Die vielen Installationsanleitungen für einen Offloader beziehen sich immer auf das generic Image mit 32 Bit. Da funktioniert fast immer. Hier ist nun zu sehen wie einfach der Umstieg auf 64 Bit ist. In diesem Beispiel verwende ich die momentan gültige Testing unserer community. Bisher ist auf dem Offloader das Image https://downloads.bremen.freifunk.net/firmware/testing/sysupgrade/gluon-ffhb-2017.1.4+bremen2-x86-generic-sysupgrade.img.gz installiert. für den Umstieg lade ich das https://downloads.bremen.freifunk.net/firmware/testing/sysupgrade/gluon-ffhb-2017.1.4+bremen2-x86-64-sysupgrade.img.gz Image herunter. Mit einem unzipper eurer Wahl entpacken und ins /tmp Verzeichnis des Offloaders kopieren. Erfahrene Anwender machen das direkt alles im /tmp des Offloaders.
Nicht vergessen, Backup wichtiger Daten, zusätliche Partitionen sind weg und müssen neu erstellt werden. 

Per SSH einloggen, im /tmp einen sysupgrade anstossen, fertig. Siehe folgenden Output, von alt nach neu.
~~~
Using username "root".
Authenticating with public key "ffhb"


BusyBox v1.23.2 (2017-08-31 15:16:02 CEST) built-in shell (ash)

  _______                     ________        __
 |       |.-----.-----.-----.|  |  |  |.----.|  |_
 |   -   ||  _  |  -__|     ||  |  |  ||   _||   _|
 |_______||   __|_____|__|__||________||__|  |____|
          |__| W I R E L E S S   F R E E D O M
 -----------------------------------------------------
 CHAOS CALMER (Chaos Calmer, r49389)
 -----------------------------------------------------
  * 1 1/2 oz Gin            Shake with a glassful
  * 1/4 oz Triple Sec       of broken ice and pour
  * 3/4 oz Lime Juice       unstrained into a goblet.
  * 1 1/2 oz Orange Juice
  * 1 tsp. Grenadine Syrup
 -----------------------------------------------------
root@ffhb-0013490bd9f6:~#
root@ffhb-0013490bd9f6:~# cd /tmp
root@ffhb-0013490bd9f6:/tmp# ls
TZ
dhcp.leases
dnsmasq.d
etc
extroot
fastd
gluon
gluon-ffhb-2017.1.4+bremen2-x86-64-sysupgrade.img
hosts
lib
lock
log
resolv.conf
resolv.conf.auto
run
shm
spool
state
root@ffhb-0013490bd9f6:/tmp# sysupgrade -F gluon-ffhb-2017.1.4+bremen2-x86-64-sysupgrade.img
Reading partition table from bootdisk...
Reading partition table from image...
Partition layout has changed. Full image will be written.
Saving config files...
Commencing upgrade. All shell sessions will be closed now.
Using username "root".
Authenticating with public key "ffhb"


BusyBox v1.25.1 () built-in shell (ash)

     _________
    /        /\      _    ___ ___  ___
   /  LE    /  \    | |  | __|   \| __|
  /    DE  /    \   | |__| _|| |) | _|
 /________/  LE  \  |____|___|___/|___|                      lede-project.org
 \        \   DE /
  \    LE  \    /  -----------------------------------------------------------
   \  DE    \  /    Reboot (17.01-SNAPSHOT, r3581+39-6b6578f)
    \________\/    -----------------------------------------------------------

root@ffhb-0013490bd9f6:~#

~~~
Das ist echt cool :-)

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Upgradefest, Upgrade-Fest
Es wird immer wieder die Frage gestellt, wie man Pakete upgradesicher installieren kann. Achtung: In der Frage ist bereits ein fataler Fehler enthalten. Nicht die Pakete sind es, sondern die Konfiguration soll erhalten bleiben. Mit einem Sysupgrade können neuere Pakete bereitgestellt werden.

Nach einem sysupgrade installieren wir die zusätzlichen Pakete neu. Wir können uns hierfür eine Favoritenliste oder ein Script basteln.
~~~
meineprogs.sh
opkg update && opkg install znc znc-mod-fail2ban znc-mod-flooddetach znc-mod-log znc-mod-webadmin znc-webskin-ice
~~~

In der Datei /etc/sysupgrade.conf kann man festlegen, welche Dateien oder Ordner behalten werden sollen:
Hier werden nicht die Pakete aufgenommen, sonderen deren Konfigurationsdateien oder die Orte an denen diese liegen.
~~~
## This file contains files and directories that should
## be preserved during an upgrade.

# /etc/example.conf
/etc/openvpn/
/etc/ice.sh
/etc/icecast.xml
/etc/icecast.xml-opkg
/etc/ices-alsa.xml
/etc/ices-oss.xml
/etc/ices-roar.xml
/etc/listuserpackages.awk
/etc/listuserpackages.sh
/var/log/icecast/
/var/log/icecast/error.log
/var/log/icecast/access.log
/var/log/ices/
/var/log/ices/ices.log
/var/etc/configs/
/var/etc/configs/znc.conf
/root/.znc/
/root/.znc/znc.pem
/root/.znc/configs/
/root/.znc/configs/znc.conf
/root/.znc/moddata/
/root/.znc/users/
~~~
Hier muss man jedoch alle Konfigurationsdateien angeben, die bei einem Paket installiert werden, also auch Libraries, evtl. LOG-Files und config files.
Besondere Benutzer und Rechte bitte mit in einem eigen Script hinterlegen.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


