### Flashen einer FritzBox 4040.
Die folgenden Infos wurden aus verschiedenen Foren etc. zusammengetragen und sind mit Stand 12/2020 geprüft.

- Anzumerken ist: Das Flashen einer FritzBox ist nichts für Anfänger. Bitte informiert euch bei Leuten, die bereits die 4040 geflasht haben. Kommt gerne auf eines unserer Treffen, auch per Videokonferenz, dort sind immer ein paar flashen dabei.

Eine Anleitung aus den Erfahrungen aus 12/2020 ausgeführt mit Linux:

1.  Firmware herunterladen: https://downloads.bremen.freifunk.net/firmware/stable/other/
    Diese Datei Verwenden: gluon-ffhb-2019.1.2+bremen3-avm-fritz-box-4040-bootloader.bin
2.  Python3-Skript herunterladen https://raw.githubusercontent.com/freifunk-darmstadt/fritz-tools/master/fritzflash.py
3.  Beide Dateien im selben Verzeichnis ablegen.
4.  WLAN am PC abschalten
5.  LAN-Schnittstelle des PC auf feste IP einstellen: 192.168.178.2 Subnetzmaske: 255.255.255.0 Gateway: 192.168.178.1
6.  PC per LAN-Kabel mit der FritzBox (LAN 1) verbinden.
7.  Verzeichnis mit den beiden Dateien im Terminal öffnen.
8.  Befehl eingeben:
    python3 fritzflash.py
    Enter
9.  FritzBox ans Stromnetz anschließen.
10. Anweisung im Terminal folgen.
11. LAN-Schnittstelle des PC auf DHCP zurückstellen.
12. Warten bis LAN wider aktiv ist dann 192.168.1.1 aufrufen.
13. Den Router im Browser Webinterface einrichten (wie bei allen neuen Knoten).

### Konfigurationsmodus/Fritzbox 4040 

Der Konfigurationsmodus der FB 4040 wir wie folgt erreicht:
Im normalen Betrieb die WPS-Taste drücken; nach ca. 10-15 Sekunden (Sobald einmal alle Lampen aufleuchten loslassen ) daraufhin erfolgt ein Reset des Routers und ein neustart im Konfigurationsmodus.

Der Router darf dabei nicht vom Strom getrennt werden.

### Informationsquellen Firmwareinstallation/Fritzbox 4040 
Original von https://wiki.freifunk-franken.de/w/Firmwareinstallation/Fritzbox_4040

Freifunk Darmstadt hat eine gute Anleitung für Linux, Windows, MacOS veröffentlicht: 
https://fritz-tools.readthedocs.io/de/latest/ 

**Windows:**

Für Windows gibt es eine Powershell Anwendung: https://github.com/adrianschmutzler/evaFFF 

### Auch Interessant: Wichtige Infos:

* Bei der Fritzbox 4040 sind alle vier gelben Ports entweder Mesh oder Client, denn diese hängen alle intern an einem Hardware-Switch und werden nicht als VLAN an den Switch angebunden, somit sind die Ports nicht aufteilbar. Dies ist vermutlich auch in Zukunft nicht möglich.

   * * eth0 - gelbe Buchsen - Standard ist Mesh, kann zu Client umgeschaltet werden
   * * eth1 - blaue Buchse - Uplink/VPN
    
* Installation geht nicht, probiert mal die aktuellste FW 4.1.0er. Die sollte eigentlich gehen. Falls die nicht klappt, musst du ganz auf die 4.0.1er zurück und dann mit sysupgrade auf 4.1.0 aktualisieren. _Achtung:_ Die 4.0.3er ist kaputt, was das Bootloader-Image für die 4040 angeht.

* Das Flashen der FB 4040 mit der Anleitung unter https://fritz-tools.readthedocs.io/de/latest/ und der aktuellen Firmware sollte auch problemlos funktionieren.

* je nach Tageszeit liegt der Upload bei 20-25 MBit/s (ziemlich unabhängig davon, ob Mesh-VPN-Verschlüsselung aktiviert ist)

* Stromverbrauch ist laut seiner Messung erfreulich niedrig: ca. 2,5 Watt