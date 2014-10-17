Im Freifunk-Netz kann man nicht nur das Internet benutzen. Jeder kann eigene Dienste anbieten, die wir auf dieser Seite sammeln wollen:

* [Wikipedia-Mirror (mit Bildern)](http://wikipedia.ffhb)
* [Tahoe-LAFS](Dienste/Tahoe-LAFS)
* [Smokeping](http://smokeping.bremen.freifunk.net/smokeping/smokeping.cgi) Erreichbarkeitsmessung zu verschiedenen Zielen
* [Straßenbahn-Fahrplan Sielwall](http://10.196.0.69) Echtzeit Haltestellendaten (noch Testbetrieb)
* [Freifunk Store](http://10.196.0.69/ff_store/) unkommerzielle Router-, Antennen und Teilebörse

## Infos zum aktuellen Router
Unter http://node.ffhb/ findest du Informationen zu dem Router, mit dem du momentan verbunden bist.

## IP-Adressen

Folgende IP-Adressen sind vergeben:

* 10.196.0.0/17
    * 10.196.0.1 VPN-Server (mortzu)
    * 10.196.0.2 VPN-Server (jplitza)
    * 10.196.0.3 zukünftiger VPN-Server (?) (Julian)
    * 10.196.0.69 S-Bahn Fahrplan + Store (anon6789)
    * 10.196.0.100 Tahoe-LAFS node (mortzu)
    * 10.196.0.101 DNS-Server (mortzu)
    * 10.196.0.102 Tahoe-LAFS node (mortzu)
    * 10.196.0.127 node.ffhb
    * 10.196.0.196 Dienste von Eike
    * 10.196.0.200 Dienste von jplitza
    * 10.196.1.2-10.196.1.254 per DHCP vergeben von 10.196.0.1
    * 10.196.2.2-10.196.2.254 per DHCP vergeben von 10.196.0.2
* 10.196.128.0/17
    * 10.196.128.0/27 Dienste von mortzu
        * 10.196.128.1 DNS-Server
        * 19.196.128.2 HTTP-Server (Firmware)

Feste IP-Adressen von an Freifunk-Knoten angeschlossenen Servern sollten denke ich erstmal in 10.196.0.0/24 liegen. Einfach hier eintragen und nehmen. Wenn der Bereich voll ist können wir immer noch die DHCP-Bereiche verschieben.

## Andere Netze
Aus dem Bremer Freifunk-Netz heraus erreichst du auch die Freifunk-Netze andere Städte und deren Dienste, beispielsweise [jene in Lübeck](http://luebeck.freifunk.net/wiki/Freifunk-verwenden). Auch zu anderen Netzen wie dem [dn42](http://dn42.net) oder [Chaos-VPN](http://wiki.hamburg.ccc.de/index.php/ChaosVPN) besteht eine Verbindung.