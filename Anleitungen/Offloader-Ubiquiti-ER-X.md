## Gluon auf UBNT EdgeRouter X und X-SFP

Einige Erfolge und die tollen verfügbaren Anleitungen, sollen hier Mut machen, die kleinen Leistungsstarken Ubiquiti Edgerouter ER-X als Offloader einzusetzen.
Warum Offloader? Werden mehrere Freifunkrouter verwendet, ist es sinnvoll, dass nicht alle Router ihren eigenen VPN Tunnel aufbauen. Der Offloader übernimmt die Verschlüsselung und mesht über die LAN Ports mit den Freifunkroutern, das gibt ein deutlich schnelleres Netz bei geringen Kosten.

### Was spricht für dieses Modell Ubiquiti EdgeRouter X (ER-X)?
- Der ER-X besitzt einen Gigabit Port mit Passiv PoE Eingang (24 V, eth0) und kann so ohne Netzteil betrieben werden. Weiterhin gibt es einen Gigabit Port mit Passiv PoE Ausgang (24 V, eth4) um einen Access Point anzuschließen. Daneben noch drei weitere Gigabit Ports zur weiteren Verwendung (eth1/2/3). 
- Abmessungen: 110 x 75 x 22
- Prozessor:   Dual-Core 880 MHz
- Geringer Stromverbrauch: 5W, 12V Netzteil.

### Diverse nützliche Links:
- https://www.ubnt.com/edgemax/edgerouter-x/
- https://dl.ubnt.com/datasheets/edgemax/EdgeRouter_X_DS.pdf
- https://www.ubnt.com/edgemax/comparison/
- https://www.heise.de/preisvergleich/ubiquiti-edgerouter-er-x-a1271798.html
- https://wiki.funkfeuer.at/wiki/Hardware/EdgeRouter_X
- https://wiki.funkfeuer.at/wiki/Hardware/EdgeRouter_X-SFP

### Links zu Anleitungen:
- https://github.com/oszilloskop/UBNT_ERX_Gluon_Factory-Image
- https://www.freifunk-winterberg.net/die-nutzung-von-ubiquiti-edgerouter-x-als-freifunk-offloader/
- https://wiki.openwrt.org/toh/ubiquiti/ubiquiti_edgerouter_x_er-x_ka
- https://community.ubnt.com/t5/EdgeMAX-Updates-Blog/EdgeMAX-EdgeRouter-X-X-SFP-bootloader-update/ba-p/1472216

### Links zu Firmware:
- https://downloads.openwrt.org/snapshots/trunk/ramips/mt7621/openwrt-ramips-mt7621-ubnt-erx-squashfs-sysupgrade.tar
- https://dl.ubnt.com/firmwares/edgemax/v1.10.x/ER-e50.v1.10.6.5112725.tar
- https://downloads.bremen.freifunk.net/firmware/stable/sysupgrade/gluon-ffhb-2017.1.8+bremen1-ubnt-erx-sysupgrade.tar
- https://downloads.bremen.freifunk.net/firmware/all/2017.1.8+bremen1/sysupgrade/gluon-ffhb-2017.1.8+bremen1-ubnt-erx-sfp-sysupgrade.tar

Frohes Freifunken.



 