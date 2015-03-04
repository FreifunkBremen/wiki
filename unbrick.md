# Unbrick Anleitung TP-Link
Sobald der Router eine Firmware mit der flaschen Versions- oder Modellnummer abbekommt, hat man schnell einen Briefbeschwerer.

Diese Anleitung konzentriert sich auf das Flashen/Retten des Router über die serielle Schnittstelle.

Vorher sollte man probieren, über den [Failsafe-Mode](http://wiki.openwrt.org/doc/howto/generic.failsafe) den Router zu erreichen.

Beim aktuellsten Modell des 841n(d), der Version 9+ ist es auch möglich, komplett auf Löten zu verzichten. Details finden sich [hier](http://wiki.openwrt.org/toh/tp-link/tl-wr841nd#v9_without_serial).

## Vorbereitungen
Folgende Dinge werden benötigt:
* gebrickter Router
* TTL-auf-USB-Adapter (3.3V Pegel!)
  * ansonsten bei 5V drei Widerstände (ca. 1k+ Ohm)
* Ein LAN-Kabel
* die ***passende*** Firmware für euren Router
* Ein Computer mit ein paar Programmen

Zuerst gilt es die Version und das Modell des Routers herauszufinden. Anschließend darf das Gehäuse des Routers vorsichtig geöffnet werden. Dazu die zwei Schrauben unter den hinteren beiden Füßen lösen und dann den Deckel vorsichtig abhebeln.
Nun gilt es die drei Kontakte der seriellen Schnittstelle ausfindig zu machen. Mit der Suchmaschiene deine Wahl und den Begriffen "PCB Layout + $Routermodell" "ttl pins  + $Routermodell" o.ä. sind diese leicht zu finden. Einige uns schon bekannte Pole befinden sich hier:

Bilder todo

## Serielle Verbindung aufbauen
Sind die Kontaktpunkte auf der Platine ausfindig gemacht, müssen diese mit Pins bestückt werden (ja löten!). Auf diese Pins werden jetzt entsprechend die Pins des TTL-USB-Wandlers gesteckt. 
Dabei erfolgt das Verbinden wie folgt:
* Router TX -> Wandler RX
* Router RX -> Wandler TX
* Router GND -> Wandler GND
* Router VCC nichts mit machen

### Was tun bei 5V Wandler?
Die Pegel des Router laufen nur bei 3.3V, es muss also gewandelt werden. Am einfachsten geht das mit einem Spannungsteiler am RX-Pin des Routers.
Schaltung wie folgt:

### Auf dem Computer
Ist der Wandler richtig am Router angeschlossen muss der Adapter auch in den Computer eingesteckt werden. Mit einem Terminal-Programm öffnen wir die Schnittstelle:
```
picocom -b 115200 /dev/ttyUSB0 
```
Putty, Hyperterminal o.ä. geht natürlich auch.
Die Baudrate von 115200 muss gegebenenfalls auf das Routermodell angepasst werden.

## tftp starten
Der Router soll später das neue Image über FTP herunterladen. Dazu ist es notwendig, dass ein (trivial) FTP-Server installiert und gestartet ist.
Zuerst wird also tftp installiert (tftp-hpa unter Arch).
Gestartet wird es mit
```
systemctl start tftpd.socket
```
(Socket muss eventuell erst erstellt werden)

Standardmäßig ist das Verzeichnis des FTP-Servers unter Arch /srv/tftp/, hier gilt es also das ***passende*** Image hin zu kopieren. 
Mit netstat und ps aux | grep tftp prüfen, ob Server wirklich läuft


# Console öffnen
Sobald der Router startet müssten wir Ausgaben in der Console sehen (er rebootet ständig). Nun hämmern wir die Buchstaben "tpl" in das serielle Fenster, damit wir eine Console bekommen.

## Netzwerkschnittstellen Konfigurieren
Zuerst wird die Netzwerkschnittstelle des Computer mit der des Router verbunden (LAN oder WAN ist afaik egal). Beim Computer legen wir die IP-Adresse statisch auf 192.168.1.1/24 fest.

In der Konsole des Routers legen wir Client und Server Adresse fest:
```
ar7240> 
ar7240> set ipaddr 192.168.1.2
ar7240> set serverip 192.168.1.1
```
## Image Übertragen
Beide Rechner sollten jetzt über Netzwerk miteinander kommunizieren können. Mit dem Befehl:
```
ar7240> tftpboot 0x80000000 tplink.bin
```
versucht der Router das Image mit dem Namen "tplink.bin" vom FTP-Server herunterzuladen. Dieser Name muss also gegebenenfalls angepasst werden.

Der Erfolg wird wie folgt quittiert:
```
done
Bytes transferred = 3932160 (3c0000 hex)
```
Falls es zu keiner Verbindung kommen sollte, Schritte wiederholen. Eventuell gibt es ein Problem mit ARP (ich musste den ARP Eintrag für den Router bei mir auf dem Rechner statis festlegen)
Dazu : 
```
sudo arp -s 192.168.1.2 $MACADRESSEDESROUTER
```
Die Mac-Adresse des Router lässt sich z.B. mit Wireshark herausfinden. Löschen des statischen eintrags mit:
```
sudo arp -d 192.168.1.2
```
## Firmware schreiben
Der nächste Befehl, wichtig hierbei ist der Offset (+0x3x0000, der aus der Erfolgsmeldung übernommen werden muss, vgl. oben).
```
ar7240> erase 0x9f020000 +0x3c0000
```
Es folgt:
```
ar7240> cp.b 0x80000000 0x9f020000 0x3c0000
ar7240> bootm 0x9f020000
```
Nun solltet ihr wieder einen ansprechbaren Router haben!

