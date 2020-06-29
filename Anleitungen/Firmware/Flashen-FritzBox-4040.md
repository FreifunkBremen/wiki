### Flashen einer FritzBox 4040.
Die folgenden Infos wurden aus verschiedenen Foren etc. zusammengetragen und sind mit Stand 6/2020 nicht verifiziert.

- Anzumerken ist: Das Flashen einer FritzBox ist nichts für Anfänger. Bitte informiert euch bei Leuten, die bereits die 4040 geflasht haben.

Eine Anleitung behauptet, so funktioniert es definitiv für jede Box:

1.  PC fest auf 192.168.178.2 Subnet 255.255.255.0 einstellen
2.     fritzflash.py imagename.bin ausführen, noch NICHT enter drücken
3.     Strom auf die Fritzbox 4040 geben und danach enter drücken in fritzflash.py
4.     Auch falls eure Box jetzt aus irgendwelchen Gründen nicht automatisch gefunden wird, wurde die IP vom Bootloader auf 192.168.178.1 gesetzt durch das Script
5.     Daher nochmal vom Strom trennen
6.     fritzflash.py --ip 192.168.178.1 imagename.bin ausführen
7.     Strom auf die Fritzbox 4040 geben und danach enter drücken in fritzflash.py
8.     Jetzt sollte er flashen und alles ist gut.

fritzflash.py wird eiter unten erläutert.


### Firmwareinstallation/Fritzbox 4040 
Original von https://wiki.freifunk-franken.de/w/Firmwareinstallation/Fritzbox_4040

Freifunk Darmstadt hat eine gute Anleitung für Linux, Windows, MacOS veröffentlicht: 
https://fritz-tools.readthedocs.io/de/latest/ 

**Hier die Zusammenfassung:**

1.     Firmware herunterladen: https://downloads.bremen.freifunk.net/firmware/stable/other/
2.     Python3-Skript herunterladen https://raw.githubusercontent.com/freifunk-darmstadt/fritz-tools/master/fritzflash.py
3.     LAN-Schnittstelle des PC auf feste IP einstellen: 192.168.178.2 Subnetzmaske: 255.255.255.0
4.     PC per LAN-Kabel mit der FritzBox (Buchse 1) verbinden.
5.     Python3-Skript auf dem PC ausführen.
6.     FritzBox ans Stromnetz anschließen.
7.     Das Python3-Skript die Arbeit erledigen lassen.
8.     LAN-Schnittstelle des PC auf DHCP zurückstellen.
9.     Mit der Box per WLAN verbinden [per LAN-Kabel vermutlich nicht möglich]
10.     Diesen Link öffnen: https://[fdff::1]
11.     Den Router im Browser Webinterface einrichten (wie bei allen neuen Knoten).

Für Windows gibt es eine Powershell Anwendung: https://github.com/adrianschmutzler/evaFFF 

### Auch Interessant:
Bei der Fritzbox 4040 sind alle vier gelben Ports entweder Mesh oder Client, denn diese hängen alle intern an einem Hardware-Switch und werden nicht als VLAN an den Switch angebunden, somit sind die Ports nicht aufteilbar. Dies ist vermutlich auch in Zukunft nicht möglich.

    eth0 - gelbe Buchsen - Standard ist Mesh, kann zu Client umgeschaltet werden
    eth1 - blaue Buchse - Uplink/VPN
    
Installation geht nicht, probier mal die aktuellste FW 4.1.0er. Die sollte eigentlich gehen. Falls die nicht klappt, musst du ganz auf die 4.0.1er zurück und dann mit sysupgrade auf 4.1.0 aktualisieren. Die 4.0.3er ist kaputt, was das Bootloader-Image für die 4040 angeht.


Ich kann bestätigen, dass flashen der FB 4040 mit der Anleitung unter https://fritz-tools.readthedocs.io/de/latest/ und der aktuellen Firmware kein Problem ist.


Wiki biite für Bremen aktualisieren.