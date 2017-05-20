Was ist ein Offloader?
Das ist ein Mini-PC, Rasberry, Thin-Client, der mit der Freifunksoftware
primär nur eine Aufgaben hat. Er baut einen leistungsstarken VPN Tunnel 
zu einem Freifunkgateway auf.
Ein Offloader kommt zum Einsatz, wenn mehr Bandbreite an einem DSL-Anschluss
benötigt wird. Nach bisherigen Berichten sind 100Mb VPN Tunnel kein Problem.
Erfahrungen mit höheren Bandbreiten liegen nicht vor.

Welche Geräte brauche ich oder werden unterstützt?
Um keine spezifische Werbung zu machen, alle kleinen x86 Geräte die
Openwrt/LEDE, also LINUX fähig sind.
Damit das bezahlbar bleibt, setzten Freifunker gerne auf Gebrauchtgeräte
der Marke IGEL oder Fujitsu-Siemens Futro. Da der Gebrauchtmarkt stark
schwankt, wechseln die Geräte in der Beliebtheit gerne ihren Rang.
Gerne werden der Futro S550-2 oder Futro S900 verwendet.

Stückliste, Materialliste
Ein Freifunk X86 Image, z.B. (gluon-ffhb-2016.2.4+bremen2-x86-generic.img.gz) zu finden unter https://downloads.bremen.freifunk.net/firmware/stable/factory/
Ein bootfähiger USB Stick, wo das Image so wie es ist, draufkopiert wird.
Die Anleitung und die Bootsoftware unter: https://github.com/oszilloskop/Gluon2Futro/
Für den Futro S900 ist noch eine Korektur notwendig, siehe: https://wiki.bremen.freifunk.net/Anleitungen/Offloader-Futro-S900
Einen Futro S550/S900, ebay ca. 8-28 € inklusive Netzteil.
Eine Speicherkarte >55Mb, Im Futro S550 ist normalerweise eine CF Flashcard 1-2Gb dabei,
der Futro S900 benötigt eine mSata, die nicht babei ist.
Eine mSata ist ab 20€ zu bekommen. Eine CF-Card ab 1€
Eine zweite Netzwerkkarte mit kurzem Slotblech, bei Conrad neu für ca. 7€
Eine Risercard, das ist ein Winkeladapter für die Netzwerkkarte, ca. 2.90€
siehe ebay http://www.ebay.de/itm/RISER-CARD-RISERCARD-SINGLE-PCI-RISER-KARTE-FSC-FUTRO-S500-S550-736TR3230K100-/311501262291?hash=item4886ec0dd3:g:D-oAAOSwfZ1WZxOd
Monitor und Tastatur für die Installation.

Kosten für den Futro S550-2: zwischen 20€ - 30€
Kosten für den Futro S900  : zwischen 35€ - 50€

Die Konfiguration erfolgt wie bei einem normalen Freifunkrouter, zusätzliche
Konfigurationen im Linux sind nicht notwendig. Weitere Informationen über die Offloaderbeiträge im Wiki oder im Forum.freifunk.net
