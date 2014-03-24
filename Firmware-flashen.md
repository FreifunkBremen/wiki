Auf dieser Seite wird erklärt, wie die Router geflasht werden können.

## TP-Link Router flashen

Wenn ein TP-Link Router neu gekauft wird, kann der Flash-Vorgang über den Browser vorgenommen werden:

1. Router ans Stromnetz anschließen
2. Router mit LAN-Kabel von einen LAN-Port an Rechner anschließen. Auf Rechner DHCP einschalten oder IP-Adresse aus dem Bereich 192.168.0.0/24
3. Mit dem Browser der Wahl die Adresse [192.168.0.1](http://192.168.0.1) aufrufen. Zugangsdaten stehen auf der Rückseite des Routers (in der Regel admin/admin)
4. Nun unter System Tools -> Firmware Upgrade das entsprechende [Factory](http://downloads.bremen.freifunk.net/firmware/testing/factory/) einspielen
5. Warten bis der Flash-Vorgang abgeschlossen ist ("Completed" erscheint auf Bildschirm und Browser versucht zu refreshen).

Damit ist der Flashvorgang abgeschlossen und der Router kann unter [192.168.1.1](http://192.168.1.1) konfiguriert werden. Weitere Informationen zum Konfig-Mode finden sich auf [[Firmware]] 
