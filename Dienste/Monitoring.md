
## Verfügbar
* [InterCity VPN](http://icvpn.wg1337.de) Monitoring der verschiedenen Freifunk-Communities 
* [Meshviewer](http://bremen.freifunk.net/meshviewer/) interessante Darstellung unseres Netzes mit Daten zu Punkten wie einer Übersicht (neue und verschwundene Router), Knoten (alle Netzknoten mit Uptime und Anzahl der verbundenen Geräte), Verbindungen (Verbindungs-Qualität und Entfernung der im Router hinterlegten Geo-Koordinatender Funkstrecken) und Statistiken (eingesetzte Software/Hardware, Software- und Softwareupdate-Mechanismen).
* [node.ffhb.de](http://node.ffhb.de) Netzwerk-Daten wie IP-Adressen und Uptime-Infos von dem Router, mit dem man gerade physisch verbunden ist. Eventuell auch Links zum nächsten Router, falls verfügbar.
* [Knotenkarte](http://bremen.freifunk.net/map/geomap.html) Ein ältere Variante des Meshviewers. Enthält drei Bereiche:
  * [Karte](http://bremen.freifunk.net/map/geomap.html) Zeigt die Knoten und Meshverbindungen auf einer Karte an.
  * [Statistik](http://bremen.freifunk.net/map/stats.html) Graph, der die Anzahl der verbundenen Clients und aktiven Knoten darstellt. 
  * [Liste](http://bremen.freifunk.net/map/list.html) Zeigt eine Liste aller bekannten Knoten mit ein paar Details: Name, Anzahl Clients, Anzahl Meshverbindungen, sind Koordinaten hinterlegt?, Routermodell, installierte Firmware-Version. Von dieser Liste aus kann man auf die Knotenstatistik eines Knoten navigieren.
  * Knotenstatistik, z.B. [ffhb-14cc2030cade](http://bremen.freifunk.net/map/node.html?id=16:d0:20:30:ca:de). Zeigt die primäre MAC-Adresse, das Modell, die Firmware-Version und ggf. die Koordinaten an. Zusätzlich gibt es grafische Statistiken: Anzahl der Clients, Meshingverbindungen, Prozessorauslastung, gesendete und empfangene Pakete oder Bytes. Die letzten beiden verfügen über mehrere Graphen die wie folgt zu interpretieren sind:
    * **rx_*** ist das, was der Knoten runtergeladen hat
    * **tx_*** ist das, was der Knoten gesendet hat
    * **\*\_mgmt_*** sind Daten die zum Verwalten des Netzes nötig sind, nämlich Routing-Informationen für Batman selbst (z.B. welcher Client an welchem Knoten hängt).
* [Freifunk-Karte](http://www.freifunk-karte.de/) Die Karte nutzt die [Freifunk-API](https://api.freifunk.net/), um eine Liste der Communities in Deutschland zu beziehen. Aus deren API-Files werden dann die Links zu Knotenkarten gelesen. Die Karte wurde von [Tino Dietel](https://github.com/stilgarbf), FF Emskirchen gebaut.
* [VPN-Server-Status](http://status.ffhb.mortzu.de/) Zeigt den Status der VPN-Server an, gemessen von mehreren Monitoring-Clients im Freifunk-Netz.

Viel Spass beim Erkunden und Verbessern unseres Netzes!<br/>
PS. Wenn Ihr neues zum Monitoring beitragen könnt, bitte eintragen. DANKE