Im Freifunk-Netz kann man nicht nur das Internet benutzen. Jeder kann eigene Dienste anbieten, die wir auf dieser Seite sammeln wollen:

* [Wikipedia-Mirror (mit Bildern)](http://wikipedia.ffhb.de)
* [Tahoe-LAFS](/Dienste/Tahoe-LAFS)
* [SIP Server](http://sip.ffhb.de/web/) Asterisk SIP und SMS Server (alpha - Nebirosh) Anleitung zur Einrichtung folgt!
* [Etherpad-lite](http://pads.ffhb.de/) kollaboratives Schreiben von Texten

## Infos zum aktuellen Router
Unter http://node.ffhb.de findest du Informationen zu dem Router, mit dem du momentan verbunden bist.

Generell findet man alle Knoten unter http://_knotennamen_.nodes.ffhb.de (Ausnahmen: wenn der Knotenname Punkte enthält, werden die hierfür durch Bindestriche ersetzt; und es werden hier keine Knotennamen unterstützt, die mit Ziffern beginnen).

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
    * 10.196.0.42 server, mumble, experimentell (diega)
    * 10.196.0.60 notebook (bis dhcp zuverlässig läuft (diega))
    * 10.196.0.50 VPN-Offloader der Uni
    * 10.196.0.70 anon6789
    * 10.196.0.75 Offloader azgbr
    * 10.196.0.80 Futro Frank.H Offloader Test
    * 10.196.0.90-94 genofire
    * 10.196.0.100 Dienste von Lorenz
    * 10.196.0.111 ec8or
    * 10.196.0.123 rbtz
    * 10.196.0.127 local-node FFHB
    * 10.196.0.128-159 Dienste von mortzu
      * 10.196.0.131 gatemon-3.ffhb.moritzrudert.de
      * 10.196.0.134 gatemon-2.ffhb.moritzrudert.de
      * 10.196.0.135 gatemon-fes216.ffhb.moritzrudert.de
    * 10.196.0.196 Dienste von Eike
    * 10.196.0.200 Dienste von jplitza
    * 10.196.0.240 Dienste von proxyhb
    * 10.196.0.250-252 Gatemon (Pi1) etc. von ollibaba
    * 10.196.10.0 - 10.196.19.255 per DHCP vergeben von 10.196.0.1
    * 10.196.20.0 - 10.196.29.255 per DHCP vergeben von 10.196.0.2
    * 10.196.30.0 - 10.196.39.255 per DHCP vergeben von 10.196.0.3
    * 10.196.40.0 - 10.196.49.255 per DHCP vergeben von 10.196.0.4
    * 10.196.50.0 - 10.196.59.255 per DHCP vergeben von 10.196.0.5
    * 10.196.60.0 - 10.196.69.255 per DHCP vergeben von 10.196.0.6
  * 10.196.123.0/24 Range von Ixoid
    * 10.196.123.42 GartenPi
* 10.196.126.0/24
  * 10.196.126.0/24 Dienste von Nebirosh
* 10.196.127.0/24 Dienste von HeinzBoettjer
    * 10.196.127.1 Scanner an asm_100_EG (pausiert)
    * 10.196.127.2 Scanner an hhs-1 (pausiert)
    * 10.196.127.3 Linux-ISO-Server an ffhb-asm100 (in Vorbereitung)
    * 10.196.127.4 apt-mirror (in Vorbereitung)
    * 10.196.127.5 mirror für downloads.bremen.freifunk.net/firmware (in Vorbereitung)
    * 10.196.127.6 mumble-server (in Planung)

Feste IP-Adressen von an Freifunk-Knoten angeschlossenen Servern sollten in 10.196.0.0/17 liegen. Hier eintragen und glücklich sein.

## IPv6-Adressen
Corny stellt das Netz `2a06:8782::/32` zur Verfügung.
Daraus verwenden wir `2a06:8782:ffbb:1337::/64` für unser Layer 2 (Batman-adv).


Mortzu hat bei bei SixXS das ULA-Netz `fd2f:5119:0f2c::/48` registriert, dieses begegnet einem an manchen Stellen ebenso wie das ehemalige Prefix `2001:bf7:540::/48`.

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
* 2a06:8782:ffbb:1337::5b bis 5f (genofire)
* 2a06:8782:ffbb:1337::f0 (proxyhb)
* 2a06:8782:ffbb:1337::6f (ec8or)
* 2a06:8782:ffbb:1337::80 bis 9f Dienste von mortzu
  * 2a06:8782:ffbb:1337::83 gatemon-3.ffhb.moritzrudert.de
  * 2a06:8782:ffbb:1337::85 Gatemon (Pi1) von ollibaba
  * 2a06:8782:ffbb:1337::86 gatemon-2.ffhb.moritzrudert.de
  * 2a06:8782:ffbb:1337::87 gatemon-fes216.ffhb.moritzrudert.de
* 2a06:8782:ffbb:1337::a0 bis af (ollibaba)
  * 2a06:8782:ffbb:1337::a0 Gatemon Pi2

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
