Der Aufwand über die KOnsole wäre mir zu groß, deshalb werde ich die Einstellungen über den Kartenleser vornehmen. Über den Kartenleser fällt es mir auch leichter die Konfiguration mit bestehenden Routern zu Vergleichen.

Wir bauen eine Freifunkrouter mit einem Raspberry-Zero-W. Der Zero-W hat WLAN :-)

**- Diese Zeile zeigt an, der Beitrag ist noch im Entwurf!**

## Inhalt

[[_TOC_]]

### Teile-Liste

Die hier angegebenen Links dienen nur als Beispiel und sind meine persönliche Empfehlung. Viele Teile befinden sich normalerweise bereits im Fundus eine Raspi-Bastlers.
- [Zero-W oder WH](https://www.reichelt.de/de/de/raspberry-pi-zero-wh-v-1-1-1-ghz-512-mb-ram-wlan-bt-rasp-pi-zero-wh-p222531.html?&trstct=pos_1&nbc=1)
- [Micro-SD ab 300Mb](https://www.reichelt.de/microsdhc-speicherkarte-32gb-sandisk-mit-adapter-sdsdqm032gb35a-p196654.html?&trstct=pos_7&nbc=1)
- [Netzteil](https://www.reichelt.de/raspberry-pi-netzteil-5-v-2-5-a-micro-usb-schwarz-rasp-nt-25-sw-e-p240934.html?search=raspberry+netzteil)
- [Serielles Interface](https://www.reichelt.de/raspberry-pi-usb-zu-ttl-0-9-m-pl2303hx-rpi-usb-ttl-p150567.html?&trstct=pos_7&nbc=1) oder
  - [LAN-USB-HAT]([https://www.amazon.de/Waveshare-USB-HUB-HAT-Connection/dp/B07T35X4P4/ref=sr_1_9?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=Netzwerkkarte+raspberry+zero+hat&qid=1601205083&quartzVehicle=3443-316&replacementKeywords=netzwerkkarte+raspberry+hat&sr=8-9) oder
  - [LAN-USB-Peitsche](https://www.amazon.de/Micro-Fast-Ethernet-Netzwerkkonverter-Port/dp/B071HS1TF6/ref=sr_1_7?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=Netzwerkkarte+micro+usb+zero&qid=1601204957&quartzVehicle=3443-316&replacementKeywords=netzwerkkarte+micro+usb&sr=8-7)
  - [LAN-Kabel](https://www.reichelt.de/cat-6a-slim-patchkabel-u-ftp-1-5-m-gelb-slim-s6a-1-5-ge-p264786.html?&trstct=pos_9&nbc=1)
- DiskImager z.B. [Win32DiskImager](https://sourceforge.net/projects/win32diskimager/)
- PartedMagic oder Gparted
- ggf. [Gehäuse](https://www.reichelt.de/gehaeuse-fuer-raspberry-pi-zero-transparent-rpiz-case-tr-p223609.html?&trstct=pos_4&nbc=1) 
- ggf. Maus und Tastatur, sowie Monitor und [Micro-HDMI Kabel](https://www.reichelt.de/hdmi-a-stecker-hdmi-micro-d-stecker-4k-2-0-m-delock-84783-p167187.html?&trstct=pos_4&nbc=1) 

### Image vorbereiten
Von der [Freifunk-Imageseite](https://downloads.bremen.freifunk.net/firmware/) die Firmware herunterladen und entpacken. Das Image wird dann mit einem Imager auf die Mico-SD geschrieben, dauert ca. 22 Sekunden. Ggf. mit einem geeigneten Tool die Partitionsgröße anpassen (nicht empfohlen) oder den restlichen Speicherplatz partitionieren und später mounten. 
Den leeren Speicherplatz später zu mounten ist der bessere Weg, da nach einem Sysupgrade die Erweiterng verloren geht. Also bitte immer zusätzliche Partitionen erstellen. 

<img src="https://cloud.ffhb.de/index.php/s/PgrACoTsgj4B2Jq/preview">

Ich bastel ja immer gerne mit Windows und mit Linux und vermische die Arbeiten auch gerne miteinander. Es geht auch nur mit einem Betriebssystem, ich nutze aber gerne beides. 

Das Bild oben zeigt die Ansicht in GParted der Micro-SD Karte mit aufgespieltem Image. 
Mit einem Klick ist der noch freie Platz einer neuen Partition zugeordnet und formatiert.

Schaue ich auf den Inhalt der Karte, sehe ich die Grundstruktur von Raspbian. Damit wäre die Grundkonfiguration ja sofort möglich.
Dieses ist bereits hier im WIKI unter [RaspBerry-Hacks](https://wiki.bremen.freifunk.net/Anleitungen/Raspberry-Hacks) beschrieben.

Speicherkarte in den Zero stecken, Zubehör anstöpseln und booten lassen.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Erster Zugriff - LAN
Der Raspberry hat nun das erste mal gebootet.
LAN Kabel ist angeschlossen, IP auf 192.168.1.2 gesetzt und Ping 192.168.1.1 auf den Raspberry.
Leider kein Erfolg, was ist passiert? Wir konfigurieren einen Freifunkrouter über die gelben Ports, das am Pi angesteckete Interface (Kabelpeitsche oder USB/LAN HAT-Modul) stellt ein blaues WAN Interface zur Verfügung. Eine andere Überlegung ist, die USB Treiber für die Netzwerkkarte sind nicht installaiert, da das Image von einem Pi3 ist und nicht für den Zero.
- Hier fehlt jetzt erst einmal das Vorgehen, wie wird das Interface auf LAN umbiegen.
- - evtl. das OpenWrt Repro auf den freien Speicher clonen
- - die Konfig von einen laufendem Router auf die Speicherkarte schubsen.
- - Speicherkarte über Kartenleser konfigurieren.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Zweiter Zugriff - Seriell
Nachdem den LAN-Zugriff gescheitert ist, gehen wir über die serielle Schnittstelle auf den Pi-Zero.

Zugriff klappt.
<img src="https://cloud.ffhb.de/index.php/s/6JBDP8TkcdcEq7g/preview">
Einstellungen: 115200 8 N 1 auf dem gefundenen COM Port.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Node zurücksetzen

Wenn man mal etwas kaputt-konfiguriert hat lässt sich der Zustand "frisch-geflash" wie folgt wiederherstellen.

    Der Befehl firstboot setzt alle Konfigurationen zurück.
    Anschließend startet man mit dem Befehl reboot neu.

Der Node befindet sich jetzt im wieder im Config-Mode, wie beim ersten Start.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Konfiguration
Solange der Zero nicht konfiguriert ist, Funkt er nicht. Der Zugang erfolgt über die serielle Schnittstelle oder über ein angeschlossenes LAN-Interface. Wenn der Zero eher voll verkabelt ist, also Maus Monitor Tastatur, kann er auch darüber konfiguriert werden.
Ich möchte mich hier auf Seriell, WEB-Interface und SSH beschränken.

#### Konfiguration Serielles Interface
Ich sammel hier mal alle Punkte, die mit notwendig erscheinen.
1. Wie ist jetzt mein Konfigsatus?
~~~
cat /etc/config/gluon-setup-mode
config setup_mode
       option enabled '0'
       option configured '0'
~~~
configured = '0', also unkonfiguriert. Das ändern wir schon mal auf fertig. Reboot erst ganz zum schluss und mit vi in  /etc/dropbear/authorized_keys den eigenen SSH Key einfügen.

2. Konfigurieren über serielle Konsole.
Daten entsprechend Anpassen.

~~~
uci set gluon-setup-mode.@setup_mode[0].enabled=0
uci commit gluon-setup-mode
uci set system.@system[0].hostname='FFHB-Raspi-Zero-WH-01'
uci commit system
uci set gluon-node-info.@owner[0]='MaxMustermann'
uci set gluon-node-info.@owner[0].contact='MustermannBremen@bremen.freifunk.net'
uci set gluon-node-info.@location[0]='location'
uci set gluon-node-info.@location[0].share_location='1'
uci set gluon-node-info.@location[0].latitude='53.086859171'
uci set gluon-node-info.@location[0].longitude='8.815151428'
uci commit gluon-node-info
reboot
~~~

3. Schritt 1 Wiederholen.
Der Eintrag option configured muss auf 1 stehen. Ggf. die Datei /etc/config/gluon-setup-mode mit vi editieren.
Neu booten, jetzt sind auch über ifconfig alle Interfaces zu sehen.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Statische IP WAN
Set a static IPv4 for the WAN-Port
~~~
uci set network.wan.proto=static
uci set network.wan.ipaddr=192.168.1.1
uci set network.wan.netmask=255.255.255.0
uci set network.wan.gateway=192.168.1.1
uci commit network
/etc/init.d/network restart
~~~

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

