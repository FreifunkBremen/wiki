# Beobachtete Probleme im Freifunk-Netz - Störungen, Ausfälle, Probleme

Hier werden Störungen, Ausfälle, Performance-Mängel und andere Probleme gesammelt, die im Freifunk-Netz beobachtet wurden.

Trag möglichst viele Details ein: was genau hast du beobachtet, wann war das, was hast du stattdessen erwartet?

## Ausfälle (Loop?) morgens am 25.3.2020
* von hias beobachtet
* hoher ICMP6 durchsatz[2], Hinweise auf loop in den Logs[3], Was war da los, Wurde was unternommen um es zu beheben und wenn ja, Was?
* hat sich anscheinend von selbst wieder gelöst

Anmerkungen:
* 1: https://grafana.bremen.freifunk.net/d/000000011/multicast?orgId=1&from=1585094038403&to=1585129298085&var-protocol=All
* 2: https://grafana.bremen.freifunk.net/d/000000001/globals?orgId=1&from=1585094038403&to=1585129298085
* 3: kern.warn kernel: (...) br-client: received packet on bat0 with own address as source address


## Langsames Freifunk bei 50-MBit-Leitung
[Louis sagt:](https://wiki.ffhb.de/Treffen/2020_03_20#protokoll_fehler-geschwindigkeit-des-freifunks-warum-ist-das-so-langsam_wie-%C3%A4u%C3%9Fern-sich-die-probleme) mit einer 50-MBit-Leitung ist das Internet über Freifunk merklich langsamer als über den direkten Anschluss. Lässt sich mit einem normalen Download messen.

Nächste Schritte:
* gib mal einen Download-Link, mit dem das messbar ist
* tritt das zu beliebigen Zeiten auf, oder nur zu bestimmten Zeiten?
* tritt das nur mit bestimmten VPN-Gateways auf?
* tritt das nur an bestimmten Knoten oder mit bestimmten Knoten-Modellen auf?
* ist ein Offloader im Einsatz?
