Im Freifunk-Netz kann man nicht nur das Internet benutzen. Jeder kann eigene Dienste anbieten, die wir auf dieser Seite sammeln wollen:

* [Wikipedia-Mirror (mit Bildern)](http://wikipedia.ffhb.de)
* [Tahoe-LAFS](Dienste/Tahoe-LAFS)
* [Straßenbahn-Fahrplan Sielwall](http://10.196.0.69) Echtzeit Haltestellendaten (noch Testbetrieb)
* [Freifunk Store](http://10.196.0.69/ff_store/) unkommerzielle Router-, Antennen und Teilebörse
* [Gitlab](http://gitlab.services.ffhb.de/) per Aktivierung von genofire
* [Chat](http://chat.services.ffhb.de/) Jabber Server. ( Webclient noch in der Entwicklung - genofire)
* [SIP Server](http://sip.services.ffhb.de/web/) Asterisk SIP Server ( alpha - Nebirosh)
* [Etherpad-lite](http://pads.services.ffhb.de/) kollaboratives Schreiben von Texten 

## Infos zum aktuellen Router
Unter http://node.ffhb.de findest du Informationen zu dem Router, mit dem du momentan verbunden bist.

## IPv4-Adressen
Folgende IP-Adressen sind vergeben:

* 10.196.0.0/17
    * 10.196.0.1 – 10.196.0.9 VPN-Server
    * 10.196.0.42 server, mumble, experimentell (diega)
    * 10.196.0.60 notebook (bis dhcp zuverlässig läuft (diega))
    * 10.196.0.69 S-Bahn Fahrplan + Store (anon6789)
    * 10.196.0.70 anon6789
    * 10.196.0.90-95 genofire
    * 10.196.0.127 node.ffhb.de
    * 10.196.0.128 alternativer DNS Server (mortzu)
    * 10.196.0.129-159 Dienste von mortzu
    * 10.196.0.196 Dienste von Eike
    * 10.196.0.200 Dienste von jplitza
    * 10.196.10.0 – 10.196.19.255 per DHCP vergeben von 10.196.0.1
    * 10.196.20.0 – 10.196.29.255 per DHCP vergeben von 10.196.0.2
    * 10.196.30.0 – 10.196.39.255 per DHCP vergeben von 10.196.0.3
* 10.196.126.0/24
  * 10.196.126.0/24 Dienste von Nebirosh
* 10.196.127.0/24
  * 10.196.127.1 Scanner an ffhb-asm100
  * 10.196.127.2 Scanner an ffhb-dvb15
  * 10.196.127.3 Linux-ISO-Server an ffhb-asm100 (in Vorbereitung)

Feste IP-Adressen von an Freifunk-Knoten angeschlossenen Servern sollten in 10.196.0.0/24 liegen. Hier eintragen und glücklich sein.

## IPv6-Adressen
mortzu hat bei bei SixXS das ULA-Netz fd2f:5119:0f2c::/48 registriert. Wir haben aber auch den globalen Bereich 2001:bf7:540::/43 vom Freie Netze e.V. Momentan werden beide verteilt, in der Firmware ist das ULA-Netz eingetragen.

## Andere Netze
Aus dem Bremer Freifunk-Netz heraus erreichst du auch die Freifunk-Netze andere Städte und deren Dienste, beispielsweise [jene in Lübeck](http://luebeck.freifunk.net/wiki/Freifunk-verwenden). Auch zu anderen Netzen wie dem [dn42](http://dn42.net) oder [Chaos-VPN](http://wiki.hamburg.ccc.de/index.php/ChaosVPN) besteht eine Verbindung.