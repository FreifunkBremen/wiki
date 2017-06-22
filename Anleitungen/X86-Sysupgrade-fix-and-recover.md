Bei X86 - Systemen ist die Festplatte größer als die Systempartition. Die X86 Images belegen ungefähr 50Mb Plattenplatz auf der Disk. Der restliche Plattenplatz ist unpartitioniert. Dieser Platz lässt sich für andere Anwendungen nutzen und muss nur eingerichtet werden. Dazu kann die vorhandene Partition vergrößert werden oder eine weitere Partition erstellt werden.

Leider sind die Erweiterungen nicht upgradefest. Ein sysupgrade erzeugt immer wieder die Originalgröße des Images und löscht alle anderen Partitionen. Ein Fix in Gluon ist in Arbeit. Diese Spielereien können auch in einer VM Umgebung geübt werden.

Fall 1: Die vorhandene Partition wurde vergrößert und ein sysupgrade durchgeführt. Hier ist nichts mehr zu Retten, die Pertition wurde verkleinert.

Fall 2: Es war eine dritte Partition /sda3 erstellt und gemounted. Diese ist nun nach einem sysupgrade verschwunden.
#### Es kann Hilfe geben, wir gehen wie folgt vor:

- Das X86 System ist im Freifunk Online und wir können uns per Konsole Anmelden.

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
- Die Bestätigung, /dev/sda3 ist weg.
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

## opkg-update-fix
Bei einigen Gluonversionen konnten keine Pakete installiert werden. Einfach den DNS auf 8.8.8.8 setzen.
Alternativ die Pakete direkt installieren:

~~~
root@ffhb-0019997a7220:~# opkg install openssl
Unknown package 'openssl'.
Collected errors:
 * opkg_install_cmd: Cannot install package openssl.
~~~
- manuelle Installation

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
- Klappt das immer noch nicht, schau auf einem Freifunk Treffen vorbei.

