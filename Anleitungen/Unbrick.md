# Unbrick Anleitung TP-Link
Sobald der Router eine Firmware mit der falschen Versions- oder Modellnummer abbekommt, hat man schnell einen Briefbeschwerer.

Diese Anleitung konzentriert sich im ersten Teil auf das Flashen/Retten des Router über die serielle Schnittstelle, im zweiten Teil über Failsafe per TFTP.

Vorher sollte man probieren, über den [Failsafe-Mode](http://wiki.openwrt.org/doc/howto/generic.failsafe) den Router zu erreichen.

Beim aktuellsten Modell des 841n(d), der Version 9+ ist es auch möglich, komplett auf Löten zu verzichten. Details finden sich [hier](http://wiki.openwrt.org/toh/tp-link/tl-wr841nd#v9_without_serial).


## Hinweise:
**Warum TFTP nicht klappt.** Der Router schaltet die LAN Schnittstelle ein und schaut auf einer von diesem Modell festgelegten IP-Adresse ob ein Modellspezifisches Image geladen werden kann. 
Dieses erfolgt oft so schnell, dass der angeschlossene PC dies nicht mitbekommt. Lösung: einen kleinen Switch dazwischen schalten, dieser hält den PC Online und reagiert deutlich schneller auf den Uplink des Routers.

**Dauerbootschleife:** Auf dem Router sind zwei Images. Das Erste ist der uboot Bootloader, der am Ende des Startvorgangs das zweite Image anspring und die Applikation startet. In seltenen Fällen kommt es vor, das während der Installation eines neuen Images, der uboot Bootloader hinter den ersten geschrieben wird. uboot springt an eine feste Adresse im Speicher. Trifft es dort auf den neuen uboot, kommt es zur Schleife. Hier hilft ein gestripptes Image ohne uboot am Anfang.



[Teil 1 unbrick seriell](#inhalt_Vorbereitungen)

[Teil 2 unbrick TFTP Archer C7](#inhalt_Unbrick Anleitung TP-Link Archer C7 v2)

##Vorbereitungen

Folgende Dinge werden benötigt:
* gebrickter Router
* TTL-auf-USB-Adapter (3.3V Pegel!)
  * ansonsten bei 5V drei Widerstände (ca. 1k+ Ohm)
* Ein LAN-Kabel
* die ***passende*** Firmware für euren Router
* Einen Computer mit ein paar Programmen

Zuerst gilt es die Version und das Modell des Routers herauszufinden. Anschließend muss das Gehäuse des Routers vorsichtig geöffnet werden. Dazu die zwei Schrauben unter den hinteren beiden Füßen lösen und dann den Deckel vorsichtig abhebeln.
Nun gilt es die drei Kontakte der seriellen Schnittstelle ausfindig zu machen. Mit der Suchmaschine deiner Wahl und den Begriffen "PCB Layout + $Routermodell" "ttl pins  + $Routermodell" o.ä. sind diese leicht zu finden. Einige uns schon bekannte Pole befinden sich hier:

Platine des 741v2:
<img src="https://jel.to/ff_pics/741v2-1.jpg" title="PCB 741v2" />

Platine des 841v7:
<img src="https://jel.to/ff_pics/841ndv7.2.jpg" title="PCV 841v7" />

...mehr folgen

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

<img src="https://jel.to/ff_pics/spannungsteiler.jpg" title="Spannungsteiler" />

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

### Für Unbrickprofis

Wer die Unbrickaktion des öfteren durchführt, sollte sich z.B. in der Bucht einen USB-TTL Adapter für ca. 1€ zulegen.


#Unbrick Anleitung TP-Link Archer C7 v2

## Vorbereitungen
Folgende Dinge werden benötigt:
* gebrickter Router
* Zwei LAN-Kabel
* Ethernet Switch
* die ***passende*** Firmware für euren Router
* Einen Computer mit ein paar Programmen

## Vorgeschichte
Fast alle Router haben einen failsaverecover. Der schreibgeschützte Bootloader des Routers versucht kurz eine Verbindung von **LAN1** ( erster gelbe Port) zu einem tftp Server herzustellen und ein entsprechendes recover.bin zu laden. Dazu hat der Router kurz die IP Adress **192.168.0.86** und schaut auf die Serveradresse **192.168.0.66**, sofern ein **Link** vorhanden ist.

## Recovery Image
Für den TP-Link Archer C7 v2 auf der Herstellerseite das passende Image herunterladen und entpacken. Das entpackte Binary in ArcherC7v2_tp_recovery.bin umbenennen.
Image z.B. hier: https://static.tp-link.com/Archer%20C7(EU)_V2_170803.zip
oder hier: https://static.tp-link.com/res/down/soft/Archer_C7(EU)_V2_160616.zip
Für andere Modelle ein entsprechendes Image suchen.

## tftp
Über den tftp Server wird die Firmware auf das Gerät gespielt und das sollte automatisch passieren. Zuerst eine passende tftp Version installieren, die gibt es hier: http://tftpd32.jounin.net/tftpd32_download.html

Bild: ![cp210-UART](https://cloud.ffhb.de/index.php/s/HS65Ac4Ytes44aw/download)

[CP210-UART-Treiber](https://www.silabs.com/products/development-tools/software/direct-access-drivers)

Der tftp Server soll an eurer LAN Schnittstelle lauschen, das macht er jedoch nur, wenn die LAN Schnittstelle auf **"up"** ist. (Ist diese auf up, dann ist es ausreichend, wenn er auf der Loopbackadresse 127.0.0.1 läuft). Also jetz einen Link zum Ethernet Switch herstellen. 

(Anmerkung: Der Router bootet schneller, als das der PC das LAN Interface einschalten kann. Der Router sucht bereits das Image, bevor die Verbindung zum TFTP aufgebaut ist. Bei einigen Schnittstellenkarten kann das Interface manuell auf **"up"** gestellt werden, dann wird kein Switch benötigt.)

Jetzt kann die LAN Schnittstelle auf **192.168.0.66** eingestellt werden.
Durch die Verbindung zum Switch ist unser LAN Port auf up und einsatzbereit.
Der TP-Link Archer C7 v2 schaut bei einem Reset kurz auf dieser IP nach, ob es ein Image für ihn gibt.
tftp Server auf die LAN Schnittstelle setzen und in das Serververzeichnis die Datei "ArcherC7v2_tp_recovery.bin" hineinkopieren.


## Recover Teil 1
Den Port 1 (erster gelber Port) des TP-Link Archer C7v2 und den den LAN Port des PC mit dem Switch verbinden.
Den Reset-Knopf ca. 5-10 Sekunden gedrückt halten. Wenn die Verbindungslampe vom Switch leuchtet (Kabelverbindung zum Archer), ~~dann loslassen~~ grückt halten, bis das Recyclingsymbol ganr rechts leuchtet. Sofort startet der Imagedownload. Ist dieses abgeschlossen, bootet der Archer und ist im Originalzustand. Ggf. wiederholen.
Der Zugriff erfolgt über 192.168.0.1 admin/admin. 

Bild: ![tftp-Download](https://cloud.ffhb.de/index.php/s/3RRwy3CsBxcHJyg/preview)

Wir öffnen die Einstellung sysupgrade im Router und kopieren unser Freifunkimage drauf. Ist unser PC noch angeschlossen, das LAN Interface von 192.168.0.66 jetzt auf 192.168.1.66 ändern.

## Recover Teil 2
Diesen Teil benötigen wir, wenn vorhergender Abschnitt fehlschlägt und der Router immer noch im Dauerbootzustand ist.

Letzter Versuch mit Recover Teil 1
Es gibt speziell gepatchte Firmware ohne Bootloader für TP-Link Router, hier zur finden: http://www.friedzombie.com/tplink-stripped-firmware/

Wieso stripped? Normalerweise erkennt der Bootloader bei der Installation des Images, das dieses ebenfalls einen Bootloader aufweist und überspringt diesen bei der Installation. Ist dies nicht der Fall, haben wir einen zweiten Bootloader direkt nach dem Ersten mit der Einsprungadresse des Zweiten. Eine prima Bootschleife. Ein gestripptes Image ist quasi nur die Applikation ohne Bootloader.

Wenn das nicht klappt, geht es hier weiter.
Jetzt ist Löten angesagt. Der Router benötigt eine serielle Schnittstelle, bzw, wir führen die vorhandene aus dem Gerät heraus.
Keine Panik, es werden nur 3 Kabel angeschlossen.

Je nach Material gibt es verschiedene Möglichkeiten, Pfostenleiste für Steckbare Kabel oder Kabel mit Steckern und Pins oder nur einfache Drähte. Den USB-TTL Wandler anschliessen. Eine TX/RX Vertauschung sollte noch möglich sein. Viele Bilder zeigen RX und TX vertauscht an.

Der USB Wandler benötigt häufig einen Treiber, der sich durch Google leicht finden lässt. 

Terminal Programm wie TeraTerm etc. starten. Wenn lesbare Ausgaben zu sehen sind, Bootvorgang durch Eingabe von TPL (klein) also tpl unterbrechen. Ist ein Eingabepromt vorhanden, das Image wie folgt einspielen. Hier gleich das gestrippte.

~~~
tftp 0x81000000 Archer-C7-V2-FW0.0.3-stripped.bin
erase 0x9f020000 +f80000
cp.b 0x81000000 0x9f020000 0xf80000
reset
~~~

Jetzt sollte der Router wieder mit den TP-Link Zugangsdaten erreichbar sein. Freifunk factory Image drauf, konfigurieren und frohes Freifunken.

In einigen Freifunk/OpenWRT/LEDE Foren wird ausführlich über dieses Thema diskutiert. Auf diesem Wege soll auch ein Freifunk factory Image direkt geladen werden können. Hier ein Link zu diesem Thema: https://forum.freifunk.net/t/router-recovery-tftp-pushbutton-und-ttl-serial-recovery/8691


### Unbrick CPE/WBS

Gleiche Anleitung wie oben.
Die IP Adresse des PC ist auf **192.168.0.100** einzustellen.
Das Faktory Image wird umbenannt auf **"recovery.bin"**
Login auf der CPE/WBS mit **192.168.0.254** und admin/admin, dann muss ein neues PW gesetzt werden. Der Upload der Freifunksoftware klappt mit der CPE/WBS Option Restore. Nach dem automatischen Reeboot klappt der Zugang wie bei jedem anderen Freifunkrouter mit **192.168.1.1**. Daten eingeben, neu Starten, fertig.
