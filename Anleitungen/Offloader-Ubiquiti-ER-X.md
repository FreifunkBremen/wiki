## Gluon auf UBNT EdgeRouter X und X-SFP

Einige Erfolge und die tollen verfügbaren Anleitungen, sollen hier Mut machen, die kleinen Leistungsstarken Ubiquiti Edgerouter ER-X als Offloader einzusetzen.
Warum Offloader? Werden mehrere Freifunkrouter verwendet, ist es sinnvoll, dass nicht alle Router ihren eigenen VPN Tunnel aufbauen. Der Offloader übernimmt die Verschlüsselung und mesht über die LAN Ports mit den Freifunkroutern, das gibt ein deutlich schnelleres Netz bei geringen Kosten.

### Was spricht für dieses Modell Ubiquiti EdgeRouter X (ER-X) / (ER-X SFP)?
- Der ER-X besitzt einen Gigabit Port mit Passiv PoE Eingang (24 V, eth0) und kann so ohne Netzteil betrieben werden. Weiterhin gibt es einen Gigabit Port mit Passiv PoE Ausgang (24 V, eth4) um einen Access Point anzuschließen. Daneben noch drei weitere Gigabit Ports zur weiteren Verwendung (eth1/2/3).
- Bei Verwendung eines 24V Netzteils, kann der ER-X auf Port 4 auch direkt POE ausgeben.
- Abmessungen: 110 x 75 x 22
- Prozessor:   Dual-Core 880 MHz
- Geringer Stromverbrauch: 5W, 12V Netzteil.
- Der ER-X SFP hat neben dem SFP-Modul und dem 24V Netzteil auf allen Ports passiv POE 24V.

### Diverse nützliche Links:
- https://www.ubnt.com/edgemax/edgerouter-x/
- https://dl.ubnt.com/datasheets/edgemax/EdgeRouter_X_DS.pdf
- https://www.ubnt.com/edgemax/comparison/ (Vergleich der Modelle)
- https://www.heise.de/preisvergleich/ubiquiti-edgerouter-er-x-a1271798.html
- https://wiki.funkfeuer.at/wiki/Hardware/EdgeRouter_X
- https://wiki.funkfeuer.at/wiki/Hardware/EdgeRouter_X-SFP

### Links zu Anleitungen:
- https://github.com/oszilloskop/UBNT_ERX_Gluon_Factory-Image (Empfehlenswert)
- https://www.freifunk-winterberg.net/die-nutzung-von-ubiquiti-edgerouter-x-als-freifunk-offloader/
- https://wiki.openwrt.org/toh/ubiquiti/ubiquiti_edgerouter_x_er-x_ka
- https://community.ubnt.com/t5/EdgeMAX-Updates-Blog/EdgeMAX-EdgeRouter-X-X-SFP-bootloader-update/ba-p/1472216

### Links zu Firmware:
- https://downloads.openwrt.org/snapshots/trunk/ramips/mt7621/openwrt-ramips-mt7621-ubnt-erx-squashfs-sysupgrade.tar
- https://dl.ubnt.com/firmwares/edgemax/v1.10.x/ER-e50.v1.10.6.5112725.tar
- https://downloads.bremen.freifunk.net/firmware/stable/sysupgrade/gluon-ffhb-2017.1.8+bremen1-ubnt-erx-sysupgrade.tar
- https://downloads.bremen.freifunk.net/firmware/all/2017.1.8+bremen1/sysupgrade/gluon-ffhb-2017.1.8+bremen1-ubnt-erx-sfp-sysupgrade.tar

Frohes Freifunken.


## Unbrick UBNT EdgeRouter X und X-SFP

Wenn der Router einmal gebrickt ist, also es besteht kein Zugriff mehr über die externen Schnittstellen, hier im folgenden einige Rettungsversuche.


### Freifunkimage verbastelt? Zugriff über SSH

Unter /etc/confog/network ist ein Abschnitt, der die Interne Adresse beschreibt. Der Zugriff auf das Gerät erfolgt über einen Client-Port oder im Konfig-Modus nach einem langen Reset. Die local ip ist/kann je nach Freifunk-Community unterschiedlich sein.

~~~
config interface 'local_node'
	option ifname 'local-node'
	option ipaddr '10.196.0.127/17'
	option ip6addr 'fd2f:5119:0f2c::127/128'
	option ip6deprecated '1'
	option proto 'static' 
~~~

SSH starten und mit root@fd2f:5119:0f2c::127 verbindung aufnehmen.
Wenn es keine Verbindung gibt, müssen wir die serielle Schnittstelle verwenden. 

### Freifunkimage verbastelt? Zugriff über die serielle Schnittstelle
Ich habe durch diverse Konfigurationen den Router unbrauchbar gemacht.
Keine Panik, es gibt die serielle Schnittstelle im Router. Auf der rechten Seite am Rand sind 4 Pins eingelötet an der ein Seriell-USB Adapter angeschlossen werden kann.
- Router öffnen: Auf der Rückseite sind zwei kleine Kreuzschrauben, die die beiden Gehäusehälften zusammenhalten. Im SFP Modell zuerst das SFP entfernen. Schrauben herausnehmen und Gehäuse aufklappen.
- Seriellen Adapter Anschliessen. Ich verwende hier ein Raspberry-PI Seriell-USB Kabel. z.B. dieses: https://www.conrad.de/de/raspberry-pi-usb-kabel-usb-rb-ttl-raspberry-pi-409202.html andere TTL Adapter funktionieren aber auch.
- Herstellerbeschreibung des Raspberry-Pi-Kabels: "Mit diesem Kabel verbinden Sie Ihren Raspberry PI ganz einfach mit einem PC System. Gleichzeitig stellt das Kabel über den USB Port des PC 5V bei 500mA zur Verfügung, so dass Sie kein separates Netzteil verwenden müssen. Der in dem Kabel integrierte serielle PL2303HX Chip sorgt dafür, dass beide Geräte miteinander Daten austauschen können. Hierbei werden Windows XP, Vista, 7 und 8 unterstützt. Belegung der PIN Stecker: rot = Power +5V / schwarz = Ground / weiß = RX / grün = TX"
- Die PIN Belegung der seriellen Schnittstelle des ER-X ist beschrieben unter: https://openwrt.org/toh/ubiquiti/ubiquiti_edgerouter_x_er-x_ka#poe_out_on_edgerouter_x
- ER-X: PIN zum Reset-Knopf: Ground, TX, RX, 3,3V, der zur ETH 5 Buchse zeigt.

![Bild: UBNT-ERX-SFP_Seriell](https://cloud.ffhb.de/index.php/s/ZR4opcNa7xrzyqe/download)

Wer den Bootvorgang aufzeichnen möchte, verbindet den USB Adapter vor Inbetriebnahme mit dem PC und startet ein Terminal Programm. Unter Windows z.B. TerTerm und LOG einschalten. Der serielle Adapter hat sich bei mir unter COM 8 installiert. (Das Windows Terminal kann original nur bis COM 4). Geschwindigkeit: 57600 / 8 / N / 1 einstellen. Router Einschalten.

Wenn am Ende des Bootvorgangs ungefähr folgende Ausgabe übrig bleibt, dann ist der Router am Leben und alle Einstellungen können über die Konsole geändert werden.

~~~

BusyBox v1.25.1 () built-in shell (ash)

     _________
    /        /\      _    ___ ___  ___
   /  LE    /  \    | |  | __|   \| __|
  /    DE  /    \   | |__| _|| |) | _|
 /________/  LE  \  |____|___|___/|___|                      lede-project.org
 \        \   DE /
  \    LE  \    /  -----------------------------------------------------------
   \  DE    \  /    Reboot (17.01-SNAPSHOT, r3881+51-999bb66b20)
    \________\/    -----------------------------------------------------------

root@ffhb-fcecda7f28e1-UBNT-ERX-SFP:/#
~~~

Also daran Denken, vor dem Basteln einmal kurz /etc/config/ von der Kiste sichern, erleichtert viel Tiparbeit. Bei komplexeren Installationen sind einige Konfigs auch unter /var/ und /root/ abgelegt.

### Freifunkimage verbastelt? Stockfirmware einspielen.
An dieser Stelle waren alle Wiederbelebungsversuche erfolglos?, keine Panik.
Es wird nun die Originalfirmware eingespielt.
Wir brauchen:
- serielles Kabel mit Zugang zum Router
- 2 LAN-Kabel
- 1 externer Switch
- die Originalfirmware von der Herstellerseite
- einen laufenden TFTP Server auf unserem PC

Bedeutung des externen Switch: In dem Bootloader eines jeden Routers ist eine Abfrage eingebaut, die einen kurzen Moment eine bestimmte IP Adresse nach einem Image per TFTP fragt. Wenn euer PC zu langsam den LAN-Port hochfährt und ihr den nicht dauerhaft einschalten könnt, rennt der Router im Bootvorgang weiter und nix ist mit Image laden. Klemmt zwischen Router und PC einen kleinen Switch, der hält die Verbindung zum PC und stellt sehr schnell eine Verbindung zum Router her, wenn dieser nach dem Image fragt.

ER-X flashen:

1. Der ER-X hat die Adresse 172.16.3.211 im Bootloader und erwartet einen TFTP-Server mit 172.16.3.210, wo er ein Image mit dem Namen vme50 sucht.
2. Verbindun mit Port 0 herstellen und Router starten.

~~~
Please choose the operation:
   1: Load system code to SDRAM via TFTP.
   2: Load system code then write to Flash via TFTP.
   3: Boot system code via Flash (default).
   4: Entr boot command line interface.
   7: Load Boot Loader code then write to Flash via Serial.
   9: Load Boot Loader code then write to Flash via TFTP.
default: 3

You choosed 2
~~~
Jetzt lädt der Router das Image, bootet und alles ist wieder gut.


### POE EINschalten AUSschalten über Konsole
Ab der 2018.1.7 kann POE über das Konfigurationsinterface / Webinterface EIN oder AUS geschaltet werden.
Lange den Reset Knopf drücken und über den Internetbrowser die 192.168.1.1 aufrufen. Auf der Seite der Erweiterten Einstellungen finden sich die POE Ports, die mit einem einfachen Haken bedient werden. Der POE Satus wird über LED auf der Geräteoberseite angezeigt.

Im Openwrt WIKI steht noch, das einige Pakete installiert werden müssen, diese sind bereits enthalten.
Dieser Schritt nur der Vollständigkeit halber.

~~~
https://wiki.openwrt.org/toh/ubiquiti/ubiquiti_edgerouter_x_er-x_ka
PoE out on EdgeRouter X-SFP and EdgePoint R6
The routers can supply PoE on the LAN ports. This is controlled by a PCA9555A with GPIO 0..4.
In order to get this running you need:

  install "kmod-i2c-gpio-custom" (pulls gpio and algo-bitbang)
  install "kmod-gpio-pca953x"
  "insmod i2c-gpio-custom bus0=0,3,4"
  "echo pca9555 0x25 >/sys/bus/i2c/devices/i2c-0/new_device"
  export the GPIOs 496..500 (/sys/class/gpio/)

After reboot you need to run insmod and the echo line below to allow on/off functionality.

  insmod i2c-gpio-custom bus0=0,3,4
  echo pca9555 0x25 >/sys/bus/i2c/devices/i2c-0/new_device
~~~


#### Die GPIO Ports können direkt oder über UCI beschrieben werden.
Hier der direkte Weg:

~~~
#Turn on POE all ports except eth0(WAN)
#eth0 WAN port
  echo "496" > /sys/class/gpio/export
  echo "out" > /sys/class/gpio/gpio496/direction
  echo "0" > /sys/class/gpio/gpio496/value
#eth1
  echo "497" > /sys/class/gpio/export
  echo "out" > /sys/class/gpio/gpio497/direction
  echo "1" > /sys/class/gpio/gpio497/value
#eth2
  echo "498" > /sys/class/gpio/export
  echo "out" > /sys/class/gpio/gpio498/direction
  echo "1" > /sys/class/gpio/gpio498/value
#eth3
  echo "499" > /sys/class/gpio/export
  echo "out" > /sys/class/gpio/gpio499/direction
  echo "1" > /sys/class/gpio/gpio499/value
#eth4
  echo "500" > /sys/class/gpio/export
  echo "out" > /sys/class/gpio/gpio500/direction
  echo "1" > /sys/class/gpio/gpio500/value
~~~

und wieder aus:

~~~
#Turn off POE all ports except eth0(WAN)
  echo "0" > /sys/class/gpio/gpio496/value
  echo "0" > /sys/class/gpio/gpio497/value
  echo "0" > /sys/class/gpio/gpio498/value
  echo "0" > /sys/class/gpio/gpio499/value
  echo "0" > /sys/class/gpio/gpio500/value
~~~

UCI Befehle folgen.
