## Gluon auf UBNT EdgeRouter X und X-SFP

Einige Erfolge und die tollen verfügbaren Anleitungen, sollen hier Mut machen, die kleinen Leistungsstarken Ubiquiti Edgerouter ER-X als Offloader einzusetzen.
Warum Offloader? Werden mehrere Freifunkrouter verwendet, ist es sinnvoll, dass nicht alle Router ihren eigenen VPN Tunnel aufbauen. Der Offloader übernimmt die Verschlüsselung und mesht über die LAN Ports mit den Freifunkroutern, das gibt ein deutlich schnelleres Netz bei geringen Kosten.

### Was spricht für dieses Modell Ubiquiti EdgeRouter X (ER-X) / (ER-X SFP)?
- Der ER-X besitzt einen Gigabit Port mit Passiv PoE Eingang (24 V, eth0) und kann so ohne Netzteil betrieben werden. Weiterhin gibt es einen Gigabit Port mit Passiv PoE Ausgang (24 V, eth4) um einen Access Point anzuschließen. Daneben noch drei weitere Gigabit Ports zur weiteren Verwendung (eth1/2/3). 
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

Wenn der Router einmal gebrickt ist, also es besteht kein Zugriff mehr über die externen Schnittstellen, im folgenden einige Rettungsversuche.

### Freifunkimage verbastelt?
Ich habe durch diverse Konfigurationen den Router unbrauchbar gemacht.
Keine Panik, es gibt die serielle Schnittstelle im Router. Auf der rechten Seite am Rand sind 4 Pins eingelötet an der ein Seriell-USB Adapter angeschlossen werden kann.
- Router öffnen: Auf der Rückseite sind zwei kleine Kreuzschrauben, die die beiden Gehäusehälften zusammenhalten. Im SFP Modell zuerst das SFP entfernen. Schreuben herausnehmen und Gehäuse aufklappen.
- Seriellen Adapter Anschliessen. Ich verwende hier ein Raspberry-PI Seriell-USB Kabel. z.B. dieses: https://www.conrad.de/de/raspberry-pi-usb-kabel-usb-rb-ttl-raspberry-pi-409202.html
- Herstellerbeschreibung des Kabels: "Mit diesem Kabel verbinden Sie Ihren Raspberry PI ganz einfach mit einem PC System. Gleichzeitig stellt das Kabel über den USB Port des PC 5V bei 500mA zur Verfügung, so dass Sie kein separates Netzteil verwenden müssen. Der in dem Kabel integrierte serielle PL2303HX Chip sorgt dafür, dass beide Geräte miteinander Daten austauschen können. Hierbei werden Windows XP, Vista, 7 und 8 unterstützt. Belegung der PIN Stecker: rot = Power +5V / schwarz = Ground / weiß = RX / grün = TX"
- Die PIN Belegung der seriellen Schnittstelle ist beschrieben unter: https://openwrt.org/toh/ubiquiti/ubiquiti_edgerouter_x_er-x_ka#poe_out_on_edgerouter_x
- PIN zum Reset-Knopf: Ground, TX, RX, 3,3V zur ETH 5 Buchse zeigend.
- 


 