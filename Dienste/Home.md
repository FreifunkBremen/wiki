Im Freifunk-Netz kann man nicht nur das Internet benutzen. Jeder kann eigene Dienste anbieten, die wir auf dieser Seite sammeln wollen:

* [Wikipedia-Mirror (mit Bildern)](http://wikipedia.ffhb.de)
* [Meshviewer / map.bremen.freifunk.net / map.ffhb.de](https://map.bremen.freifunk.net/) interessante Darstellung unseres Netzes mit Daten zu Punkten wie einer Übersicht (neue und verschwundene yRouter), Knoten (alle Netzknoten mit Uptime und Anzahl der verbundenen Geräte), Verbindungen (Verbindungs-Qualität und Entfernung der im Router hinterlegten Geo-Koordinatender Funkstrecken) und Statistiken (eingesetzte Software/Hardware, Software- und Softwareupdate-Mechanismen).
* [grafana.bremen.freifunk.net / grafana.ffhb.de](https://grafana.bremen.freifunk.net) ist zur Darstellung von Werten über die Zeit hinweg (genauer siehe unsere [Datenschutz](Infrastruktur/Datenschutz)-Seite). Der Meshviewer zeigt einige Diagramme hieraus.
* [node.ffhb.de / node.bremen.freifunk.net](http://node.ffhb.de) Netzwerk-Daten wie IP-Adressen und Uptime-Infos von dem Router, mit dem man gerade physisch verbunden ist. Eventuell auch Links zum nächsten Router, falls verfügbar.
* [VPN-Server-Status](http://status.bremen.freifunk.net/) Zeigt den Status der VPN-Server an, gemessen von mehreren Monitoring-Clients im Freifunk-Netz.
* [Nodemon](https://nodemon.bremen.freifunk.net/) Lass dich informieren, wenn dein Knoten offline ist

* [InterCity VPN](http://icvpn.wg1337.de) Monitoring der verschiedenen Freifunk-Communities
* [freifunk-karte.de](http://www.freifunk-karte.de/) Die Karte nutzt die [Freifunk-API](https://api.freifunk.net/), um eine Liste der Communities in Deutschland zu beziehen. Aus deren API-Files werden dann die Links zu Knotenkarten gelesen. Die Karte wurde von [Tino Dietel](https://github.com/stilgarbf), FF Emskirchen gebaut.

* [minecraft.onffhb.de](http://minecraft.onffhb.de) Ein Minecraft Vanilla Server (Java Edition), erlaubt das gemeinsame Spielen in den nahezu unendlichen weiten der kantigen Welt. Der Server ist nur aus dem Freifunknetz erreichbar.

* minecraft.onffhb.de:25566 Eine epische Minecraft-Welt, bestehend aus Fliegenden Inseln. Hier wird gemeinsam im Kreativmodus gespielt.

## Infos zum aktuellen Router
Unter http://node.ffhb.de findest du Informationen zu dem Router, mit dem du momentan verbunden bist.

Generell findet man alle Knoten unter http://_knotennamen_.nodes.ffhb.de (Ausnahmen: wenn der Knotenname Punkte, Umlaute oder sonstige Sonderzeichen enthält, [werden die hierfür durch Bindestriche ersetzt](https://github.com/FreifunkBremen/ansible/blob/master/roles/nsd/files/zonegen.py#L13); und es werden hier keine Knotennamen unterstützt, die mit Ziffern beginnen oder die länger als 63 Zeichen sind).

## IPv4-Adressen
Folgende IP-Adressen sind vergeben:

* 10.196.0.0/17
    * 10.196.0.1 – 10.196.0.9 VPN-Server
        * 10.196.0.1 vpn01 (DNS, Gateway)
        * 10.196.0.2 vpn02 (DNS, Gateway)
        * 10.196.0.3 vpn03 (DNS, Gateway)
        * 10.196.0.5 vpn05 (DNS, Gateway, anon6789/genofire)
        * 10.196.0.6 vpn06 (DNS, Gateway, corny)
    * 10.196.0.10 – 10.196.0.39 Dienste-Server
    * 10.196.0.40 gatemon janeric
    * 10.196.0.80 Futro Frank_H Futro-Offloader Test
    * 10.196.0.81 gatemon-Frank_H, Frank_H
    * 10.196.0.82 WBS510 OpenWRT temporäre Tests; Frank_H
    * 10.196.0.90-94 genofire
    * 10.196.0.120 gatemon, rainbowcables, mortzu
    * 10.196.0.127 local-node FFHB
    * 10.196.0.131 gatemon-charlotte, mortzu
    * 10.196.0.134 gatemon-sommerwg, SimJoSt
    * 10.196.0.135 gatemon-moge, mortzu
    * 10.196.0.136 services.ffhb.mortzu.de (u.A. gatemon-plutex), mortzu
    * 10.196.0.137 gatemon-gueterbahnhof, yannik
    * 10.196.0.139 gatemon-banane, yannik
    * 10.196.0.141 gatemon-yannik2, yannik
    * 10.196.0.142 yannik
    * 10.196.0.145 Güterbahnhof-Test über yannik
    * 10.196.0.150 test-vm, anon6789
    * 10.196.0.200 Dienste von jplitza
    * 10.196.0.250 gatemon-oliverspi, ollibaba
    * 10.196.0.251 gatemon-charlotte (per WLAN), mortzu
    * 10.196.1.0/24 Richtfunk-Management
        * 10.196.1.4 Hal över Fährhäuschen NanoBeam
    * 10.196.2.10 - 50 Testbreich #Strahlemann
        * 10.196.2.15 CPE 210 v3.2 #Strahlemann
    * 10.196.10.0 - 10.196.19.255 per DHCP vergeben von 10.196.0.1
    * 10.196.20.0 - 10.196.29.255 per DHCP vergeben von 10.196.0.2
    * 10.196.30.0 - 10.196.39.255 per DHCP vergeben von 10.196.0.3
    * 10.196.40.0 - 10.196.49.255 per DHCP vergeben von 10.196.0.4
    * 10.196.50.0 - 10.196.59.255 per DHCP vergeben von 10.196.0.5
    * 10.196.60.0 - 10.196.69.255 per DHCP vergeben von 10.196.0.6
    * 10.196.70.0 - 10.196.79.255 per DHCP vergeben von 10.196.0.7
    * 10.196.80.0 - 10.196.89.255 per DHCP vergeben von 10.196.0.8
    * 10.196.90.0 - 10.196.99.255 per DHCP vergeben von 10.196.0.9
    * 10.196.100.0 - 10.196.109.255 per DHCP vergeben von 10.196.0.10
    *  10.196.122.224 - 10.196.122.255  Range von hias


Feste IP-Adressen von an Freifunk-Knoten angeschlossenen Servern sollten in 10.196.0.0/17 liegen. Hier eintragen und glücklich sein. Bitte schreib einen IRC-Nick oder eine Email-Adresse oder sonstige Kontaktdaten dazu.

## IPv6-Adressen
Corny stellt das Netz `2a06:8782::/32` zur Verfügung.
Daraus verwenden wir `2a06:8782:ffbb:1337::/64` für unser Layer 2 (Batman-adv).


Ausserdem nutzen wir das ULA-Netz `fd2f:5119:0f2c::/48`.

Einige Adressen sind fest hinterlegt. Sie werden im Folgenden aufgelistet.

### 2a06:8782::/32
#### 2a06:8782:ff00::/64
globale Dienste
* 2a06:8782:ff00::f1 download-ipv6
* 2a06:8782:ff00::f2 Webserver
* 2a06:8782:ff00::f3 DNS
* 2a06:8782:ff00::f4 Mails
* 2a06:8782:ff00::f6 ffmap (yanic -> generiert meshviewer/Karte)
* 2a06:8782:ff00::f7 vpn01

#### 2a06:8782:ffbb:1::/64
IPv6 Routing zum Gateway vpn01
#### 2a06:8782:ffbb:2::/64
IPv6 Routing zum Gateway vpn02
#### 2a06:8782:ffbb:3::/64
IPv6 Routing zum Gateway vpn04
#### 2a06:8782:ffbb:5::/64
IPv6 Routing zum Gateway vpn05
#### 2a06:8782:ffbb:6::/64
IPv6 Routing zum Gateway vpn06
#### 2a06:8782:ffbb:1337::/64
* *2a06:8782:ffbb:1337::1 bis 9 sind für Gateways vorgesehen.*
  * 2a06:8782:ffbb:1337::1 vpn01 (DNS, Gateway)
  * 2a06:8782:ffbb:1337::2 vpn02 (DNS, Gateway)
  * 2a06:8782:ffbb:1337::3 vpn03 (DNS, Gateway)
  * 2a06:8782:ffbb:1337::5 vpn05 (DNS, Gateway, anon6789/genofire)
  * 2a06:8782:ffbb:1337::6 vpn06 (DNS, Gateway)
* 2a06:8782:ffbb:1337::11 (bremnet.de/lxsbbs revival)
* 2a06:8782:ffbb:1337::5b bis 5f (genofire)
* 2a06:8782:ffbb:1337::83 gatemon-charlotte.ffhb.moritzrudert.de, mortzu
* 2a06:8782:ffbb:1337::86 gatemon-sommerwg.ffhb.moritzrudert.de, mortzu
* 2a06:8782:ffbb:1337::87 gatemon-moge.ffhb.moritzrudert.de, mortzu
* 2a06:8782:ffbb:1337::88 services.ffhb.moritzrudert.de (u.A. gatemon-plutex), mortzu
* 2a06:8782:ffbb:1337::b0 bis bf (janeric)
* 2a06:8782:ffbb:1337::c8 (steffen)
* 2a06:8782:ffbb:1337::d1 gatemon-charlotte (per WLAN), mortzu
* 2a06:8782:ffbb:1337:1ad6:c7ff:fe90:dd6c CPE 210 v3.2 #Strahlemann ( Funktioniert irgentwie nicht ausserhalb aus FF. :-( )

#### 2a06:8782:ffbb:42::/64
(reserviert für das neue Batman-v15-Netz)

#### 2a06:8782:ffbb:bat0::/64
Babel-Netzwerk Segment für die Knoten/Nodes und das Routing des Client-Netzwerks

* *2a06:8782:ffbb:bat0::1 bis 9 sind für Gateways vorgesehen.*
  * 2a06:8782:ffbb:bat0::5 vpn05 (DNS, Gateway, anon6789/genofire)


#### 2a06:8782:ffbb:bat1::/64
Babel-Netzwerksegment das für die Clients an den Knotes/Nodes und darüber hinaus zur Verfügung steht.

* *2a06:8782:ffbb:bat1::1 bis 9 sind für Gateways vorgesehen.*
  * 2a06:8782:ffbb:bat1::5 vpn05 (DNS, Gateway, anon6789/genofire)

## Andere Netze
Aus dem Bremer Freifunk-Netz heraus erreichst du auch die Freifunk-Netze andere Städte und deren Dienste, beispielsweise [jene in Lübeck](http://luebeck.freifunk.net/wiki/Freifunk-verwenden). Auch zu anderen Netzen wie dem [dn42](http://dn42.net) oder [Chaos-VPN](http://wiki.hamburg.ccc.de/index.php/ChaosVPN) besteht eine Verbindung.
