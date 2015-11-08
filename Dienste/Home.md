Im Freifunk-Netz kann man nicht nur das Internet benutzen. Jeder kann eigene Dienste anbieten, die wir auf dieser Seite sammeln wollen:

* [Wikipedia-Mirror (mit Bildern)](http://wikipedia.ffhb.de)
* [Tahoe-LAFS](/Dienste/Tahoe-LAFS)
* [Monitoring in FFHB](http://monitoring.ffhb.de) [in Public](http://monitoring.ffhb.ml) OMD Site.
  (Benutzer:guest, Passwort: ffhb - Weitere Rechte auf Anfrage) (genofire)
* [SIP Server](http://sip.services.ffhb.de/web/) Asterisk SIP und SMS Server (alpha - Nebirosh) Anleitung zur Einrichtung folgt!
* [Etherpad-lite](http://pads.services.ffhb.de/) kollaboratives Schreiben von Texten
* [Gogs](http://gogs.io)-Instanz: https://git.ffhb.de (mortzu)
* [Firmware](http://downloads.bremen.freifunk.net/firmware/)-Mirror: http://[2001:bf7:540::84]/
* [torproject.org](https://www.torproject.org)-Mirror: http://[2001:bf7:540::82]/torproject.org/

## Infos zum aktuellen Router
Unter http://node.ffhb.de findest du Informationen zu dem Router, mit dem du momentan verbunden bist.

## IPv4-Adressen
Folgende IP-Adressen sind vergeben:

* 10.196.0.0/17
    * 10.196.0.1 – 10.196.0.9 VPN-Server
      * 10.196.0.1 vpn01 (DNS, Gateway)
      * 10.196.0.2 vpn02 (DNS, Gateway)
      * 10.196.0.3 vpn03 (DNS, Gateway)
      * 10.196.0.5 vpn05 (Testbetrieb, anon6789)
      * 10.196.0.6 vpn06 (Testbetrieb, corny)
    * 10.196.0.10 – 10.196.0.39 Dienste-Server
      * 10.196.0.10   Monitoring - OMD site (genofire)
    * 10.196.0.42 server, mumble, experimentell (diega)
    * 10.196.0.60 notebook (bis dhcp zuverlässig läuft (diega))
    * 10.196.0.70 anon6789
    * 10.196.0.90-94 genofire
    * 10.196.0.100 Dienste von Lorenz
    * 10.196.0.101 Küchenchef 3000
    * 10.196.0.111 ec8or (u.a. Firmware-Mirror)
    * 10.196.0.123 rbtz 
    * 10.196.0.127 node.ffhb.de
    * 10.196.0.128 alternativer DNS Server (mortzu)
    * 10.196.0.129-159 Dienste von mortzu
    * 10.196.0.196 Dienste von Eike
    * 10.196.0.200 Dienste von jplitza
    * 10.196.0.240 Dienste von proxyhb
    * 10.196.10.0 - 10.196.19.255 per DHCP vergeben von 10.196.0.1
    * 10.196.20.0 - 10.196.29.255 per DHCP vergeben von 10.196.0.2
    * 10.196.30.0 - 10.196.39.255 per DHCP vergeben von 10.196.0.3
    * 10.196.50.0 - 10.196.59.255 per DHCP vergeben von 10.196.0.5
    * 10.196.60.0 - 10.196.69.255 per DHCP vergeben von 10.196.0.7
  * 10.196.123.0/24 Range von Ixoid
    * 10.196.123.42 GartenPi
* 10.196.126.0/24
  * 10.196.126.0/24 Dienste von Nebirosh
* 10.196.127.0/24
  * 10.196.127.1 Scanner an ffhb-asm100
  * 10.196.127.2 Scanner an ffhb-dvb15
  * 10.196.127.3 Linux-ISO-Server an ffhb-asm100 (in Vorbereitung)



Feste IP-Adressen von an Freifunk-Knoten angeschlossenen Servern sollten in 10.196.0.0/24 liegen. Hier eintragen und glücklich sein.

## IPv6-Adressen
mortzu hat bei bei SixXS das ULA-Netz fd2f:5119:0f2c::/48 registriert. Wir haben aber auch den globalen Bereich 2001:bf7:540::/43 vom Freie Netze e.V. Momentan werden beide verteilt, in der Firmware ist das ULA-Netz eingetragen.

global
  * 2001:bf7:540::1-6 VPN-Server
  * 2001:bf7:540::a  Monitoring - OMD site (genofire)
  * 2001:bf7:540::5b-5f (genofire)
  * 2001:bf7:540::f0 (proxyhb)
  * 2001:bf7:540::6f ec8or (u.a. Firmware-Mirror)

  
## Andere Netze
Aus dem Bremer Freifunk-Netz heraus erreichst du auch die Freifunk-Netze andere Städte und deren Dienste, beispielsweise [jene in Lübeck](http://luebeck.freifunk.net/wiki/Freifunk-verwenden). Auch zu anderen Netzen wie dem [dn42](http://dn42.net) oder [Chaos-VPN](http://wiki.hamburg.ccc.de/index.php/ChaosVPN) besteht eine Verbindung.