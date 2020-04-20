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


## 2019.1.2 bremen 2
* Frank_H 841nd v8 & Archer C7v2 nach upgrade schlechte Meshverbindung auf der Karte, beide Router neu gestartet.


## [Gelöst] logread zeigt "fastd[1999]: resolving host `vpn01.bremen.freifunk.net' failed: Try again"
Übliche Ursache: der Knoten versucht, eine VPN-Verbindung aufzubauen, aber er hat keinen direkten Internetzugang.
- deshalb: am besten Mesh-VPN ausschalten, wenn der Knoten eh definitiv kein VPN aufbauen soll; das reduziert den Log-Spam
- abschalten geht per "/etc/init.d/fastd stop ; uci set fastd.mesh_vpn.enabled='0'; uci commit fastd"


## SSH-Verbindungen zum Knoten bleiben hängen
Wenn man sich per SSH aus dem Internet zu einem Knoten verbindet und dort große Datenmengen übertragen werden (z.B. durch Ausführen von `logread` und Scrollen), bleibt die SSH-Verbindung hängen.

- das sind IPv6-Verbindungen (weil die Knoten nur über IPv6 erreichbar sind)
- könnte ein MTU-Problem sein

Lässt sich auch hier mit in Verbindung bringen:
#### TL-MR3020 v1 hängt sich bei Upgrade auf (hias)
Bei Manuellen upgrade eines TL-MR3020 v1  via ssh (mit 'autoupdater -f')
friert die SSH Sitzung ein, und das Upgrade läuft nicht durch.

Problem ist mind. 2x aufgetreten.
Router mesh't nur via VPN.

## Fehlermeldung in den Logs vieler Knoten
Bei 7 von 8 Knoten festgestellt.
Im Schnitt c.a. 80 x innerhalb eines Tages in den logs.
Das war schon mal besser.

daemon.err gluon-radv-filterd[1725]: Unable to find router ... in transtable_{global,local}

daemon.err gluon-radv-filterd[1725]: Unable to find TQ for originator ... (router ...)


## [Gelöst] `okpg update` läuft nicht durch, wenn der Knoten mit vpn2 oder vpn5 verbunden ist
Dieses Problem wurde in https://tasks.ffhb.de/T357 ("IPv6-Pakete mit bestimmten Größen werden nicht zuverlässig übertragen") weiter untersucht und gelöst.

Das Symptom war, dass IPv6-TCP-Pakete mit Paketgrößen zwischen 1343 und 1366 Bytes (inklusive) nicht übertragen wurden, wenn der Knoten an vpn2 oder vpn5 hing.

Das Problem war am Ende, dass ein Tunnel zwischen vpn2 bzw. vpn5 und dem ipv6-downlink-Host eine falsche MTU hatte.
