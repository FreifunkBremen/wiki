### geplante Tests

#### Test LAN-verketteter Router (Vorschlag von?)
* Mesh-on-LAN enabled
* 1. Router ans Internet anschließen
* mindestens 5 Geräte verkettet
* Testen: Internetgeschwindigkeit und -stabilität am letzten Router über LAN

#### Kein Meshing, zentraler Router (Julian)
* Ports der WDR-Router ins gleiche VLAN
* Ein zentraler Router (Debian/FreeBSD) für DHCP und VPN-Routing (GRE-Tunnel, weil performanter als alles andere)
    * B.A.T.M.A.N. advanced gibt es nicht für *BSD, also wohl eher Debian. --jplitza
* Testen: Durchsatz und Latenz des WDR-Switches (einzeln und über mehrere Nodes)
* Testen: Funktioniert so eine Konfiguration mit Gluon? Insbesondere:
    * Funktioniert der Multicast-Filter weiterhin?
        * Ja, solange im VLAN B.A.T.M.A.N. advanced gesprochen wird. Der Filter setzt an der br-client an, die die bremen.freifunk.net ESSID mit dem bat0-Interface verbindet. --jplitza
    * Gibt Alfred noch sinnvolle Daten für die Nodes aus?
        * Ja, solange im VLAN B.A.T.M.A.N. advanced gesprochen wird. Lediglich für den zentralen Router müsste man noch das [Announcen von Informationen konfigurieren](https://github.com/ffnord/ffnord-gateway-alfred/) --jplitza
* Testen: Hardware für den zentralen Router vergleichen:
    * APU1.D: 440 Mbit/s durch GRE unter FreeBSD
    * Alternativen?
* Nachteil: SPoF. --jplitza