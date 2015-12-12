# Versions-Changelog
## Freifunk Bremen Versionen
### 2015.1.2+bremen2 (09.11.2015)
* Gluon-Version: [2015.1.2](#gluon-versionen_2015-1-2)
* signing-keys hinzugefügt von:
  * SimJoSt
  * oliver
  * janeric
  * ec8or
  * ProXyhb

##### Features die nach dem Testbetrieb für die stable-Version wieder entfernt wurden
* VPNs 04,05,06 hinzugefügt  
  Test, ob per Ansible aufgesetzte VPNs einwandfrei funktionieren

### 2015.1.2+bremen1~testing
* Gluon-Version: [2015.1.2](#gluon-versionen_2015-1-2)

### 2015.1.1+bremen1
* Gluon-Version: [2015.1.1](#gluon-versionen_2015-1-1)
* Node-Namen-Präfix `ffhb-` nicht mehr standardmäßig vorgegeben

### 2014.4+bremen0 - **erste Stable** ([28.06.2015](http://bremen.freifunk.net/blog/2015/06/28/Erste-stabile-Firmware.html))
*urspr. 0.6~testing1 ([03.05.2015](http://bremen.freifunk.net/blog/2015/05/03/Neue-Firmware.html))*
* Gluon-Version: [2014.4](#gluon-versionen_2014-4)

### 0.5~testing5 ([06.09.2014](http://bremen.freifunk.net/blog/2014/09/06/Neue-Testing-Channel-Survey.html))
* Gluon-Version: [2014.3](#gluon-versionen_2014-3)
* Kanalanalyse-Komponenten integriert
* WLAN-Feintuning
  * 2,4Ghz-Kanalbreite von 40Mhz auf 20Mhz reduziert
  * Multicast-Rate auf 6 Mbit/s herabgesetzt (die Grenze ab wann 2 Knoten Meshen/sich verbinden)
* DHCP-Server und IPv6-Router hinter einem Node werden nicht mehr durchgelassen ("Funktion Internet" im Freifunk-Netz sonst leicht störbar)

### 0.5~testing4 ([08.08.2014](http://bremen.freifunk.net/blog/2014/08/08/Neue-Testing.html))
* Gluon-Version: [2014.3](#gluon-versionen_2014-3)
* Ende der WLAN-Probleme (mit Überwachung evtl. Probleme)
* Autoupdater standardmäßig an

### 0.5~testing3 ([23.06.2014](http://bremen.freifunk.net/blog/2014/06/23/Facebook-und-Testing-3.html))
* Gluon-Version: [2014.2](#gluon-versionen_2014-2)
* Mesh-ESSID von batman.bremen.freifunk.net zu mesh.ffhb geändert um Verwirrung zu vermeiden
* neue WLAN-Treiber und -Software, dadurch hoffentlich keine Signal-Abbruch-Probleme mehr
* vom Knoten übertragene Statistik wird nun komprimiert
* Probleme mit TP-LINK TL-WR841N/ND v9 behoben
* Firewall block alles Eingehende auf dem WAN-Port außer SSH

### 0.5~testing2
* Gluon-Version: [2014.2](#gluon-versionen_2014-2)

#### bekannte Probleme
* Signal-Abruch-Problem auf 2,4Ghz
* TP-LINK TL-WR841N/ND v9 macht Probleme


### 0.5~testing1 - **erste Testing** ([24.03.2014](http://bremen.freifunk.net/blog/2014/03/24/testing-firmware.html))
* Gluon-Version: [2014.2](#gluon-versionen_2014-2)
* alle Nightly-Geräte haben auf den Testing-Branch gewechselt
* Doppel-Key-Problem behoben



## Gluon-Versionen
Hier aufgeführt sind die von Freifunk Bremen genutzten Gluon-Versionen mit einer kurzen Zusammenfassung von relevanten Änderungen.

### [2015.1.2](http://gluon.readthedocs.org/en/v2015.1.2/releases/v2015.1.2.html)
* Unterstützung für mehr Geräte
* eigene Images (nur umbenannte Kopien) für einige Ubiquiti Geräte, welche bis jetzt das Bullet M Image benutzen mussten, für mehr Klarheit und Einfachheit
* Download-Link von OpenSSL korrigiert

### [2015.1.1](http://gluon.readthedocs.org/en/v2015.1.2/releases/v2015.1.1.html)
* Unterstützung für ein weiteres Gerät
* Download-Link von OpenSSL korrigiertd
* Problem mit der LED-Anzeige für die Signalstäkre bei TP-LINK CPE210/510 behoben

### [2015.1](http://gluon.readthedocs.org/en/v2015.1/releases/v2015.1.html)
* Unterstützung für mehr Geräte
* Zweisprachiger Config-Mode (Deutsch; Englisch)
* Mesh-on-LAN
* Option um Mesh oder Client Netzwerke standardmäßig auszuschalten
* fastd "performance mode" mit ausgeschalteter Verschlüsselung
* optionales Feld für Höhe in Geo-Daten
* Vorbereitung von announced um alfred zu ersetzen
* Option um beim Aufruf des Autoupdaters temporär einen anderen Branch zu wählen
* vorgegebenes Namens-Prefix jetzt optional

### [2014.4](http://gluon.readthedocs.org/en/v2014.4/releases/v2014.4.html)
* Update auf OpenWRT 14.09 (Barrier Breaker)  
  mehr Stabilität und mehr Performance
* Unterstützung für mehr Geräte
* Privates WLAN bridged with WAN möglich
* fastd v16 mit UMAC  
  mehr Sicherheit und Performance
* Option um SSH-Keys fest in die Firmware zu integrieren
* Node-Status-Page erkennt Nachbar-Nodes und zeigt ihre Namen an und macht sie klickbar

### [2014.3](http://gluon.readthedocs.org/en/v2014.4/releases/v2014.3.html)
* Unterstützung für ein weiteres Gerät
* Autoupdater wurde neugeschrieben
  * geplante Updates mit Datumsangabe möglich
  * zeitlich verteiltes Update möglich mit Angabe eines Zeitraums
* erste Implementation von announced für querys von nodeinfo Daten für zukünftige Statuspage
* erste Implementation für fastd/VPN über IPv6
* Mesh-on-WAN hinzugefügt
* site.conf wird nach dem Kompilieren validiert
* ath9k verbessert für bessere WLAN Stabilität
* IPv6 nun präferiert für wget (Autoupdater und NTP)

### 2014.2
#### Bugfixes:
* Stark verbesserte Stabilität des ath9k-WLAN-Treibers (besonders auf
TP-Link-Hardware; auf einigen Ubiquiti-Geräten scheint es zwar besser
geworden zu sein, aber noch immer problematisch)

* Gluon-Knoten beantworten keine DNS-Requests auf dem WAN-Port mehr (war
problematisch bei Nodes mit öffentlicher IP auf dem WAN-Port wegen DNS
Amplification Attacks)

#### Support für neue Hardware:
* TP-Link TL-WR841N/ND v9
* TP-Link TL-WR842N/ND v2
* TP-Link TL-WA901N/ND v2
* TP-Link TL-MR3420 v2
* D-Link DIR-615 rev. E1
* D-Link DIR-825 rev. B1

#### Änderungen unter der Haube:
* Neues site.conf-Format auf Lua-Basis. Die site.conf wird jetzt als
ganzes Teil der Firmware, was sie deutlich flexibler macht. Ein guter
Teil unserer Scripte in der Firmware wurde von Shell nach Lua portiert.
(Aktuell wird beim Bauen nur die Syntax der site.conf überprüft, nicht
aber ob der Inhalt sinnvoll ist... das wird im nächsten Release behoben)
* gluon-alfred sendet seine Daten jetzt gzip-komprimiert (großer
Vorteil: ein Datenpaket passt jetzt in einen einzelnen Ethernet-Frame)
* Verschiedense Erweiterungen der Daten, die gluon-alfred sammelt
(Speicherverbrauch, Anzahl der Prozesse)
* Viele OpenWrt-make-targets funktionieren jetzt auch mit Gluon (z.B.
`make package/fastd/install` um das Paket fastd zu bauen, und `make
target/linux/clean`, um den Kernel-Tree zu säubern)
* Neue Option opkg_repo in der site.conf, um das Default-opkg-Repo zu
überschreiben

Support für nicht-ar71xx-Platformen und VPN-Verbindungen über
IPv6-Internet-Anschlüsse haben es leider nicht mehr in dieses Release
geschafft, das wird dann in Gluon 2014.3 nachgeliefert :D