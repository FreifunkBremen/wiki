#Futro S900 als Offloader

Alternativ zum Futro S550 kann man auch den Futro S900 als Offloader benutzen. Den Futro-S900 bekommt man in der Bucht füf 19€ (http://www.ebay.de/itm/142017687738). Er benutzt als Speichermedium statt der CFcard eine mSATA, die noch hinzu gekauft werden muss.

Bei mir kommt z.Zt. eine SanDisk 32GByte aus der Bucht für €20 zum Einsatz. Es war die kleinste, die ich auf die Schnelle gefunden habe.

Der Rest läuft in der gleichen Weise ab. Es werden benötigt:

1. Risercard
2. Netzwerkkarte

Die Installation läuft genau so ab wie beim Futro S550. Auf dem USB-Stick muss aber die
~~~
bitte_nicht_loeschen.sh
~~~

geändert oder erweitert werden. Da das Script den vorhandenen CPU-Typ überprüft, muss der neue CPU-Typ ergänzt oder einer der vorhandenen Einträge überschrieben werden.

Der Eintrag lautet:

~~~
if (grep -Fq "AMD G-T44R Processor" /proc/cpuinfo) ; then
  echo "AMD G-T44R Processor -> Futro S900"
~~~

Wenn externe Speichermedien an den USB Port verwendet werden, ist im BIOS die Bootsequenz auf die interne mSata zu stellen und Force USB Boot zu deaktivieren.
Sonst versucht der Futro von USB zu booten.


Weitere Partition auf der mSata mit fdisk einrichten
~~~
fdisk -l

Disk /dev/sda: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x3815abaf

Device     Boot Start    End Sectors Size Id Type
/dev/sda1  *      512   8703    8192   4M 83 Linux
/dev/sda2        9216 107519   98304  48M 83 Linux
~~~

~~~
fdisk /dev/sda
n new
p primary
defaults mit Enter bestätigen
w write
reboot
~~~

und /dev/sda3 einhängen

mkdir -p /mnt/share
mount -t ext4 /dev/sda3 /mnt/share

mount: mounting /dev/sda3 on /mnt/share failed: No such file or directory

Ach ja, da war noch was, Formatieren vergessen :-)

~~~
mke2fs -t ext4 /dev/sda3
mke2fs 1.42.12 (29-Aug-2014)
Discarding device blocks: done
Creating filesystem with 7803094 4k blocks and 1954064 inodes
Filesystem UUID: da78f1cc-c42f-4209-a9fd-469cd32800cc
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done
~~~

Mit Systemstart mounten, in /etc/config/fstab folgende Zeilen anfügen.
~~~
config 'mount'
	option	target	'/mnt/share'
	option	uuid	'da78f1cc-c42f-4209-a9fd-469cd32800cc'
	option	enabled	'0'
~~~
die uuid kann auch mit "Block Detect" angezeigt werden.

