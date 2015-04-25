### geplante Tests

#### Test LAN-verketteter Router (Vorschlag von?)
* Mesh-on-LAN enabled
* 1. Router ans Internet anschließen
* mindestens 5 Geräte verkettet
* Testen: Internetgeschwindigkeit und -stabilität am letzten Router über LAN

#### Kein Meshing (Julian)
* Ports der WDR-Router ins gleiche VLAN
* Ein zentraler Router (Debian/FreeBSD) für DHCP und VPN-Routing (GRE-Tunnel)
* Testen: Funktioniert so eine Konfiguration mit Gluon?
* Testen: Gibt Alfred noch sinnvolle Daten für die Nodes aus?
* Testen: Durchsatz und Latenz des WDR-Switches (einzeln und über mehrere Nodes)
* Testen: Hardware für den zentralen Router vergleichen:
 * APU1.D: 440 Mbit/s durch GRE unter FreeBSD
 * Alternativen?
 