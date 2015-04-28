### geplante Tests

#### Test LAN-verketteter Router (Vorschlag von?)
* Mesh-on-LAN enabled
* 1. Router ans Internet anschließen
* mindestens 5 Geräte verkettet
* Testen: Internetgeschwindigkeit und -stabilität am letzten Router über LAN

#### Kein Meshing, zentraler Router (Julian)
* Ports der WDR-Router ins gleiche VLAN
* Ein zentraler Router (Debian/FreeBSD) für DHCP und VPN-Routing (GRE-Tunnel, weil performanter als alles andere)
* Testen: Durchsatz und Latenz des WDR-Switches (einzeln und über mehrere Nodes)
* Testen: Funktioniert so eine Konfiguration mit Gluon? Insbesondere:
 * Funktioniert der Multicast-Filter weiterhin?
 * Gibt Alfred noch sinnvolle Daten für die Nodes aus?
* Testen: Hardware für den zentralen Router vergleichen:
 * APU1.D: 440 Mbit/s durch GRE unter FreeBSD
 * Alternativen?
 