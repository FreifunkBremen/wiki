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


## Unzuverlässige Karten-Updates bei Mesh-Verbindungen
* Knoten, die nur per Mesh verbunden sind, erscheinend tw. nicht auf der Karte
* tritt wohl erst seit 2019.1.2+bremen2 auf
* Frank_H 841nd v8 & Archer C7v2 nach upgrade schlechte Meshverbindung auf der Karte, beide Router neu gestartet.

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

Nachtrag:
Fehler tritt vmtl dann auf wenn der Router nicht aus Freifunk aufgerufen wird.

## Fehlermeldung in den Logs vieler Knoten
Bei 7 von 8 Knoten festgestellt.
Im Schnitt c.a. 80 x innerhalb eines Tages in den logs.
Das war schon mal besser.
```
daemon.err gluon-radv-filterd[1725]: Unable to find router ... in transtable_{global,local}

daemon.err gluon-radv-filterd[1725]: Unable to find TQ for originator ... (router ...)
```

## Schlechte Benutzererfahrung
Verbindungsabbrüche  bei Onlinegaming.
Speedtest zum VPN << 1 Mbit up and down an 30 Mbit DSL Anschluss.
schlechtes Ping mit viel Duplikaten.

In den Logs der beiden lokalen Knoten keine Hinweise.

Ergebnis paralleler ping von client gegen localnode und aktuellem vpn:
```
--- vpn03.ffhb.de ping statistics ---
808 packets transmitted, 737 packets received, +417 duplicates, 8.8% packet loss
round-trip min/avg/max/stddev = 26.900/547.563/6832.153/1052.252 ms
--- node.ffhb.de ping statistics ---
818 packets transmitted, 812 packets received, 0.7% packet loss
round-trip min/avg/max/stddev = 0.803/17.921/1125.749/83.971 ms
```
2 Stunden später, packet loss in der gleichen Größenordnung (um 10%) zu vpn, allerdings keine Duplikate mehr.
Diesmal auch ping zu 2. Knoten um auch die mesh-Verbindung zu erfassen, hier packet los 0,1%, zu local.node 0,0%

Local scheinbar keine Probleme, erst über VPN wird es schwierig.

Umgebung:
```
client
   | <-Funk client
TL-WR841N/ND v10
2019.1.2+bremen2
   | <-Funk mesh TQ 90-100%
TL-WR1043N/ND v4 mit WWAN
2019.1.2+bremen2
   | <-Ethernet, Frizbox, DSL
VPN03
```

Fragen hierzu:
* welcher DSL-Anbieter wird da verwendet?
* - EWE
* zu welchem Datum/Uhrzeit passierte das?
* - Unspezifisch / unbekannt
* ist das immer so, oder gibt es Zeiten, wo es problemlos funktioniert? Morgens, mittags, abends? Am Wochenende oder unter der Woche?
* - Funktioniert auch Problemlos. Kann zu allen Zeiten sein.
* Vorschläge um das Automatisch zu überwachen? Weiß jemand was fertiges?

## DNS kaput
Namensauflösung funktioniert im FF nicht mehr.
betrifft clients und knoten.
2020-05-01
Zwischen 15:00 - 16:30 aufgetreten.
Siehe Tagesordnung Freffen
https://wiki.bremen.freifunk.net/Treffen/2020_05_01

## UBNT AC-Mesh ohne SSID
Bei meinem UBNT AC-M werden bei den Meshkanälen als SSID * angezeigt.
Ist das so richtig? Bei anderen Geräten sehe ich das nicht.

Liegt wohl an 11s, dass nur ein * anstatt mesh.ffhb.net abgestrahlt wird.

## UBNT AC-Mesh nur 2,4Ghz Mesh

Bei der Erstinstallation kann es vorkommen, dass nur 2,4Ghz Mesh übernommen wird.
Lösung: Datei /etc/config/network prüfen, ob beide Einträge vorhanden sind.
~~~
config interface 'mesh_radio0'
	option proto 'gluon_mesh'

config interface 'mesh_radio1'
	option proto 'gluon_mesh'
~~~


## Sehr langsames Internet an der Radstation
* am 15.5.2020 hat FsH an der Radstation Speedtests gemacht. Es war sehr langsam: 5-10 MBit/s; stark schwankend
* früher (bei der Einrichtung, und auch bis ca. Mitte März) waren da noch 70 MBit/s erreichbar
* der Vorplatz-Knoten ist zwar nur per WLAN-Mesh angebunden. Aber die Probleme gab es auch z.B. am GST-Knoten; und der mesht laut Karte per "Kabel" (also Kabel+Richtverbindung)
* möglicherweise auch ein MTU-Problem?
* seit den guten Ergebnissen wurden wohl mehrere Dinge geändert (Firmware-Upgrade, Kabel-Mesh-Verbindungen optimieren...)
* die Radstation ist über den Schlachthof angebunden; also im Moment über vpn01

## [Gelöst] logread zeigt "fastd[1999]: resolving host `vpn01.bremen.freifunk.net' failed: Try again"
Übliche Ursache: der Knoten versucht, eine VPN-Verbindung aufzubauen, aber er hat keinen direkten Internetzugang.
- deshalb: am besten Mesh-VPN ausschalten, wenn der Knoten eh definitiv kein VPN aufbauen soll; das reduziert den Log-Spam
- abschalten geht per "/etc/init.d/fastd stop ; uci set fastd.mesh_vpn.enabled='0'; uci commit fastd"


## [Gelöst] `okpg update` läuft nicht durch, wenn der Knoten mit vpn2 oder vpn5 verbunden ist
Dieses Problem wurde in https://tasks.ffhb.de/T357 ("IPv6-Pakete mit bestimmten Größen werden nicht zuverlässig übertragen") weiter untersucht und gelöst.

Das Symptom war, dass IPv6-TCP-Pakete mit Paketgrößen zwischen 1343 und 1366 Bytes (inklusive) nicht übertragen wurden, wenn der Knoten an vpn2 oder vpn5 hing.

Das Problem war am Ende, dass ein Tunnel zwischen vpn2 bzw. vpn5 und dem ipv6-downlink-Host eine falsche MTU hatte.
