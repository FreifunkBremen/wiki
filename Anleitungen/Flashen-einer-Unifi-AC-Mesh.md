	
#### Ubiquiti Unifi AC-Mesh / AC-Lite flashen und Back to Stock

Flashen einer Unifi AC-Mesh / AC-Lite unter Linux Mint/Ubuntu:

Vor dem flashen muss unbedingt darauf geachtet werden das die vorinstallierte original Firmware 3.7.58, 3.8.3 oder 4.0.21 von Ubiquiti installiert ist!
Ubiquiti Firmware Versionen kleiner 3.7.58 kann beim aufspielen und Updaten mit Freifunk Firmware (ab Version 0.9.4 / GLUON 2017.1.7) zum Soft-Brick führen!

Bei einigen Ubiquiti Firmware Versionen ist kein „MTD“ dabei und ein flashen wird so unmöglich.
Dies sollte vor einem Downgrade ausprobiert werden, ob "MTD" vorhanden ist.

Auf dem Gerätekarton steht ein Testdatum, Geräte bis 1.4.2019 sollten die richtige Firmware haben.
Die richtige Firmware von Ubiquiti herunterladen (3.7.58 / 3.8.3)
https://www.ubnt.com/download/unifi/unifi-mesh/uap-ac-m
Dann auf „SEE PAST FIRMWARE“ die „Unfi Firmware 3.7.58 for UAP-AC-LITE/M/…/… “ auswählen und herunterladen.

Der Reihe nach: 

## Inhalt:
[1.) Firmwareversion ermitteln und  flashen:](#inhalt_1-firmwareversion-ermitteln-und-flashen)

[2.) Freifunk Image aufspielen](#inhalt_2-freifunk-image-aufspielen)

[]()

### 1.) Firmwareversion ermitteln und flashen:

Das LAN Kabel ist mit dem Ubiquiti PoE Adapter verbunden.
Netzwerkeinstellung des PC/Laptop auf manuell (statisch) stellen – 192.168.1.2/255.255.255.0

Mit original Firmware ist die Unifi per SSH unter der IP 192.168.1.20 erreichbar.

Anmeldung mit…

    ssh ubnt@192.168.1.20  =>Passwort ubnt



Im Idealfall sieht die Ausgabe mit Angabe der vorinstallierten Firmware dann so aus. Wenn nicht, bitte unbedingt ein up/downgrade durchführen.

    BZ.v3.7.58#
    

~~~
BZ.v3.7.58# mtd
Usage: mtd [<options> ...] <command> [<arguments> ...] <device>[:<device>...]

The device is in the format of mtdX (eg: mtd4) or its label.
mtd recognizes these commands:
        unlock                  unlock the device
        refresh                 refresh mtd partition
        erase                   erase all data on device
        write <imagefile>|-     write <imagefile> (use - for stdin) to device
        jffs2write <file>       append <file> to the jffs2 partition on the device
Following options are available:
        -q                      quiet mode (once: no [w] on writing,
                                           twice: no status messages)
        -n                      write without first erasing the blocks
        -r                      reboot after successful command
        -f                      force write without trx checks
        -e <device>             erase <device> before executing the command
        -d <name>               directory for jffs2write, defaults to "tmp"
        -j <name>               integrate <file> into jffs2 data when writing an image
        -p                      write beginning at partition offset
        -F <part>[:<size>[:<entrypoint>]][,<part>...]
                                alter the fis partition table to create new partitions replacing
                                the partitions provided as argument to the write command
                                (only valid together with the write command)

Example: To write linux.trx to mtd4 labeled as linux and reboot afterwards
         mtd -r write linux.trx linux

BZ.v3.7.58#
~~~
Wenn die Ausgabe so aussieht, kann die Freifunkfirmware installiert werden.	Ohne MTD bitte eine Firmware mit MTD aufspielen, weiter bei Punkt 3.
	

### 2.) Freifunk Image aufspielen
	
Auf eurem Rechner/Laptop, dass “sysupgrade-Image“ der „Unifi AC-Mesh/Lite“ eurer Domäne, (der einfachheitshalber) in „firmware.bin“ umbenennen und per scp ins /tmp Verzeichnis der AC-Mesh/Lite kopieren.
cd /home/USER/PFAD/ZUR/FIRMWARE.BIN

    scp firmware.bin ubnt@192.168.1.20:/tmp/ =>Passwort ubnt

Ein neues Terminal öffnen und mit

    ssh ubnt@192.168.1.20

einloggen.

In das temporäre Verzeichnis wechseln

    cd /tmp

Dann folgende Zeilen exakt so anwenden!

    mtd write /tmp/firmware.bin kernel0
    mtd write /tmp/firmware.bin kernel1

Jetzt sollte noch der Bootselect geschrieben werden.

Die MTD Partition mit dem Label „bs“ ausfindig machen.

    cat /proc/mtd | grep bs

Als Ausgabe erscheint:

    BZ.v3.7.58# cat /proc/mtd | grep bs
    mtd4: 00020000 00010000 „bs“

und ein Nullbyte an den Anfang der Partition schreiben.
~~~
    dd if=/dev/zero bs=1 count=1 of=/dev/mtdX **<-x Anpassen**
~~~
Die gesuchte Partition ist vor dem reboot /dev/mtd4.

Nach dem reboot, oder wenn der Bootselect nachträglich geschrieben wird ist es /dev/mtd7. 

Das sollte aber durch den obigen Schritt (cat /proc/mtd | grep bs) sichergestellt werden. Der Befehl lautet dann am Ende statt mtdX, also mtd4 oder mtd7.

Ab den neueren GLUON Versionen (2017.1.x) kann der Bootselect auch aus der Ferne gefixt werden. Die Anleitung ist hier kein Bestandteil.

Mit dem anschließendem Befehl

    reboot

wird die AC-Mesh neu gestartet. Nach dem ersten Neustart gelangt man dann direkt in den Config-Mode.
Der Config-Mode kann auch manuell erreicht werden wenn man während des Betriebes für ca. 12 Sekunden der Resetknopf drückt und dann los lässt. 
Bei diesem Gerät wird während diesem Vorgang nichts weiter angezeigt, erst ein paar Sekunden später blinkt die LED weiß!
Der Access Point ist in der Standardkonfiguration auf volle Leistung eingestellt (20dBm).
Diesen Wert sollten wir auf mindestens 17 dBm (oder 16 dBm) ändern. Damit bewegen wir uns im zulässigen Bereich und es gibt weniger Probleme mit der Airtime.


Der Router befindet sich nach dem ersten Neustart automatisch im Konfigurationsmodus.
Weiterhin verteilt der Router in der Zeit über DHCP IP-Adressen, so das der PC eine passende Adresse erhält.

Startet nun die Konfiguration über: http://192.168.1.1 und die Konfiguration kann vorgenommen werden.
 
### 3. Back to Stock - Downgrade unter Linux Mint-Ubuntu

Vorraussetzungen:
Das LAN Kabel ist mit der Unifi AC Mesh PoE Adapter und deinem Laptop verbunden.
Netzwerkeinstellung des PC/Laptop auf manuell (statisch) stellen – 192.168.1.2/255.255.255.0
Der TFTP Client ist installiert.

Vorbereitung:
TFTP Client unter Linux Mint/Ubuntu installieren.
Terminal öffnen…

    sudo apt install tftp

…mit Passwort bestätigen, fertig!

Die richtige Firmware von Ubiquiti herunterladen (3.7.58), fall noch nicht geschehen.
https://www.ubnt.com/download/
Oben rechts suchen nach „Unifi AC-Mesh“ dann auf  „SEE PAST FIRMWARE“ die „Unfi Firmware 3.7.58 for UAP-AC-LITE/M/…/… “ auswählen und laden.

Die heruntergeladene Firmware in „firmware.bin“ umbenennen und unter /home/USER/“ bzw. in das konfigurierte Tftp Verzeichnis abspeichern.

Die Unifi Stromlos machen, in dem Du das PoE Kabel am Adapter entfernst.
Den LAN Port des PoE Adapter mit deinem Laptop verbinden.

Das Terminal öffnen und

    tftp

eingeben.

Den Reset Button drücken und halten.
Die Unifi AC-Mesh mit dem PoE Kabel am Adapter verbinden.
Halte den Reset Button solange gedrückt, bis die LED’s abwechselnd blau-weiß blinkt (ca.20 Sekunden).
Jetzt fährt die Unifi in den Recovery Mode und blinkt weiterhin abwechselnd blau-weiß.

Dann jede Zeile einzeln eintippen.

    connect 192.168.1.20
    binary
    rexmt 1
    timeout 60
    put firmware.bin

Als Ausgabe erscheint…
Sent x bytes in y seconds

Nach ein paar Minuten bootet die Unifi selbstständig mit der originalen Firmware.

 

 
### 3. Back to Stock / Downgrade unter Windows 

Die Datei mit einem SCP-fähigen Program (z.B. WinSCP) auf der AC Mesh ablegen.

Für den Login die gleichen Daten wie für SSH verwenden (ubnt@192.168.1.20 und PW: ubnt).
Wichtig: Protokoll SCP auswählen, SFTP funktioniert nicht.

Verzeichnis /tmp anwählen und dort die Datei ablegen, danach zu fwupdate.bin umbenennen.

Danach wieder per SSH (mit z.B. Putty) auf dem Gerät einloggen und folgendes ausführen:

    syswrapper.sh upgrade2 &

Quelle: https://help.ubnt.com/hc/en-us/articles/204910064-UniFi-Changing-the-Firmware-of-a-UniFi-Device#local%20upgrade

Danach startet das Gerät neu, dann erneut einloggen und weiter mit Punkt 2. um die Freifunk Firmware zu installieren.

**Diese Anleitung ist wie immer ohne Gewähr. Für Anregungen und Tipps immer offen.**
