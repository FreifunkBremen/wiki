**Wir bauen uns ein Image für den Offloader Fujitsu-Siemens Futro S550-2**

In den Freifunk-Foren werden viele interessante Themen um den Futro besprochen.
Um die benötigten Informationen nicht überall zusammensuchen zu müssen, hier
eine kleine Zusammenfassung für das Bremer Futro-Image. Ganz Eilige können gleich ans Ende dieses Beitrages springen.

**1.) Abschnitt: Die Hardware.**

Fujitsu Siemens Futro S550-2.
Erste Informationen sind unter [https://forum.freifunk.net/t/f-a-q-zum-offloader-fujitsu-siemens-futro-s550/8294](https://forum.freifunk.net/t/f-a-q-zum-offloader-fujitsu-siemens-futro-s550/8294) zu finden.

Gerät öffnen: (Nur wenn eine 2te Netzwerkkarte eingebaut werden soll)
! Elektrostatische Aufladung kann das Gerät zerstören, unbedingt für ausreichnde Erdung sorgen.

Gerät auf die Seite legen, die Rückseite zu uns. Die **zwei** Schrauben **links** lösen. Die Schraube rechts bleibt im Gerät. Für die Schrauben gibt es kein vernünftig passendes Werkzeug, also ausprobieren, welches am besten passt. Schrauben entfernen. Gehäusedeckel mit Frontblende ca. 1cm in Richtung Frontblende schieben. Leichte Schläge mit der Hand helfen beim lösen. Gehäusedeckel mit Frontblende nach oben abnehmen. Der Metallsteg in der Mitte bleibt festgeschraubt. An der Frontseite ist der Metallsteg nur eingesteckt. Um die Risercard einzusetzen, wird der Metallsteg angehoben, damit mehr Platz zum Einsetzen ist.
Netzwerkkarte mit kurzem Slotblech (1/2 Bauhöhe) einsetzten. Bei Netzwerkkarten mit langem Slotblech, dieses Kürzen und umbiegen. Das Slotblech wird später nur eingeklemmt. Bedingung für Karten mit langem Slotblech, diese müssen mit 3,3V funktionieren. 5V Karten sollen nicht funktionieren (bisher nicht getestet.)
Soll das Image per USB-Stick aufgespielt werden, kann das Gehäuse jetzt wieder zusammengebaut werden. Metallbügel auf richtigen Sitz kontrollieren und Gehäusedeckel einsetzten. Vor dem Zuschrauben, den Sitz der Netzwerkkarte kontrollieren und ggf. justieren, damit die LAN Buchse zugänglich ist. Das Gerät ist nun fertig, und das Image kann eingespielt werden kann.

**2.) Image einspielen.**

Um ein Image aufzuspielen, gibt es mehrere Methoden. Die schnellste und eleganteste ist das Aufspielen mit einem USB-Stick. Dazu benötigen wir einen bootfähigen USB-Stick.

Dazu ladet Euch das Gluon2Futro-USB-Stick-Image von [Github](https://raw.githubusercontent.com/oszilloskop/Gluon2Futro/master/gluon2futro.img) herunter, und transferiert es auf einen USB-Stick ( mit 'dd' oder 'Win32 Disk Imager' oder 'Rufus'). Auf dem USB-Stick befindet sich danach ein Mini-Linux auf einer FAT32 Partition. Der USB-Stick muss mind. 64MB groß sein. Alle bisher gespeicherte Daten auf dem USB-Stick gehen verloren! [Gluon2Futro](https://github.com/oszilloskop/Gluon2Futro)

Dann einfach euer gewünschtes Gluon-x86-Factory-Image (die gepackte Version *.img.gz) auf den vorbereiteten USB-Stick kopieren (das geht mit jedem Win/Linux/Mac PC per Datei-Manager des jeweiligen Betriebsystems). Wenn jetzt der Futro mit diesem USB-Stick gebootet wird, so wird das Gluon-x86-Image vollautomatisch auf die interne CF-Karte des Futros übertragen.

Es gibt nach ca. 20-60 Sekunden auf jeden Fall eine akustische Rückmeldung:
Alles okay = 5 x Piepen
Fehler = 10 Sekunden wildes Gepiepse

Bei dieser Aktion ist eine PS/2 Tastatur und ein Monitor mit DVI Stecker / Kabel erforderlich. Futro einschalten und mit F2 in das Setup. Bootreihenfolge auf den Stick einstellen und neu starten. Die Option F12 Bootreihenfolge einstellen, funktionierte bei mir nicht. Hin und wieder klappt das kopieren des Images nicht, dann einfach den Vorgang wiederholen. Der Futro bootet vom Stick und nach 10 Sekungen ist das Image eingespelt. Der Futro schaltet sich ab, jetzt den USB Stick entfernen. Falls Ihr ein Gluon-X86-Factory-Image mit CF-Karten-Unterstützung (in **v2016.1.2** bereits enthalten) geflasht habt, so ist euer Futro S550 nach einem Neustart im Konfigurationsmodus und somit über http://192.168.1.1 zu erreichen.

P.S.
Wichtig ist, dass sich nur ein Gluon-x86-Image (die gepackte Version *.img.gz) auf dem vorbereiteten USB-Stick befindet!
Detaillierte Informationen findet Ihr auf [https://github.com/oszilloskop/Gluon2Futro32](https://github.com/oszilloskop/Gluon2Futro)

P.S.S.
Bitte bootet keinen PC mit diesem USB-Stick. Eure Daten sind dann hinüber. Das Image wird ohne Nachfrage installiert.

Eine andere Methode ist das Einspielen mit einem CF-Cardreader. Bei dieser Aktion kann auch das Image, das auf der zweiten Partition auf der CF-Karte ist, mit Gpartet vergrössert werden. Das Filesystem ist auf 128Mb eingestellt. Bei grösseren Partitionen ist noch eine Datenträgerprüfung durchzuführen, damit das Filesystem die ganze Partition verwendet. Notwendig ist die Vergrösserung nicht, von dem 50 Mb Image ist nur die Hälfte belegt. Genug Platz für weitere Installationen. In dem restlichen Bereich kann auch eine zusätzliche Partition erstellt
werden, die dann später gemountet wird.

Im nächsten Kapitel bauen wir das Image selber.

**3.) Eigene Images bauen.**

Zutatenliste. Internetzugang, ein debian basierendes Linux wie Ubuntu (Empfehlung), ca. **50GB** freien Plattenplatz.
Optional: SSD und I7 Prozessor beschleunigt die Erstellung auf 2h, 20 Min. nur X86 Image. Oder Zeit zum Erstellen einplanen. Wer noch kein Linux installiert hat, freie Partition auf dem PC schaffen und Ubuntu installieren, aktualisieren und durchbooten. Alternativ über eine virtuelle Maschine (VMWare/ Virtual Box). Gut unter Freifunk Youtube erklärt. Beider Installationen sind recht einfach,
die Bedienung des Linux ist dann eher Gewöhnungsbedürftig.

Wir bewegen uns auf die Seite [https://github.com/FreifunkBremen/gluon-site-ffhb.git](https://github.com/FreifunkBremen/gluon-site-ffhb.git) und lesen das Readme.md
Diese Anleitung ist hervoragend. Nach dieser Anleitung bitte die Images erstellen.
Sollte das build.sh Script einmal irgendwo aussteigen, einfach neu starten und weiter laufen lassen. Wenn das klappt, haben wir einmal alle Images für die gängigen Router erstellt.

Wer nicht in die Konfiguration eingreifen möchte, kann ab Version **v2016.1.2** das fertige X86 Image verwenden und die benötigten Pakete von Hand nachinstallieren. Das wäre eine Option, wenn ich kein Image selber erstellen möchte.

In dem **Read.me** ist beschrieben, wie das build.sh Script funktioniert. Ich möchte aber temporär die site.mk und das build.sh script anpassen.
Beide Dateien in das Homeverzeichnis kopieren oder die Originale umbenennen in z.B. site.mk.orig usw.

Ergänzung vom 8.4.2016: Hier ein die Befehlsfolge für einen neuen Durchlauf im Homeverzeichnis (ohne Änderungen) 
~~~
rm -rdf gluon-site-ffhb
rm -rdf gluon
sudo apt-get install coreutils build-essential subversion git libncurses5-dev zlib1g-dev unzip gawk libssl-dev
git clone https://github.com/freifunk-gluon/gluon.git gluon -b v2016.1.3
git clone --recursive https://github.com/FreifunkBremen/gluon-site-ffhb.git
cd gluon-site-ffhb/
git -C gluon checkout v2016.1.3
./build.sh testing
~~~


In die Site.mk werden folgende Zeilen eingefügt. (Anmerkung: ab **v2016.1.2** gibt es Änderungen, weiter unten beschrieben)
```
  kmod-usb-core \
	kmod-usb2 \
	kmod-usb-hid \
	kmod-usb-net \
	kmod-usb-net-asix \
	kmod-r8169 \
	kmod-usb-storage \
	block-mount \
	kmod-fs-ext4 \
	kmod-fs-vfat \
	kmod-nls-cp437 \
	kmod-nls-iso8859-1 \
	kmod-scsi-core \
	kmod-fs-ext4 \
	e2fsprogs \
```
Ist ein Paket schon vorhanden, (doppelter Eintrag :-) wird der Eintrag übersprungen. Welche Pakete für den Futro benötigt werden, um das volle Potential auszuschöpfen, ist aktuell nicht bekannt, hier besteht Experimentierbedarf.

In der Build.sh ab Zeile 124, folgede Änderungen vornehmen. (Anmerkung: ab **v2016.1.2** gibt es Änderungen, der Patch nicht mehr notwendig)

**#Hier kopiere ich den Futro Patch für 2015.x && 2016.1.1**
```
echo "CONFIG_PATA_ATIIXP=y" >> gluon/openwrt/target/linux/x86/generic/config-3.10 
echo "CONFIG_PATA_ATIIXP=y" >> gluon/openwrt/target/linux/x86/generic/config-default

cd "$GLUON_DIR"
export GLUON_BRANCH GLUON_RELEASE
if ! $cont; then
  make update ${debug:+V=s}
fi
```

**#for target in ar71xx-generic ar71xx-nand mpc85xx-generic x86-generic; do** 

_Diese Zeile austauschen, nur "x86-generic" bleibt enthalten_
```
for target in x86-generic; do   
```
_das mache ich nur, weil ich Schreibfaul bin._

"./build.sh stable" neu laufen lassen. Die x86-generic Images werden jetzt mit dem Futro Image überschrieben.
Das Futro Image liegt unter:
[/home/MEIN-PC-NAME/gluon-site-ffhb/gluon/output/images/factory].
Das Image **gluon-ffhb-2016.1.2+bremen1-x86-generic.img.gz** nun auf den bootfähigen USB-Stick kopieren, fertig. Fertig heisst, jetzt den Futro mit USB Image booten.


PS. Elegantere Lösung für die Site.mk (ab **v2016.1.2** getestet) Siehe weiter unten: 
```
ifeq ($(GLUON_TARGET),x86-generic)
GLUON_SITE_PACKAGES += \
    kmod-usb-core \
    kmod-usb2 \
    kmod-usb-hid \
    kmod-usb-net \
    kmod-usb-net-asix \
    kmod-usb-net-dm9601-ether \
    kmod-r8169
endif
```
Aktuelle Infos zur USB Unterstützung auch unter:
https://github.com/freifunk-gluon/gluon/wiki/USB-Support

Ergänzung 12.4.2016: Der **./build.sh** Durchlauf **v2016.1.3** wurde bei mir mit Fehler: *Too many levels of symbolic links * abgebrochen. Falls dieser Fehler auftritt, folgenden Workaround anwenden und den Prozess erneut starten/fortsetzen.
~~~
rm -Rf openwrt/staging_dir/host/.prereq-build openwrt/staging_dir/host/bin/bash
~~~

**4.) Konfiguration**

Der Futro wird wie ein FF-Router konfiguriert. Mit dem Browser unter 192.168.1.1 die Konfiguration vornehmen. Mesh on LAN und VPN Tunnel ist wichtig. Die LAN Schnittstelle auf der konfiguriert wird, ist die Onboardkarte. Nach der Konfiguration kann ich nur noch über einen angeschlossenen Router auf den Futro via SSH zugreifen, oder aus den FF Netz. Direkt mit dem PC bekomme ich keine Verbindung zustande. SSH-Key oder PW nicht vergessen. Welche Seite jetzt WAN oder LAN wird, hängt davon ab, mit welcher Buchse ich eine Verbindung zu meinen DSL-Gast-LAN Anschluss herstelle. Wenn der Futro Online ist, wird die andere Buchse automatisch gelb und zum LAN.

Wird jetzt ein USB Stick gesteckt, wird dieser aber erkannt, aber noch nicht automatisch gemountet.

Wir brauchen einen SSH Zugang. Adresse vergessen? Hängt die Kiste ins Netz und wartet bis er auf der Karte angezeigt wird. Dort kann die IPv6 Adresse abgelesen werden.

**Mounten von Hand:**

**# Ich möchte für jedes Objekt einen eigenen Mountpunkt**
```
mkdir -p /mnt/sda3
mkdir -p /mnt/usb
```
**# Jetz hänge ich die CF-Partition und den USB-Stick ein.**
```
mount -t ext4 /dev/sda3 /mnt/sda3 
mount -t vfat /dev/sdb1 /mnt/usb
```
**Automount** Die Konfiguration in die fstab /etc/config/fstab schreiben.
Über uci geht das so: (Bitte nur für die vorhanden Partitionen).
```
uci set fstab.sda3=mount
uci set fstab.sda3.enabled=1
uci set fstab.sda3.device="/dev/sda3"
uci set fstab.sda3.target="/mnt/sda3"
uci set fstab.usb=mount
uci set fstab.usb.enabled=1
uci set fstab.usb.device="/dev/sdb1"
uci set fstab.usb.target="/mnt/usb"
uci commit
```
Mit einem Editor deiner Wahl dann wie folgt ergänzen. /etc/config/fstab
```
**#Folgendes steht schon drin.**
 config 'global'
    option  anon_swap   '0'
    option  anon_mount  '0'
    option  auto_swap   '1'
    option  auto_mount  '1'
    option  check_fs    '0'

 config 'mount'
    option  target  '/mnt/sda1'
    option  uuid    '57f8f4bc-abf4-655f-bf67-946fc0f9f25b'
    option  enabled	'0'

 config 'mount'
    option  target  '/mnt/sda2'
    option  uuid    '57f8f4bc-abf4-655f-bf67-946fc0f9f25b'
    option  enabled	'0'

 **# ab hier anzufügende neue Einträge:**
 config 'mount'
    option  target	'/mnt/sda3'
    option  uuid	'b0dcc595-86dd-4154-a749-45894b002a18'
    option 'device' '/dev/sda3'
    option 'options' 'rw,sync'
    option 'enabled_fsck' '0'
    option 'enabled' '1'

 config 'mount'
    option  target  '/mnt/usb'
    option  uuid    '6633-6536'
    option 'device' '/dev/sdb1'
    option 'options''rw,sync'
    option 'enabled_fsck' '0'
    option 'enabled' '1'
```

Die UID zeigt der Befehl ```blkid```. die Option ```uuid``` ist aber nicht notwendig, geht auch ohne. Mehr zu dem Thema unter [https://wiki.openwrt.org/doc/techref/block_mount](https://wiki.openwrt.org/doc/techref/block_mount)

_So, und nun viel Spass beim Futro-Basteln._


**5.) Image-Update auf Community-Release 27.03.2016**

Angefügt: 27.03.2016
In diesem Kapitel wird nun das selbst gebastelte Image auf das X86 Image der Community angehoben/geändert. *Achtung:* Zusätzliche Partitionen der Flashkarte sind dann weg, die Arbeitspartition sda2 wird wieder auf 50Mb verkleinert, zumindest bei mir. Einige nachinstallierte Programme sind weg (z.B. tcpdump etc.).
(Ergänzung folgt, wenn es eine Lösung gibt.) Die Daten der zusätzlichen Partititionen auf USB sichern. Damit die CF-Card wieder voll genutzt werden kann, hilft nur ein Kartenleser und Gparted (Linux-Partitionierer). 
Ab Openwrt v2016.1.2 ist die CF Kartenunterstützung enthalten und ein Sysupdate sollte möglich sein.
Schritt 1, da ich nicht auf das Repository über https:// zugreifen kann, Openssl installieren

```
opkg update
opkg install openvpn-openssl openvpn-easy-rsa
```

Jetzt das Image der Community laden. In diesem Fall FFHB.
Aktuell, Januar 2018 ist 2017.1.4 in Vorbereitung. Als Testing unter:
https://downloads.bremen.freifunk.net/firmware/testing/sysupgrade/gluon-ffhb-2017.1.4+bremen1+-x86-generic-sysupgrade.img.gz

```
cd /tmp
wget https://downloads.bremen.freifunk.net/firmware/testing/sysupgrade/gluon-ffhb-2016.1.2+bremen1-x86-generic-sysupgrade.img.gz
gzip -d gluon-ffhb-2016.1.2+bremen1-x86-generic-sysupgrade.img.gz
sysupgrade -v /tmp/gluon-ffhb-2016.1.2+bremen1-x86-generic-sysupgrade.img

```

Der Offloader bootet, sda3 ist weg. USB Pakete nochmals laden/aktualisieren. USB neu mounten, und jetzt ggf. Autoupdate aktivieren.
Kleine Optimierung: **Disable writing when not mounted** siehe hierzu: https://wiki.openwrt.org/doc/howto/usb.storage

```
opkg update
opkg install kmod-usb-storage block-mount block-hotplug kmod-fs-ext4 kmod-fs-vfat kmod-nls-cp437 kmod-nls-iso8859-1

mkdir -p /mnt/usb
umount /mnt/usb   #make sure the disk isn't mounted before doing this
touch /mnt/usb/USB_DISK_NOT_PRESENT
chmod 555 /mnt/usb 
chmod 444 /mnt/usb/USB_DISK_NOT_PRESENT
mount -t vfat /dev/sdb1 /mnt/usb

uci set autoupdater.settings.enabled=1
uci set autoupdater.settings.branch=stable
uci commit autoupdater
```

Fertig, der Offloader zeigt nun:
Firmware	2016.1.2+bremen1 / gluon-v2016.1.2
Autom. Updates	aktiviert (stable)

***Ergänzung 13.4.2016:*** Falls der Futro nicht per SSH zu erreichen ist, hilft nur lokal Tastatur und Monitor anschliessen. Über die Konsole SSH neu konfigurieren oder den Konfig-Mode starten.
~~~
uci set "gluon-setup-mode.@setup_mode[0].enabled=1"
uci commit
reboot
~~~
Über einen der LAN-Ports Zugriff via 192.168.1.1 herstellen.
Normalerweise startet der Futro automatisch im Konfig-Mode, solange keine Konfiguration da ist.

Hilfreiche Links:

https://github.com/freifunk-gluon/gluon/wiki/Commandline-administration
https://github.com/oszilloskop/Gluon2Futro
https://wiki.freifunk-mwu.de/w/Howto/Offloader

Anleitung und Futro-USB-Stick jetzt auch auf Github.
https://github.com/oszilloskop/Gluon2Futro/
USB-Stick - Gluon2Futro (Win/Linux/OS X)
Neu: Jetzt auch mit Futro S550-2 Unterstützung!

***6.) Futro S550-2 Umstieg auf Gluon 17.1.4 19.01.2018***

Die bisherige Installation wurde mit dem X86 generic Image (32 Bit) durchgeführt. Dies ist das Universalimage für alle X86 basierten Systeme. In die Images ist die USB Unterstüzung und andere bereits eingebaut. Mit dem fertigen Image auf dem Bootstick kann direkt installiert werden. Es sind dann nur noch die normalen Einstellungen wie für einen Freifunkrpouter vorzunehmen.

Ich habe auf meinem Futro einen ZNC IRC-Bouncer laufen, um im Livechat die letzten Tage lesen zu können. Nach dem Umstieg auf 2017.1.4 konnte ich den ZNC Bouncer nicht installieren. Den Grund fand ich im Lede Repro. Die Packages für X86-Generic waren 2249 Dateien ohne die ZNC Pakete. Die Packeges für X86-64 waren 2318 Dateien. Dort fand ich auch die 56 Pakete für den ZNC wieder.

Umstieg von X86-Generic auf X86-64
Das X86-64 im Futro /tmp Verzeichnis entpacken und mit sysupgrade -F <image> den Futro auf die 64 Bit Version umgestellt. Nach dem Neustart läuft der Futro S550-2 nun mit dem 64 Bit Image. Der ZNC IRC Bouncer konnte nun wie gewohnt mit opkg update; opkg install znc auf dem Futro installiert werden.

