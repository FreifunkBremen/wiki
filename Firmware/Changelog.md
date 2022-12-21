# Firmwareversions Changelog

Diese Seite dokumentiert oberflächlich und als Übersicht alle Änderungen an der Freifunk Bremen Firmware sowie den zugrunde liegenden Gluon Versionen. Für detailliertere Änderungen kann den jeweiligen Links zum Quellcode gefolgt werden.

- [**Freifunk Bremen Versionen**](#freifunk-bremen-versionen)  
  eine Liste aller Freifunk Bremen Firmware Versionen mit allen Bremen-spezifischen Änderungen sowie bedeutenden Änderungen beim Sprung auf eine neue Gluon Basis
- [**Gluon Versionen**](#gluon-versionen)  
  eine Liste aller Gluon Versionen mit einer übersetzten und vereinfachten Liste der Neuerungen und Fehlerkorrekturen


## Freifunk Bremen Versionen

Der Quellcode der Freifunk Bremen Firmware liegt bei [Github](https://github.com/FreifunkBremen/gluon-site-ffhb).  
Die verschiedenen Varianten der Freifunk Bremen Firmware werden auf entsprechenden [[Varianten]]-Wiki-Seite erklärt. Die Firmware-Images der Freifunk Bremen Software sind auf dem [Download-Server](https://downloads.bremen.freifunk.net/firmware/) zu finden.  
Alte Firmwares werden aus Platzgründen vom Download-Server gelöscht, werden aber für gewöhnlich vorher archiviert und können über die Mailingliste angefragt werden.  
Die jeweiligen Unterordner haben folgende Bedeutungen:


- [**`all`**](https://downloads.bremen.freifunk.net/firmware/all/) listet die Ordner aller einzelnen Versionen der Freifunk Bremen Firmware auf.  
- [**`nightly`**](https://downloads.bremen.freifunk.net/firmware/nightly/) verweist auf den gleichen Inhalt wie [**`testing`**](https://downloads.bremen.freifunk.net/firmware/testing/), da wir aktuell keine nächtlichen Builds erstellen und veröffentlichen.
- [**`stable`**](https://downloads.bremen.freifunk.net/firmware/stable/) verweist auf die Images der aktuell als stabil deklarierten Firmwareversion.  
- [**`testing`**](https://downloads.bremen.freifunk.net/firmware/testing/) verweist auf die Images der aktuell im Test befindlichen Firmwareversion.

*Falls sich Geräte auf dem `exp`-Branch befinden, so werden sie keine Updates beziehen, da dies kein offizieller Branch ist und die Einstellung durch einen Fehler entstanden ist.  
Experimentelle Firmware-Versionen werden nicht offiziell unterstützt und werden meist für extrem frühe Tests verwendet. Normalerweise sollte als Branch `testing` eingestellt sein, damit sie sich später bei einer stabilen Veröffentlichung Updates holen.*

Branch        | aktuelle Version                                                    | signed by
---           | ---                                                                 | ---
**`stable`**  | [2019.1.3+bremen8](#2019-1-3-bremen3)     | `oliver`, `jplitza`
**`testing`** | [2021.1.2+bremen1](#2021-1-2-bremen1)     | `oliver`?

Es folgt eine Liste aller Freifunk Bremen Firmware-Versionen mit allen Bremen-spezifischen Änderungen sowie bedeutenden Änderungen beim Sprung auf eine neue Gluon Basis.

### 2022.1.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [noch nicht](https://downloads.bremen.freifunk.net/firmware/all/2022.1.1+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [noch nicht](https://downloads.bremen.freifunk.net/firmware/all/2022.1.1+bremen1/sysupgrade/testing.manifest)
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2022.1.1+bremen1) / [Commits/Compare](https://github.com/FreifunkBremen/gluon-site-ffhb/compare/v2021.1.2+bremen1...v2022.1.1+bremen1)  
**gluon-Version**: [2022.1.1](#2022-1-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2022.1.1+bremen1/)

Diese Version ist nur eine Update auf der neuen Gluon-Version:
- site config dafür angepasst

### 2021.1.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [noch nicht](https://downloads.bremen.freifunk.net/firmware/all/2021.1.2+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [21.11.2022](https://downloads.bremen.freifunk.net/firmware/all/2021.1.2+bremen1/sysupgrade/testing.manifest)
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2021.1.2+bremen1) / [Commits/Compare](https://github.com/FreifunkBremen/gluon-site-ffhb/compare/v2019.1.3+bremen8...v2021.1.2+bremen1)  
**gluon-Version**: [2021.1.2](#2021-1-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2021.1.2+bremen1/)

Diese Version ist die erste neue Version nach der Umstellung auf Batman v15:
- default site (falls per SSH installiert) auf ffhb_batv15
- entfernen von alten site config (ffhb\_11s und ffhb\_legacy)
- build.sh angepast für neuen gluon.sh
- haveged durch urngd ersetzt

### 2019.1.3+bremen8
**Veröffentlichung auf dem `stable`-Branch**: [21.06.2022](https://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen8/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [20.06.2022](https://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen8/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.3+bremen8) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.3+bremen8)  
**gluon-Version**: [2019.1.3+ (git250b623f)](#2019-1-3-git250b623f)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen8/)

Diese Version wird für die Umstellung auf Batman v15 verwendet werden und enthält die nötigen letzten Anpassungen:
- die automatische Umschaltung auf das v15-Netz (mittels ["gluon-scheduled-domain-switch"](https://gluon.readthedocs.io/en/v2019.1.3/package/gluon-scheduled-domain-switch.html)) wurde aktiviert, für Fr 1. Jul 02:00:00 CEST 2022
- die Namen der verfügbaren Freifunk-Domains wurden angepasst (das v15-Netz ist jetzt nicht mehr "experimentell", sondern ist das "neue Netz")
- die zukünftigen Gateway-Server vpn09 und vpn10 werden jetzt auch als DNS- und NTP-Server verwendet
- der VPN-Key von vpn10 wurde korrigiert

### 2019.1.3+bremen7
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [14.06.2022](https://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen7/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.3+bremen7) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.3+bremen7)  
**gluon-Version**: [2019.1.3+ (git250b623f)](#2019-1-3-git250b623f)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen7/)

- das Batman-v15-Testnetz wird jetzt im Config-Modus wieder angezeigt (als "Freifunk Bremen - Experimentelles Netz (mit Batman v15)")

### 2019.1.3+bremen6
(wurde nie erfolgreich gebaut)

### 2019.1.3+bremen5
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.3+bremen5) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.3+bremen5)  
**gluon-Version**: [2019.1.3+ (git250b623f)](#2019-1-3-git250b623f)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen5/)

In dieser Version gibt es nur diverse Änderungen für das Batman-v15-Testnetz:
- für Kabel-Mesh-Verbindungen wird jetzt [VXLAN](https://gluon.readthedocs.io/en/latest/features/wired-mesh.html#wired-mesh-encapsulation) verwendet. Das betrifft nur das Batman-v15-Netz! Im v13-Modus (also im derzeitigen "stabilen" Netz) wird VXLAN nicht verwendet.
- der experimentelle VPN-Server vpn04 wurde entfernt, und stattdessen wurden die regulären neuen Server vpn07/08/09/10 hinzugefügt
    - die Server vpn09 und 10 sind allerdings noch nicht in Betrieb
- es werden jetzt die korrekten DNS- und NTP-Server verwendet

### 2019.1.3+bremen4
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.3+bremen4) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.3+bremen4)  
**gluon-Version**: [2019.1.3+ (git250b623f)](#2019-1-3-git250b623f)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen4/)

- diese Firmware kann sich jetzt wieder zu unserem Batman-v15-Testnetz verbinden (diese Möglichkeit war in der [2019.1.3+bremen3](#2019-1-3-bremen3) verloren gegangen). Um das Testnetz zu verwenden, muss die Freifunk-Domain per SSH umgestellt werden (mittels `uci set gluon.core.domain='ffhb_batv15' && gluon-reconfigure && gluon-reload && uci commit`).

### 2019.1.3+bremen3
**Veröffentlichung auf dem `stable`-Branch**: [06.05.2022](https://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen3/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [06.05.2022](https://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen3/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.3+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.3+bremen3)  
**gluon-Version**: [2019.1.3+ (git250b623f)](#2019-1-3-git250b623f)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen3/)

- Update auf Gluon 2019.1.3, worin neben einigen kleineren Fehlern auch eine sehr kritische Sicherheitslücke behoben wurde.
    - Details zu der Sicherheitslücke (CVE-2022-24884) stehen u.a. unter [https://github.com/freifunk-gluon/gluon/security/advisories/GHSA-xqhj-fmc7-f8mv](https://github.com/freifunk-gluon/gluon/security/advisories/GHSA-xqhj-fmc7-f8mv) und [https://forum.freifunk.net/t/security-critical-vulnerability-in-gluon-bugfix-release-on-thursday-2022-05-05/23329](https://forum.freifunk.net/t/security-critical-vulnerability-in-gluon-bugfix-release-on-thursday-2022-05-05/23329) .

### 2019.1.3+bremen2
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.3+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.3+bremen2)  
**gluon-Version**: [2019.1.3](#2019-1-3)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.3+bremen2/)

- Update auf Gluon 2019.1.3, mit einigen kleineren Fehlerbehebungen
- Batman v15 verbindet sich zu vpn04 jetzt auf Port 50000 (statt 50001)
- Batman v15 versucht sich auch zu vpn01/2/3/5/6 zu verbinden, jeweils auf Port 50001; damit sind wir darauf vorbereitet, dass diese Server irgendwann ebenfalls auf Batman v15 umgestellt werden

### 2019.1.2+bremen4
**Veröffentlichung auf dem `stable`-Branch**: nie   
**Veröffentlichung auf dem `testing`-Branch**: [27.01.2021](https://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen4/sysupgrade/testing.manifest)   
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.2+bremen4) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.2+bremen4)  
**gluon-Version**: [2019.1.2](#gluon-versionen_2019-1-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen4/)

Diese Version ist eine Vorbereitung für den Wechsel auf eine neue Batman-Version (also eine neue Version des Mesh-Protokolls).
Man kann jetzt im Config-Modus wieder die Domain auswählen:
- "Freifunk Bremen (mit 11s Mesh-Unterstützung)" aktiviert das alte (bisherige) Protokoll, womit sich der Knoten mit dem normalen Bremer Freifunk-Netz verbindet
- "Freifunk Bremen neu (mit Batman v15 - Testnetz)" aktiviert das neue Protokoll; der Knoten verbindet sich dann mit einem neuen Testnetz, das über den vpn04-Server läuft

### 2019.1.2+bremen3
**Veröffentlichung auf dem `stable`-Branch**: [21.09.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen3/sysupgrade/stable.manifest)   
**Veröffentlichung auf dem `testing`-Branch**: [04.09.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen3/sysupgrade/testing.manifest)   
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.2+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.2+bremen3)  
**gluon-Version**: [2019.1.2](#gluon-versionen_2019-1-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen3/)

- es wird jetzt eine "[Offline-SSID](https://github.com/FreifunkBremen/gluon-site-ffhb/issues/35)" ausgestrahlt, wenn der Knoten keine Internetverbindung hat (genauer: wenn er den VPN-Server nicht erreichen kann). Diese SSID lautet "FF_offline_*Knotenname*".

### 2019.1.2+bremen2
**Veröffentlichung auf dem `stable`-Branch**: [20.07.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen2/sysupgrade/stable.manifest)   
**Veröffentlichung auf dem `testing`-Branch**: [04.04.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen2/sysupgrade/testing.manifest)   
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.2+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.2+bremen2)  
**gluon-Version**: [2019.1.2](#gluon-versionen_2019-1-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen2/)

- Outdoor-Geräte mit 5GHz-WLAN können jetzt offiziell und legal draußen verwendet werden. Dazu gibt es auf der Config-Seite des Knotens neue Optionen zur Outdoor-Installation, mit denen man angeben kann, dass das Gerät draußen benutzt werden soll.  
Wenn dies aktiviert ist, werden spezielle Outdoor-Kanäle verwendet (Kanäle 100 bis 140), [DFS](https://de.wikipedia.org/wiki/Dynamic_Frequency_Selection) wird aktiviert, und Mesh-Verbindungen auf 5GHz werden deaktiviert (weil Meshing einen stabilen Kanal erfordert, aber DFS den Kanal ändern könnte).

### 2019.1.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie   
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.2+bremen1)  
**gluon-Version**: [2019.1.2](#gluon-versionen_2019-1-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.2+bremen1/)

- Update auf [Gluon 2019.1.2](#gluon-versionen_2019-1-2)

### 2019.1.1+bremen3
**Veröffentlichung auf dem `stable`-Branch**: [07.04.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.1+bremen3/sysupgrade/stable.manifest)   
**Veröffentlichung auf dem `testing`-Branch**: [07.03.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.1+bremen3/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.1+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.1+bremen3)  
**gluon-Version**: [2019.1.1](#gluon-versionen_2019-1-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.1+bremen3/)

- SSH-Zugang ist jetzt auch wieder per Passwort möglich (anstatt nur per SSH-Key)
- im Config-Modus kann man die Knotenposition jetzt auf einer Karte auswählen. Dazu muss der Browser aber Internetzugang haben; falls das nicht der Fall ist, kann man die Position aber auch weiterhin über geografische Koordinaten eingeben

### 2019.1.1+bremen2
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [26.02.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.1+bremen2/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.1+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.1+bremen2)  
**gluon-Version**: [2019.1.1](#gluon-versionen_2019-1-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.1+bremen2/)

- **11s als Standard aktiviert, als Abschluss des Domainwechsels.**

### 2019.1.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [20.01.2020](https://downloads.bremen.freifunk.net/firmware/all/2019.1.1+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1.1+bremen1)  
**gluon-Version**: [2019.1.1](#gluon-versionen_2019-1-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1.1+bremen1/)

- Update auf [Gluon 2019.1.1](#gluon-versionen_2019-1-1)
- Umschalt-Automatik für den Wechsel von IBSS-Mesh auf 802.11s:
  - man kann jetzt im Config-Modus die Domain (11s/neu oder IBSS/alt) auswählen
  - am 5.3.2020 um 01:00 morgens wird der Knoten automatisch auf 11s umschalten
  - falls der Knoten zwei Stunden lang offline ist, wird er ebenfalls automatisch auf 11s umschalten (das ist nötig, weil Knoten nach dem Einschalten erstmal keine korrekte Uhrzeit haben)
- auf Geräten ohne WLAN-Chip (z.B. VPN-Offloader) sollte es jetzt keine Warnungen über fehlende Airtime-Informationen mehr geben

### 2019.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [19.01.2020](http://downloads.ffhb.de/firmware/all/2019.1+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [14.10.2019](https://downloads.bremen.freifunk.net/firmware/all/2019.1+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2019.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2019.1+bremen1)  
**gluon-Version**: [2019.1](#gluon-versionen_2019-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2019.1+bremen1/)

- **Update auf [Gluon 2019.1](#gluon-versionen_2019-1)**
  - neu unterstützte Geräte:
      - D-Link DAP-1330 A1
      - TP-Link CPE210 v3

### 2018.2.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [15.10.2019](https://downloads.bremen.freifunk.net/firmware/all/2018.2.2+bremen1/sysupgrade/stable.manifest)   
**Veröffentlichung auf dem `testing`-Branch**: [27.07.2019](https://downloads.bremen.freifunk.net/firmware/all/2018.2.2+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.2.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.2.2+bremen1)  
**gluon-Version**: [2018.2.2](#gluon-versionen_2018-2-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.2.2+bremen1/)

- **Update auf [Gluon 2018.2.2](#gluon-versionen_2018-2-2)**
  - Sicherheitslücken im Linux-Kernel ("SACK-Lücke" etc.) wurden geschlossen (CVE-2019-11477, CVE-2019-11478 und CVE-2019-11479). Durch diese Lücken konnte der Knoten aus der Ferne zum Absturz gebracht werden.
  - die Anzahl der Nicht-WLAN-Clients auf der Karte sollte jetzt genauer sein.
  - die Statusseite (und der DNS-Server im Knoten) sollten jetzt weiterhin korrekt funktionieren, selbst wenn ein anderer Knoten im Freifunk-Netz die reservierte Next-Node-MAC-Adresse verwendet.
  - Onion-Omega-Geräte werden nicht mehr unterstützt.

### 2018.2.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [09.08.2019](https://downloads.bremen.freifunk.net/firmware/all/2018.2.1+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [11.05.2019](https://downloads.bremen.freifunk.net/firmware/all/2018.2.1+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.2.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.2.1+bremen1)  
**gluon-Version**: [2018.2.1](#gluon-versionen_2018-2-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.2.1+bremen1/)

- **Update auf [Gluon 2018.2.1](#gluon-versionen_2018-2-1)**
    - "Scheduled domain switch"-Funktion ist jetzt vorhanden (wird aber derzeit in Bremen noch nicht genutzt)
    - einige Fehlerbehebungen und Änderungen
    - neu unterstützte Geräte:
      - Fritz!WLAN Repeater 300E

### 2018.2+bremen3
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [04.01.2019](https://downloads.bremen.freifunk.net/firmware/all/2018.2+bremen3/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.2+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.2+bremen3)  
**gluon-Version**: [2018.2](#gluon-versionen_2018-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.2+bremen3/)

* keine Änderungen; das Release ist identisch mit [2018.2+bremen1](#freifunk-bremen-versionen_2018-2-bremen1). Die Versionsnummer wurde nur geändert, um einen Neubau zu erzwingen.


### 2018.2+bremen2
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.2+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.2+bremen2)  
**gluon-Version**: [2018.2](#gluon-versionen_2018-2)  
**Download**: (nicht erfolgreich gebaut)

* keine Änderungen; das Release ist identisch mit [2018.2+bremen1](#freifunk-bremen-versionen_2018-2-bremen1). Die Versionsnummer wurde nur geändert, um einen Neubau zu erzwingen.


### 2018.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.2+bremen1)  
**gluon-Version**: [2018.2](#gluon-versionen_2018-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.2+bremen1/)

- **Update auf [Gluon 2018.2](#gluon-versionen_2018-2)**
  - Gluon basiert ab jetzt wieder auf OpenWRT statt auf LEDE (nachdem LEDE und OpenWRT wieder zusammengeführt wurden)
  - die Menge an ARP-Paketen, die ein Endgeräte versenden darf, ist jetzt [begrenzt](https://gluon.readthedocs.io/en/v2018.2/package/gluon-ebtables-limit-arp.html): es dürfen bis zu 6 Pakete pro Minute und 1 Paket pro Sekunde verschickt werden (sowie ein "Burst" von bis zu 50 Paketen). Davon ausgenommen sind Anfragen nach MAC-Adressen, die schon von anderen Clients angefragt wurden (z.B. Gateways oder DNS-Server).  
Durch diese Begrenzung soll verhindert werden, dass IPv4-Scans das ganze Netzwerk beeinträchtigen.
    - neu unterstützte Geräte:
        - AVM Fritz!WLAN Repeater 450E
        - OCEDO Koala
        - TP-Link Archer C7 v5
        - TP-Link TL-WR810N v1
        - Ubiquiti UniFi AC Mesh Pro
        - ZyXEL NBG6616

### 2018.1.4+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.1.4+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.1.4+bremen1)  
**gluon-Version**: [2018.1.4](#gluon-versionen_2018-1-4)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.1.4+bremen1/)

- **Update auf [Gluon 2018.1.4](#gluon-versionen_2018-1-4)**
  - ein Fehler beim Versionsvergleich von Firmware-Updates wurde behoben ([#208](https://github.com/freifunk-gluon/packages/issues/208)). In diesem Zuge wurden auch gleich die Regeln für den Versionsvergleich angepasst, dass sie jetzt den Regeln von opkg/dpkg entsprechen.


### 2018.1.3+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.1.3+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.1.3+bremen1)  
**gluon-Version**: [2018.1.3](#gluon-versionen_2018-1-3)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.1.3+bremen1/)

- **Update auf [Gluon 2018.1.3](#gluon-versionen_2018-1-3)**
  - ein Fehler beim Laden von Kernel-Modulen (der u.a. den batman-adv-Treiber betraf) wurde behoben ([#1580](https://github.com/freifunk-gluon/gluon/issues/1580))


### 2018.1.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.1.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.1.2+bremen1)  
**gluon-Version**: [2018.1.2](#gluon-versionen_2018-1-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.1.2+bremen1/)

- **Update auf [Gluon 2018.1.2](#gluon-versionen_2018-1-2)**
  - respondd schickt jetzt die vollständige Liste der IPv6-Adressen eines Knotens ([#1523](https://github.com/freifunk-gluon/gluon/issues/1523))
  - die Knöpfe der FRITZ!Box 4020 haben jetzt das korrekte Verhalten ([#1544](https://github.com/freifunk-gluon/gluon/issues/1544))


### 2018.1.1+bremen3
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.1.1+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.1.1+bremen3)  
**gluon-Version**: [2018.1.1](#gluon-versionen_2018-1-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.1.1+bremen3/)

- [DNS-Forwarding](https://gluon.readthedocs.io/en/v2018.1.1/features/dns-forwarder.html) wurde aktiviert


### 2018.1.1+bremen2
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.1.1+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.1.1+bremen2)  
**gluon-Version**: [2018.1.1](#gluon-versionen_2018-1-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.1.1+bremen2/)

- es wird jetzt der korrekte ath10k-Treiber verwendet, wodurch bei Geräten mit diesem Treiber (z.B. TP-Link Archer C7) jetzt auch das 5-GHz-WLAN verwendet wird ([#1561](https://github.com/freifunk-gluon/gluon/issues/1561)). Dies gilt allerdings nur für Verbindungen zu WLAN-Endgeräten; Mesh-Verbindungen können bei ath10k-Geräten immer noch nicht über das 5-GHz-Band aufgebaut werden ([#1584](https://github.com/freifunk-gluon/gluon/issues/1584)).


### 2018.1.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [19.10.2018](https://downloads.bremen.freifunk.net/firmware/all/2018.1.1+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.1.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.1.1+bremen1)  
**gluon-Version**: [2018.1.1](#gluon-versionen_2018-1-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.1.1+bremen1/)

- **Update auf [Gluon 2018.1.1](#gluon-versionen_2018-1-1)**
  - Autoupdater-Problem aus 2018.1 behoben
  - ARP-Problem aus 2018.1 behoben
  - Kompilier-Probleme auf neueren Betriebssystemen (mit glibc 2.28) behoben


### 2018.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2018.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2018.1+bremen1)  
**gluon-Version**: [2018.1](#gluon-versionen_2018-1)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2018.1+bremen1/)

**Update-Hinweis:** auf einigen Geräten (TP-Link CPE/WBS 210/510) wird jetzt für den Flash-Speicher ein neues Layout verwendet. Deshalb sollte vor dem Upgrade auf diese Version zuerst die 2017.1.8 installiert werden.

- **Update auf [Gluon 2018.1](#gluon-versionen_2018-1)** und damit etliche neue Funktionen und Fehlerbehebungen  
- neu unterstützte Geräte:
    - ALFA NETWORK
        - AP121F
    - AVM
        - FRITZ!Box 4020
    - LeMaker
        - Banana Pi (M1)
    - OpenMesh
        - A40
        - A60
        - OM2P v4
        - OM2P-HS v4
    - TP-Link
        - CPE210 v2
        - TL-WA901ND v5
    - ZyXEL
        - NBG6716

### 2017.1.8+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [13.08.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.8+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [18.06.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.8+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.8+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.8+bremen1)  
**gluon-Version**: [2017.1.8](#gluon-versionen_2017-1-8)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.8+bremen1/)

- **Update auf [Gluon 2017.1.8](#gluon-versionen_2017-1-8)** 
    - verschiedene Batman-Probleme behoben die zu viel Datenverkehr und hoher Last führen konnten
    - die Beschreibung des Kontaktinformations-Feldes im Konfigurationsmodus wurde um einen DSGVO-Passus erweitert
    - neue Geräte-Unterstützung
        - GL.iNet GL-AR750
        - TP-Link Archer C7 v4
        - TP-LINK TL-WR940N v6
        - Ubiquiti UniFi AC Mesh


### 2017.1.7+bremen2
**Veröffentlichung auf dem `stable`-Branch**: [18.06.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.7+bremen2/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [31.05.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.7+bremen2/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.7+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.7+bremen2)  
**gluon-Version**: [2017.1.7](#gluon-versionen_2017-1-7)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.7+bremen2/)

- Verringern des Timeouts von Originator-Informationen von IPv6-Gateways von 15 auf 5 Minuten


### 2017.1.7+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.7+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.7+bremen1)  
**gluon-Version**: [2017.1.7](#gluon-versionen_2017-1-7)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.7+bremen1/)

- **Update auf [Gluon 2017.1.7](#gluon-versionen_2017-1-7)**
    - Ein Problem mit dem Booten von Ubiquiti-Geräten wurde behoben.


### 2017.1.6+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [28.04.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.6+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.6+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.6+bremen1)  
**gluon-Version**: [2017.1.6](#gluon-versionen_2017-1-6)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.6+bremen1/)

- **Update auf [Gluon 2017.1.6](#gluon-versionen_2017-1-6)**
    - Das Abstürzen aller Knoten bei Neustart eines Gateways wurde behoben.
    - Der DNS-Cache auf den Knoten wurde deaktiviert, weil er Probleme mit DNSSEC verursacht hat.
- Backport eines Fixes für den gluon-radv-filterd, damit dieser die Originator von IPv6-Gateways regelmäßig neu auflöst.


### 2017.1.5+bremen2
**Veröffentlichung auf dem `stable`-Branch**: [09.04.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.5+bremen2/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [18.02.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.5+bremen2/sysupgrade/testing.manifest)   ([Blogpost](https://bremen.freifunk.net/blog/2018/02/23/neue-stable-2017-1-4-bremen2.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.5+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.5+bremen2)  
**gluon-Version**: [2017.1.5](#gluon-versionen_2017-1-5)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.5+bremen2/)

- Backport der aktuellen Version des [radv-filterd](https://gluon.readthedocs.io/en/latest/package/gluon-radv-filterd.html)


### 2017.1.5+bremen1
**Veröffentlichung auf dem `stable`-Branch**: Nie  
**Veröffentlichung auf dem `testing`-Branch**: Nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.5+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.5+bremen1)  
**gluon-Version**: [2017.1.5](#gluon-versionen_2017-1-5)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.5+bremen1/)

- **Update auf [Gluon 2017.1.5](#gluon-versionen_2017-1-5)**
    - neue Geräte-Unterstützung
        - TP-Link TL-WR1043N v5
        - Ubiquiti EdgeRouter-X
        - Ubiquiti EdgeRouter-X SFP
    - einige Fehlerbehebungen
- Aktivierung des [Knoten-lokalen DNS-Caches](https://gluon.readthedocs.io/en/v2017.1.x/features/dns-cache.html)


### 2017.1.4+bremen2
**Veröffentlichung auf dem `stable`-Branch**: [05.02.2018](https://downloads.bremen.freifunk.net/firmware/all/2017.1.4+bremen2/sysupgrade/stable.manifest)   ([Blogpost](https://bremen.freifunk.net/blog/2018/02/23/neue-stable-2017-1-4-bremen2.html))  
**Veröffentlichung auf dem `testing`-Branch**: [20.12.2017](https://downloads.bremen.freifunk.net/firmware/all/2017.1.4+bremen2/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.4+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.4+bremen2)  
**gluon-Version**: [2017.1.4](#gluon-versionen_2017-1-4)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.4+bremen2/)


- Inhaltlich identisch zu 2017.1.4+bremen1, nur ohne komisches + am Ende.


### 2017.1.4+bremen1 / 2017.1.4+bremen1+
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [16.12.2017](https://downloads.bremen.freifunk.net/firmware/all/2017.1.4+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2017.1.4+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2017.1.4+bremen1)  
**gluon-Version**: [2017.1.4](#gluon-versionen_2017-1-4)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2017.1.4+bremen1/)


**Hinweis:** Dies ist die erste Freifunk Bremen Version mit Gluon welches auf LEDE, statt auf OpenWrt basiert.  ihre Konfiguration.  
**Update-Hinweis:** Ein Problem beim Aktualisieren von x86-Knoten auf die LEDE-Basis, welches zum Verlust der Konfiguration führt, wurde in [2016.2.6+bremen1](#freifunk-bremen-versionen_2016-2-6-bremen1) behoben. Es ist zwingend nötig erst auf diese Version zu aktualisieren bevor der Sprung zu LEDE gemacht wird.  
Zusätzlich muss bei virtuellen Maschinen eventuell der Speicherplatz manuell erweitert werden.  
**Hinweis:** Geräte mit nur 4MB Speicherplatz werden nun speziell behandelt, um weiterhin einen Betrieb zu gewährleisten. Diese Geräte können keine opkg-Pakete mehr nachinstallieren.    
Für eine Übersicht an Geräten welche dies betrifft, lohnt sich ein Blick auf List der unterstützten Hardware: [ar71xx-tiny](https://gluon.readthedocs.io/en/v2017.1/index.html#ar71xx-tiny)  
**Hinweis:** Durch einen kleinen Fehler, wird der Firmwarename mit einem extra `+` am Ende angezeigt. Dies hat keine Bedeutung und kann ignoriert werden.

- **Update auf [Gluon 2017.1.4](#gluon-versionen_2017-1-4)**
    - Gluon 2017.x Versionen basieren nun auf LEDE  
      dies bringt verschiedene Behebungen für Sicherheitslücken und Programmfehler sowie viele Neuerungen und Updates von genutzer Software  
      *für eine vollständigere Liste der Neuerung seit dem Umstieg Gluons von OpenWRT auf LEDE als Basis, lest bitte die Gluon-Versions-Changelogs ([Gluon 2017.1.4](#gluon-versionen_2017-1-4), [Gluon 2017.1.3](#gluon-versionen_2017-1-3), [Gluon 2017.1.2](#gluon-versionen_2017-1-2), [Gluon 2017.1.1](#gluon-versionen_2017-1-1) und [Gluon 2017.1](#gluon-versionen_2017-1))*
        - neue Geräte werden unterstützt
            - TP-Link
                - TL-WA730RE v1
                - TL-WA7210N v2
                - RE450
                - WBS210 v1.20
                - WBS510 v1.20
            - Ubiquiti
                - AirGateway LR
                - AirGateway PRO
                - Rocket M2/M5 Ti
                - UniFi AP LR
            - GL Innovations
                - GL-AR300M
    - Linux-Kernel-Version von 3.18.x auf 4.4.x angehoben
    - KRACK-Lücke wurde behoben
    - das Kompilier-System wurde extrem vereinfacht und beschleunigt
    - *output/modules* wurde in *output/packages* umbenannt
    - Übersetzungen-Unterstützung für die Statusseite wurde hinzugefügt  
      zusätzlich zu Deutsch sind nun auch Englisch und Russisch verfügbar
    - L2TP über tunneldigger wurde als alternatives VPN-System verfügbar gemacht  
        - Verschlüsselung wird nicht unterstützt
        - Tunnel über IPv6 wird aktuell nicht unterstützt
        - fastd und L2TP können nicht in der gleichen Firmware eingesetzt werden
    - das Update-Manifest wurde erweitert, um automatische Upgrades von alten x86-kvm- und x86-xen_domu-Systemen auf das neue x86-generic-Abbild zu ermöglichen
- Signing-Keys von inaktiven Freifunkern entfernt
    - ProXyhb
    - ec8or


### 2016.2.7+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [20.11.2017](https://downloads.bremen.freifunk.net/firmware/all/2016.2.7+bremen1/sysupgrade/stable.manifest)   ([Blogpost](https://bremen.freifunk.net/blog/2017/11/17/neue-stable-firmware-2016-2-7-bremen1.html))  
**Veröffentlichung auf dem `testing`-Branch**: [31.10.2017](https://downloads.bremen.freifunk.net/firmware/all/2016.2.7+bremen1/sysupgrade/testing.manifest)   ([Blogpost](https://bremen.freifunk.net/blog/2017/10/23/updateproblem-und-neue-testing-2016-2-7-bremen1.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.7+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.7+bremen1)  
**gluon-Version**: [2016.2.7](#gluon-versionen_2016-2-7)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.7+bremen1/)

- **Update auf [Gluon 2016.2.7](#gluon-versionen_2016-2-7)**
    - ein Problem mit dem Umgang von Fehlern beim sysupgrade wurde verbessert  
  wenn sich beim Vorgang einige Prozesse nicht ordnungsgemäß beenden lassen, meist aufgrund von Kernel-Fehlern, startet der Knoten nun neu, anstatt für immer zu hängen
- ULA-Präfix wird nun für uradvd und next_node verwendet


### 2016.2.6+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [26.06.2017](http://downloads.bremen.freifunk.net/firmware/all/2016.2.6+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [12.06.2017](http://downloads.bremen.freifunk.net/firmware/all/2016.2.6+bremen1/sysupgrade/testing.manifest) ([Blogpost](https://bremen.freifunk.net/blog/2017/06/13/neue-testing-2016-2-6-bremen1.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.6+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.6+bremen1)  
**gluon-Version**: [2016.2.6](#gluon-versionen_2016-2-6)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.6+bremen1/)

**Bug-Hinweis:** Ein Problem mit dem Umgang von Fehlern beim sysupgrade (wenn sich beim Vorgang einige Prozesse nicht ordnungsgemäß beenden lassen, meist aufgrund von Kernel-Fehlern) führt dazu, dass Knoten für immer hängt.  
Für ein erfolgreiches Update muss der Knoten eventuell kurz vom Strom getrennt und das Update direkt danach noch ein mal durchgeführt werden.

- **Update auf [Gluon 2016.2.6](#gluon-versionen_2016-2-6)**
    - Unterstützung für TP-Link TL-WR841N/ND v12 wurde hinzugefügt
    - die sysupgrade-Prozedur wurde umgebaut um ein Problem beim Update von x86 Knoten zu beheben
    - eine Sicherheitslücke wurde geschlossen
    - ein Problem mit dem roaming wurde behoben
    - ein paar Probleme beim Kompilieren wurden behoben


### 2016.2.4+bremen2
**Veröffentlichung auf dem `stable`-Branch**: [30.04.2017](http://downloads.bremen.freifunk.net/firmware/all/2016.2.4+bremen2/sysupgrade/stable.manifest)   ([Blogpost](https://bremen.freifunk.net/blog/2017/05/18/aktuelle-stable-2016-2-4-bremen2.html))  
**Veröffentlichung auf dem `testing`-Branch**: [14.04.2017](http://downloads.bremen.freifunk.net/firmware/all/2016.2.4+bremen2/sysupgrade/testing.manifest) ([Blogpost](https://bremen.freifunk.net/blog/2017/04/14/neue-testing-2016-2-4-bremen2.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.4+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.4+bremen2)  
**gluon-Version**: [2016.2.4](#gluon-versionen_2016-2-4)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.4+bremen2/)

- Fehler mit der Konfiguration des Autoupdaters behoben  
  bei neuen oder zurückgesetzten Knoten ist der Autoupdater wieder standardmäßig aktiv
- Paket gluon-ebtables-segment-mld wurde hinzugefügt  
  filtert MLD-Traffic aus, der mit Batman unsinnig ist, da er seine Funktion unter Batman nicht erfüllen kann
- Images für x86-64 hinzugefügt
  für das x86-64-Target werden ab jetzt standardmäßig Images mitgebaut


### 2016.2.4+bremen1
**Veröffentlichung auf dem `stable`-Branch**: 04.07.2017  
(zurückgezogen am 10.04.2017)([Blogpost](https://bremen.freifunk.net/blog/2017/04/13/2016-2-4-bremen1.html))  
**Veröffentlichung auf dem `testing`-Branch**: 24.03.2017 ([Blogpost](https://bremen.freifunk.net/blog/2017/03/24/neue-stable-und-testing.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.4+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.4+bremen1)  
**gluon-Version**: [2016.2.4](#gluon-versionen_2016-2-4)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Durch eine fehlerhafte Konfiguration ist der Autoupdater nicht standardmäßig aktiv bei neuinstallierten oder zurückgesetzten Knoten!

- **Update auf [Gluon 2016.2.4](#gluon-versionen_2016-2-4)**  
- gluon-radv-filterd aktualisiert aus dem Gluon-PR
    - Hatte einen Fehler im Code der für das Parsen der Originators zuständig war
- vpn04 entfernt
  - Hatte massive Probleme mit Abstürzen und stand bei Hetzner
- Paket gluon-alfred entfernt
  - Mit dem Wechsel auf die neue Webseite, den neuen Meshviewer und damit Yanic und respondd wird Alfred endlich nicht mehr gebraucht


### 2016.2.3+bremen3
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: 03.03.2017 ([Blogpost](https://bremen.freifunk.net/blog/2017/03/24/neue-stable-und-testing.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.3+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.3+bremen3)  
**gluon-Version**: [2016.2.3](#gluon-versionen_2016-2-3)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Durch eine fehlerhafte Konfiguration ist der Autoupdater nicht standardmäßig aktiv bei neuinstallierten oder zurückgesetzten Knoten!

- gluon-radv-filterd aktualisiert aus dem Gluon-PR (diesmal richtig)
    - Enthält jetzt ein respondd-Modul, das den ausgewählten Gateway preisgibt
- Mesh-VPN ist jetzt standardmäßig aktiviert ([Beschluss](https://wiki.bremen.freifunk.net/Treffen/2017_02_17#protokoll_firmware))
- Bandbreitenlimits sind jetzt standardmäßig deaktiviert ([Beschluss](https://wiki.bremen.freifunk.net/Treffen/2017_02_17#protokoll_firmware))
- Bandbreitenlimits sind jetzt mit zeitgemäßen Werten versehen (14400/1800) ([Beschluss](https://github.com/FreifunkBremen/gluon-site-ffhb/issues/20))


### 2016.2.3+bremen2
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.3+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.3+bremen2)  
**gluon-Version**: [2016.2.3](#gluon-versionen_2016-2-3)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Durch die unvollständige Aktualisierung von gluon-radv-filterd könnte dieses Paket in einem vollkommen kaputten Zustand sein. Bitte stattdessen 2016.2.3+bremen3 verwenden!

- Altes Übergangspaket gluon-wan-dnsmasq-static entfernt, das eine Bremen-spezifische Konfiguration in die seit Mitte 2015 in Gluon integrierte Konfiguration überführt
- gluon-radv-filterd aktualisiert aus dem Gluon-PR (leider unvollständig, weswegen +bremen3 fällig wurde)


### 2016.2.3+bremen1
**Veröffentlichung auf dem `stable`-Branch**: 03.03.2017 ([Blogpost](https://bremen.freifunk.net/blog/2017/03/24/neue-stable-und-testing.html))  
**Veröffentlichung auf dem `testing`-Branch**: 13.02.2017 ([Blogpost](https://bremen.freifunk.net/blog/2017/02/17/neue-testing-2016-2-3-bremen1.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.3+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.3+bremen1)  
**gluon-Version**: [2016.2.3](#gluon-versionen_2016-2-3)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2016.2.3](#gluon-versionen_2016-2-3)**
    - Unterstützung für 2 neue TP-LINK Geräte
    - Unterstützung von Meraki-Geräten temporär entfernt
    - einige Fehler behoben
        - Autoupdater sollte jetzt nicht mehr hängen
        - respondd wird bei einem crash neugestartet
- Paket respondd-module-airtime hinzugefügt
- Gluon-Paket gluon-ebtables-filter-multicast hinzugefügt  
  filtert allen nicht unbedingt benötigten multicast traffic; wird das Grundrauschen vermutlich massive Verringern und die Performance von WLAN-, Uplink- und Mesh-Verbindungen dadurch deutlich erhöhen
- Bandbreitenlimitierungs-Fehler seit [2016.1+bremen1](#freifunk-bremen-versionen_2016-1-bremen1) behoben  
  die Bandbreitenlimitierung war nicht standardmäßig bei der ersten Einrichtung eingeschaltet und deren Standardwerte fehlten


### 2016.2.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: 19.12.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/12/30/neue-testing-2016-2-2-bremen1.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.2+bremen1)  
**gluon-Version**: [2016.2.2](#gluon-versionen_2016-2-2)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern aktualisiert nach längerer Betriebszeit bis zum nächsten Neustart gar nicht mehr.

- **Update auf [Gluon 2016.2.2](#gluon-versionen_2016-2-2)**
    - Unterstützung für 3 neue TP-LINK Geräte
    - einige Fehler seit [2016.2.1](#gluon-versionen_2016-2-1) und [2016.2](#gluon-versionen_2016-2) behoben  
      inkl. vertauschtem WAN/LAN-Port auf CPE210 bei initialem Flash

#### bekannte Bugs
- wget-Instanz des Autoupdaters blockiert eventuell den Autoupdater bis zum nächsten Neustart, bei einem timeout 


### 2016.2.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: 08.11.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/11/09/neue-testing-firmware.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.1+bremen1)  
**gluon-Version**: [2016.2.1](#gluon-versionen_2016-2-1)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern aktualisiert nach längerer Betriebszeit bis zum nächsten Neustart gar nicht mehr.

- **Update auf [Gluon 2016.2.1](#gluon-versionen_2016-2-1)**
    - WLAN-Treiber Probleme behoben
- Bug: auf CPE210 WAN- und LAN-Port bei kompletten Neuflash verdreht


### 2016.2+bremen2
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2+bremen2)  
**gluon-Version**: [2016.2](#gluon-versionen_2016-2)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern aktualisiert nach längerer Betriebszeit bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis2:** Laut den Gluon-Entwicklern und anderen Communities gibt es seit dieser Version Probleme mit ath9k, wodurch auf vielen unseren Geräten es zu verschwundenen und nicht sichtbaren WLANs und ständigen Neustarts kommen könnte.  
Aus diesem Grund haben wir das Release von Firmware basierend auf [Gluon 2016.2](#gluon-versionen_2016-2) zurückgenommen und verzögert.

- 802.11b deaktiviert
- Paket gluon-radv-filterd aufgenommen (lässt nur das IPv6-Router-Advertisement vom, laut batman-adv, besten Gateway durch)
- Unseren OpenWrt-Proxy in `/etc/opkg/distfeeds.conf` eingetragen (dadurch funktioniert `opkg update` nun auch auf Knoten ohne WAN-Anschluss)


### 2016.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2+bremen1)  
**gluon-Version**: [2016.2](#gluon-versionen_2016-2)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern aktualisiert nach längerer Betriebszeit bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis2:** Laut den Gluon-Entwicklern und anderen Communities gibt es seit dieser Version Probleme mit ath9k, wodurch auf vielen unseren Geräten es zu verschwundenen und nicht sichtbaren WLANs und ständigen Neustarts kommen könnte.  
Aus diesem Grund haben wir das Release von Firmware basierend auf [Gluon 2016.2](#gluon-versionen_2016-2) zurückgenommen und verzögert.

- **Update auf [Gluon 2016.2](#gluon-versionen_2016-2)**
    - ath10k-Geräte wie Archer C5/C7 unterstützen nun Meshing auf 5 Ghz
    - manuell eingestellte WLAN-Channel können nun mit einer Option updatefest gemacht werden
    - Knoten-Namen können nun all UTF-8 Zeichen enthalten
    - SSH-Server auf den Knoten aktueller und performanter
    - Fehler im Autoupdater (multiple Instanzen) behoben
- das Feld "Höhe" wird im Konfigurationsmodus nicht mehr angezeigt (solange nicht schon ein Wert gesetzt wurde)


### 2016.1.6+bremen1.1
**Bug-Hinweis:** In [Gluon 2016.1.6](#gluon-versionen_2016-1-6) gibt es ein Problem mit statisch konfigurierten DNS-Servern. fastd kann dann keine Verbindung zu einem Gateway aufbauen.

**Veröffentlichung auf dem `stable`-Branch**: 23.11.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/11/23/2016-1-6-bremen1-1-jetzt-stable.html))  
**Veröffentlichung auf dem `testing`-Branch**: 11.10.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/10/11/neue-firmware-und-ausblick.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.6+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.6+bremen1)  
**gluon-Version**: [2016.1.6](#gluon-versionen_2016-1-6)  
**Download**: *nicht mehr verfügbar*

*Bei Firmware-Version [2016.1.6+bremen1](#freifunk-bremen-versionen_2016-1-6-bremen1) wurden keine Images für die TP-Link Archer C5/C7 generiert. Diese Version ist ein erneuter Build auf dem gleichen Quellcode, jedoch mit Archer C5/C7 Images.*


### 2016.1.6+bremen1
**Bug-Hinweis:** In [Gluon 2016.1.6](#gluon-versionen_2016-1-6) gibt es ein Problem mit statisch konfigurierten DNS-Servern. fastd kann dann keine Verbindung zu einem Gateway aufbauen.

**Veröffentlichung auf dem `stable`-Branch**: 07.10.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/10/11/neue-firmware-und-ausblick.html))  
**Veröffentlichung auf dem `testing`-Branch**: 20.09.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/10/11/neue-firmware-und-ausblick.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.6+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.6+bremen1)  
**gluon-Version**: [2016.1.6](#gluon-versionen_2016-1-6)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2016.1.6](#gluon-versionen_2016-1-6)**
    - deutlich verbesserter Empfang auf TP-Link CPE210/510 (etwa 20db)
- Option zum Abschalten der fastd-Verschlüsselung für die VPN-Verbindung zu den Freifunk Bremen Gateways für den Konfigurationsmodus hinzugefügt
- die Region für die Firmware wurde auf `EU` gesetzt, so dass das Aufspielen von Freifunk Bremen Firmware auf Archer C7 Geräten mit aktueller Standard-Firmware möglich ist


### 2016.1.5+bremen1
**Veröffentlichung auf dem `stable`-Branch**: 03.07.2016  
**Veröffentlichung auf dem `testing`-Branch**: 26.05.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/05/28/neue-2016er-firmwares.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.5+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.5+bremen1)  
**gluon-Version**: [2016.1.5](#gluon-versionen_2016-1-5)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2016.1.5](#gluon-versionen_2016-1-5)**
    - Unterstützung für 9 weitere Geräte von OpenMesh, Ubiquiti und TP-Link  
      insbesondere der TL-WR841N/ND v11
    - 5-Ghz-Frequenzband auf Archer C5/C7 funktioniert nun  
    **Hinweis:** auf dem 5-Ghz-Frequenzband ist kein Mesh möglich
    - auf allen Ubiquiti AirMAX Geräten kann die Firmware nun direkt installiert werden, ohne das vorher nötige Downgrade auf AirOS 5.5.x machen zu müssen


### 2016.1.4+bremen2
**Veröffentlichung auf dem `stable`-Branch**: 24.05.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/05/28/neue-2016er-firmwares.html))  
**Veröffentlichung auf dem `testing`-Branch**: 06.05.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/05/28/neue-2016er-firmwares.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.4+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.4+bremen1)  
**gluon-Version**: [2016.1.4](#gluon-versionen_2016-1-4)  
**Download**: *nicht mehr verfügbar*

*Bei Firmware-Version [2016.1.4+bremen1](#freifunk-bremen-versionen_2016-1-4-bremen1) wurden keine Images für die TP-Link Archer C5/C7 generiert. Diese Version ist ein erneuter Build auf dem gleichen Quellcode, jedoch mit Archer C5/C7 Images.*

**Hinweis:** Aufgrund eines Fehlers spezifisch in [Gluon 2016.1.4](#gluon-versionen_2016-1-4) funktioniert das 5-Ghz-Modul der Archer-Geräte überhaupt nicht ([Gluon-Issue](https://github.com/freifunk-gluon/gluon/issues/758)).  
Die Images für die Archer-Geräte wurden vom Download-Server entfernt.


### 2016.1.4+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.4+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.4+bremen1)  
**gluon-Version**: [2016.1.4](#gluon-versionen_2016-1-4)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2016.1.4](#gluon-versionen_2016-1-4)**
- Port und MTU für Mesh-VPN geändert. **Dies erfordert ggf. eine Änderung in den Freigaben der FRITZ!Box!** Der neue Port ist UDP 50000, der alte war UDP 10000.


### 2016.1.3+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.3+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.3+bremen1)  
**gluon-Version**: [2016.1.3](#gluon-versionen_2016-1-3)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2016.1.3](#gluon-versionen_2016-1-3)**


### 2016.1.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: 19.03.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/05/28/neue-2016er-firmwares.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.2+bremen1)  
**gluon-Version**: [2016.1.2](#gluon-versionen_2016-1-2)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2016.1.2](#gluon-versionen_2016-1-2)**


### 2016.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: 18.02.2016 ([Blogpost](https://bremen.freifunk.net/blog/2016/05/28/neue-2016er-firmwares.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1+bremen1)  
**gluon-Version**: [2016.1](#gluon-versionen_2016-1)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2016.1](#gluon-versionen_2016-1)**
- vpn05 hinzugefügt
- eigenes opkg-Repository für die Kernel Module für Freifunk Bremen hinzugefügt
- TP-Link WR841N/ND v10 Unterstützung


### 2015.2+bremen3~exp
**Veröffentlichungsdatum**: 25.12.2015 
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.2+bremen3-exp) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.2+bremen3-exp)  
**gluon-Version**: [2015.2](#gluon-versionen_2016-1) (unfertig; noch in der Entwicklung)  
**Download**: *nicht mehr verfügbar*

- **Update auf den aktuellen Entwicklungsstand des unfertigen [Gluon 2015.2](#gluon-versionen_2016-1)**


### 2015.1.2+bremen3
**Veröffentlichung auf dem `stable`-Branch**: 30.12.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/12/30/v2015-1-2-bremen3-wird-stable.html))  
**Veröffentlichung auf dem `testing`-Branch**: 18.12.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/12/20/v2015-1-2-bremen3-und-firmwareschema-umstellung.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen3)  
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)  
**Download**: *nicht mehr verfügbar*

- Firmware-Mirror entfernt  
  autoupdater lief mehrfach, wenn Mirror nicht erreichbar waren ([gluon-issue](https://github.com/freifunk-gluon/gluon/issues/582))
- VPNs 01, 02, 03, 04 und 06 enthalten (davon 04 und 06 neu)
- DNS-Einträge der NTP-Server korrigiert
- Firmware-Schema umgestellt ([Beschluss](/Treffen/2015_12_17#protokoll_firmware))
    - Firmware wird nicht mehr als Testing- oder Stable-Firmware gebaut  
        - es gibt **eine** Firmware
            - steht zuerst nur Knoten mit Autoupdater auf *testing* zur Verfügung
            - bei erfolgreichem Test, wird die Firmware bitgleich, ohne neu zu kompilieren, für die Stable-Knoten freigegeben
        - `~testing`-Suffix entfält
    - Testing versteht sich als Release Candidate  
      nur Funktionen, welche unmittelbar auf Stable-Knoten sollen, werden in die Firmware eingebaut
    - Firmware mit `~exp`-Suffix für Tests von brandneuen und experimentellen Features
        - wird auf dem Downloadserver verfügbar gemacht
        - hat kein Autoupdater
        - wird per Blog angekündigt


### 2015.1.2+bremen3~testing
**Veröffentlichungsdatum**: 15.12.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/12/16/v2015-1-2-bremen3-testing.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen3-testing) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen3-testing)  
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)  
**Download**: *nicht mehr verfügbar*

- IPv6-Präfix gewechselt
- Fehlerbehebungen
- Firmware-Mirror und Signing-Key von mortzu entfernt


### 2015.2+bremen2~exp
**Veröffentlichungsdatum**: 12.12.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.2+bremen2-exp) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.2+bremen2-exp)  
**gluon-Version**: [2015.2](#gluon-versionen_2016-1) (unfertig; noch in der Entwicklung)  
**Download**: *nicht mehr verfügbar*

- **Update auf den aktuellen Entwicklungsstand des unfertigen [Gluon 2015.2](#gluon-versionen_2016-1)**
- fehlerhaftes Abschalten des WLAN-Moduls bei TP-Link TL-WR841 v10 Geräten bei [2015.2+bremen1~exp](#Freifunk-Bremen-Versionen_2015.2+bremen1~exp) behoben


### 2015.2+bremen1~exp
**Veröffentlichungsdatum**: 26.11.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.2+bremen1-exp) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.2+bremen1-exp)  
**gluon-Version**: [2015.2](#gluon-versionen_2016-1) (unfertig; noch in der Entwicklung)  
**Download**: *nicht mehr verfügbar*

- **Update auf den aktuellen Entwicklungsstand des unfertigen [Gluon 2015.2](#gluon-versionen_2016-1)**
- Support für TP-Link TL-WR841 v10


### 2015.1.2+bremen2
###### *urspr. [2015.1.2+bremen2~testing](#freifunk-bremen-versionen_2015-1-2-bremen2-testing)*
**Veröffentlichungsdatum**: 08.11.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/11/08/neue-firmware.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen2)  
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)  
**Download**: *nicht mehr verfügbar*

- signing-keys hinzugefügt von:
  - SimJoSt
  - oliver
  - janeric
  - ec8or
  - ProXyhb

##### Features, welche nach dem Testbetrieb für die stable-Version wieder entfernt wurden
- VPNs 04,05,06 hinzugefügt  
  Test, ob per Ansible aufgesetzte VPNs einwandfrei funktionieren


### 2015.1.2+bremen2~testing
**Veröffentlichungsdatum**: 06.09.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen2-testing) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen2-testing)  
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)  
**Download**: *nicht mehr verfügbar*

- neues Gateway VPN04 hinzugefügt


### 2015.1.2+bremen1~testing
**Veröffentlichungsdatum**: 29.08.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen1-testing) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen1-testing)  
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2015.1.2](#gluon-versionen_2015-1-2)**


### 2015.1.1+bremen1
###### *ursprünglich [2015.1.1+bremen1~testing](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.1+bremen1-testing)*
**Veröffentlichungsdatum**: 07.08.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.1+bremen1)  
**gluon-Version**: [2015.1.1](#gluon-versionen_2015-1-1)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2015.1.1](#gluon-versionen_2015-1-1)**
- Node-Namen-Präfix `ffhb-` nicht mehr standardmäßig vorgegeben


### 2014.4+bremen0 - **erste Stable**
###### *ursprünglich [0.6~testing1](#Freifunk-Bremen-Versionen_0.6~testing1)*

**Veröffentlichungsdatum**: 28.06.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/06/28/erste-stabile-firmware.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2014.4+bremen0) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2014.4+bremen0)  
**gluon-Version**: [2014.4](#gluon-versionen_2014-4)  
**Download**: *nicht mehr verfügbar*

- die effizientere und schnellere fastd cipher salsa2012+umac hinzugefügt
- signing-key von corny hinzugefügt


### 0.6~testing1
**Veröffentlichungsdatum**: 03.05.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/05/03/neue-firmware.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v0.6-testing1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v0.6-testing1)  
**gluon-Version**: [2014.4](#gluon-versionen_2014-4)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2014.4](#gluon-versionen_2014-4)**
- Link zum Eingeben des fastd key auf dem Server entfernt
- Kanalanalyse-Komponenten entfernt
- neues Gateway VPN03 hinzugefügt
- mesh ssid von mesh.ffhb zu mesh.ffhb.de geändert
- IPv6-Präfix zu 2001:bf7:540 geändert; weg von local zu public
- autoupdater URLs behoben


### 0.5~testing5
**Veröffentlichungsdatum**: 06.09.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/09/06/Neue-Testing-Channel-Survey.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v0.5-testing5) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v0.5-testing5)  
**gluon-Version**: [2014.3](#gluon-versionen_2014-3)  
**Download**: *nicht mehr verfügbar*

- Kanalanalyse-Komponenten integriert
- WLAN-Feintuning
  - 2,4Ghz-Kanalbreite von 40Mhz auf 20Mhz reduziert
  - Multicast-Rate auf 6 Mbit/s herabgesetzt (die Grenze ab wann 2 Knoten Meshen/sich verbinden)
- DHCP-Server und IPv6-Router hinter einem Node werden nicht mehr durchgelassen ("Funktion Internet" im Freifunk-Netz sonst leicht störbar)


### 0.5~testing4
**Veröffentlichungsdatum**: 08.08.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/08/08/Neue-Testing.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v0.5-testing4) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v0.5-testing4)  
**gluon-Version**: [2014.3](#gluon-versionen_2014-3)  
**Download**: *nicht mehr verfügbar*

- **Update auf [Gluon 2014.3](#gluon-versionen_2014-3)**
- Ende der WLAN-Probleme (mit Überwachung evtl. Probleme)
- Autoupdater standardmäßig an


### 0.5~testing3
**Veröffentlichungsdatum**: 23.06.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/06/23/Facebook-und-Testing-3.html))  
**gluon-Version**: [2014.2](#gluon-versionen_2014-2)  
**Download**: *nicht mehr verfügbar*

- Mesh-ESSID von batman.bremen.freifunk.net zu mesh.ffhb geändert um Verwirrung zu vermeiden
- neue WLAN-Treiber und -Software, dadurch hoffentlich keine Signal-Abbruch-Probleme mehr
- vom Knoten übertragene Statistik wird nun komprimiert
- Probleme mit TP-Link TL-WR841N/ND v9 behoben
- Firewall block alles Eingehende auf dem WAN-Port außer SSH


### 0.5~testing2
**gluon-Version**: [2014.2](#gluon-versionen_2014-2)  
**Download**: *nicht mehr verfügbar*

#### bekannte Probleme
- Signal-Abbruch-Problem auf 2,4 Ghz
- TP-Link TL-WR841N/ND v9 macht Probleme


### 0.5~testing1 - **erste Testing**
**Veröffentlichungsdatum**: 24.03.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/03/24/testing-firmware.html))  
**gluon-Version**: [2014.2](#gluon-versionen_2014-2)  
**Download**: *nicht mehr verfügbar*

- alle Nightly-Geräte haben auf den Testing-Branch gewechselt
- Doppel-Key-Problem behoben




## Gluon Versionen

Der Quellcode von Gluon liegt bei [Github](https://github.com/freifunk-gluon/gluon).  
Die Dokumentation ist auf [gluon.readthedocs.io](https://gluon.readthedocs.io/) einsehbar.

Es folgt eine Liste aller Gluon Versionen mit einer übersetzten und vereinfachten Liste der Neuerungen und Fehlerkorrekturen.

### 2022.1.1
**Veröffentlichungsdatum**: 05.09.2022  
**offizielle Versionshinweise**: [2022.1.1](https://gluon.readthedocs.io/en/v2022.1.1/releases/v2022.1.1.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2022.1.1/user/supported_devices.html)  
**Github-Repository**: [Commits](https://github.com/freifunk-gluon/gluon/commits/v2022.1.1)

#### Ängerungen
- Viele neuen Geräte
- Entfernen viele Geräte, die nicht genug Speicher haben (wie zum Beispiel: TP-Link WR421)
- viele, viele Änderungen im Vergleich zur 2021.1

### 2021.1.2
**Veröffentlichungsdatum**: 05.05.2022  
**offizielle Versionshinweise**: [2021.1.2](https://gluon.readthedocs.io/en/v2021.1.2/releases/v2021.1.2.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2021.1.2/user/supported_devices.html)  
**Github-Repository**: [Commits](https://github.com/freifunk-gluon/gluon/commits/v2021.1.2)

#### Fehlerbehebungen
- viele, viele Änderungen im Vergleich zur 2019.1.3


### 2019.1.3+ (git250b623f)
**Veröffentlichungsdatum**: 05.05.2022  
**offizielle Versionshinweise**: [2019.1.3](https://gluon.readthedocs.io/en/v2019.1.3/releases/v2019.1.3.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2019.1.3/user/supported_devices.html)  
**Github-Repository**: [Commits](https://github.com/freifunk-gluon/gluon/commit/250b623fb4a1bc2d6e0b91809385b8aaa1a4b5d5)

Für dieses Gluon-Release gibt es keine eigene Versionsnummer (weil der 2019.x-Branch nicht mehr offiziell gepflegt wird).
Deshalb wird diese Version hier mit dem Git-Commit ([250b623f](https://github.com/freifunk-gluon/gluon/commit/250b623fb4a1bc2d6e0b91809385b8aaa1a4b5d5)) benannt.

#### Fehlerbehebungen
- Behebung für kritische Sicherheitslücke [CVE-2022-24884](https://github.com/freifunk-gluon/gluon/security/advisories/GHSA-xqhj-fmc7-f8mv)
- diverse andere Fehlerbehebungen


### 2019.1.3
**Veröffentlichungsdatum**: 05.11.2020  
**offizielle Versionshinweise**: [2019.1.3](https://gluon.readthedocs.io/en/v2019.1.3/releases/v2019.1.3.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2019.1.3/user/supported_devices.html)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2019.1.3) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2019.1.3)

#### Fehlerbehebungen
- diverse Fehlerbehebungen


### 2019.1.2
**Veröffentlichungsdatum**: 04.02.2020  
**offizielle Versionshinweise**: [2019.1.2](https://gluon.readthedocs.io/en/v2019.1.2/releases/v2019.1.2.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2019.1.2/user/supported_devices.html)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2019.1.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2019.1.2)

#### Fehlerbehebungen
- zwei Sicherheitslücken in OpenWRT wurden geschlossen:
  - CVE-2020-7248 in libubox
  - CVE-2020-7982 in opkg


### 2019.1.1
**Veröffentlichungsdatum**: 06.01.2020  
**offizielle Versionshinweise**: [2019.1.1](https://gluon.readthedocs.io/en/v2019.1.1/releases/v2019.1.1.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2019.1.1/user/supported_devices.html)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2019.1.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2019.1.1)

#### Fehlerbehebungen
- diverse Fehlerbehebungen


### 2019.1
**Veröffentlichungsdatum**: 14.09.2019  
**offizielle Versionshinweise**: [2019.1](https://gluon.readthedocs.io/en/v2019.1/releases/v2019.1.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2019.1/user/supported_devices.html)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2019.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2019.1)

#### Fehlerbehebungen
- das `gluon-authorized-keys`-Modul funktioniert jetzt korrekt, auch wenn in der `site.mk` das `gluon-setup-mode`-Modul nicht eingetragen wurde

#### Neuerungen
- Neue Funktionen für Infrastruktur-Migrationen (z.B. für den Wechsel der B.A.T.M.A.N-Version), in Form von Scheduled Domain Switching und Koexistenz von batman-adv-Treibern. Solche Migrationen werden dringender, weil mit 2019.2 einige alte Funktionen nicht mehr unterstützt sein werden.
- respondd-Anfragen an `[ff02::2:1001]:1001` werden nicht mehr unterstützt; nur `[ff05::2:1001]:1001` wird noch unterstützt.
- für 5GHz-Geräte kann jetzt der "Outdoor Mode" eingeschaltet werden, damit DFS (Dynamic Frequency Selection) verwendet wird.
- Geolocation-Unterstützung im Hood Selector hinzugefügt
- der `firstboot`-Befehl wird jetzt auch bei x86-Geräten unterstützt

#### Neue Geräte-Unterstützung
- 8devices
  - Jalapeno
- Aerohive
  - HiveAP 330
- ASUS
  - RT-AC57U
- D-Link
  - DAP-1330 A1
- TP-Link
  - TL-WR840N v2


### 2018.2.2
**Veröffentlichungsdatum**: 24.06.2019  
**offizielle Versionshinweise**: [2018.2.2](https://gluon.readthedocs.io/en/v2018.2.2/releases/v2018.2.2.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.2.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.2.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.2.2)

#### Fehlerbehebungen
- Sicherheitslücken im Linux-Kernel ("SACK-Lücke" etc.) wurden geschlossen (CVE-2019-11477, CVE-2019-11478 und CVE-2019-11479). Durch diese Lücken konnte der Knoten aus der Ferne zum Absturz gebracht werden.
- der Netgear R6120 bleibt nicht mehr im Config-Modus stecken ([#1722](https://github.com/freifunk-gluon/gluon/pull/1722))
- respondd zählt die Anzahl der Nicht-WLAN-Clients jetzt besser ([#1676](https://github.com/freifunk-gluon/gluon/pull/1676))
- der Batman-Management-Traffic wurde reduziert. Ein Fehler ab Gluon 2017.1 hatte zu unnötigem Traffic geführt ([#1446](https://github.com/freifunk-gluon/gluon/pull/1446)). Dies betrifft aber nicht die Batman-Version, die in Bremen verwendet wird.
- Ein Fehler wurde behoben, durch den Dienste auf dem Knoten selbst (z.B. DNS-Server oder Statusseite) nicht erreichbar waren, wenn im gleichen Layer-2-Segment fehlerhafte Knoten  liefen ([#1659](https://github.com/freifunk-gluon/gluon/pull/1659)).
- Probleme beim Tunneldigger-VPN (beim Traffic-Shaping) und beim Umstieg von fastd auf Tunneldigger wurden behoben ([#1736](https://github.com/freifunk-gluon/gluon/pull/1736)).

#### Nicht mehr unterstützte Hardware
- Onion-Omega-Geräte werden nicht mehr unterstützt


### 2018.2.1
**Veröffentlichungsdatum**: 15.03.2019  
**offizielle Versionshinweise**: [2018.2.1](https://gluon.readthedocs.io/en/v2018.2.1/releases/v2018.2.1.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.2.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.2.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.2.1)

#### Fehlerbehebungen
- auf der Statusseite und auf der Karte werden jetzt keine doppelten IPv6-Adressen mehr angezeigt ([#1615](https://github.com/freifunk-gluon/gluon/pull/1615))
- Images für einige Geräte sind umbenannt worden (betrifft GL.iNet GL-AR150, GL.iNet GL-AR300M, GL.iNet GL-AR750, Raspberry Pi Model B+ Rev 1.2)
- bei Unifi AC Lite/Mesh/Pro/Mesh Pro wird die primäre MAC-Adresse jetzt korrekt bestimmt ([#1629](https://github.com/freifunk-gluon/gluon/pull/1629))
- Probleme mit der Bandbreiten-Auswahl bei ath10k und ath10k-ct wurden behoben ([#1644](https://github.com/freifunk-gluon/gluon/pull/1644), [#1657](https://github.com/freifunk-gluon/gluon/pull/1657))
- kleinere Fehlerbehebungen bzgl. Übersetzungen und Statusseite

#### Neuerungen
- "Scheduled domain switch"-Funktion, um die Migration auf neue Freifunk-Techniken (z.B. 11s) zu erleichtern ([#1555](https://github.com/freifunk-gluon/gluon/pull/1555))
- Änderungen an der Behandlung von Dualband-Chips. Dies sollte sich wohl nicht auf bisher unterstützte Geräte auswirken, ist aber für neu unterstützte Geräte wie Fritz!WLAN Repeater 300E nötig. ([#1606](https://github.com/freifunk-gluon/gluon/pull/1606))

#### Neue Geräte-Unterstützung
- AVM
  - Fritz!WLAN Repeater 300E
- Nexx
  - WT3020AD/F/H (nur 11s-Mesh)
- Gl.iNet
  - MT300N (v2) (nur 11s-Mesh)
- Netgear
  - R6120 (nur 11s-Mesh)
- TP-Link
  - Archer C50 (v3, v4) (nur 11s-Mesh)
  - TL-WR841N (v13) (nur 11s-Mesh)


### 2018.2
**Veröffentlichungsdatum**: 29.12.2018  
**offizielle Versionshinweise**: [2018.2](https://gluon.readthedocs.io/en/v2018.2/releases/v2018.2.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.2)

#### Neuerungen
- Gluon basiert ab jetzt wieder auf OpenWRT statt auf LEDE (nachdem LEDE und OpenWRT wieder zusammengeführt wurden)
- im Config-Mode kann eine Karte eingeblendet werden, damit der Benutzer die Knoten-Position leichter eintragen kann
- es gibt jetzt experimentelle Unterstützung für das Babel-Protokoll
- die Mengenbegrenzung für ARP-Pakete (aus dem "gluon-ebtables-limit-arp"-Paket) ist jetzt standardmäßig aktiv

#### Neue Geräte-Unterstützung
- AVM
  - Fritz!WLAN Repeater 450E
  - FRITZ!Box 4040 (nur 11s-Mesh)
- D-Link
  - DIR-860L B1 (nur 11s-Mesh)
- GL.iNet
  - GL-B1300 (nur 11s-Mesh)
- NETGEAR
  - EX6100v2 (nur 11s-Mesh)
  - EX6150v2 (nur 11s-Mesh)
- OCEDO
  - Koala
- OpenMesh
  - A42 (nur 11s-Mesh)
  - A62 (nur 11s-Mesh)
- TP-Link
  - Archer C7 v5
  - TL-WR810N v1
- Ubiquiti
  - UniFi AC Mesh Pro
- ZBT
  - WG3526-16M (nur 11s-Mesh)
  - WG3526-32M (nur 11s-Mesh)
- ZyXEL
  - NBG6616
  - NBG6617 (nur 11s-Mesh)
  - WRE6606 (nur 11s-Mesh)


### 2018.1.4
**Veröffentlichungsdatum**: 20.12.2018  
**offizielle Versionshinweise**: [2018.1.4](https://gluon.readthedocs.io/en/v2018.1.4/releases/v2018.1.4.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.1.4/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.1.4) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.1.4)

#### Fehlerbehebungen
- der Fehler beim Versionsvergleich von Firmware-Updates wurde behoben ([#208](https://github.com/freifunk-gluon/packages/issues/208)). In diesem Zuge wurden auch gleich die Regeln für den Versionsvergleich angepasst, dass sie jetzt den Regeln von opkg/dpkg entsprechen.


### 2018.1.3
**Veröffentlichungsdatum**: 26.11.2018  
**offizielle Versionshinweise**: [2018.1.3](https://gluon.readthedocs.io/en/v2018.1.3/releases/v2018.1.3.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.1.3/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.1.3) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.1.3)

#### Fehlerbehebungen
- der Fehler beim Laden von Kernel-Modulen (der u.a. den batman-adv-Treiber betraf) wurde behoben ([#1580](https://github.com/freifunk-gluon/gluon/issues/1580))


### 2018.1.2
**Veröffentlichungsdatum**: 20.11.2018  
**offizielle Versionshinweise**: [2018.1.2](https://gluon.readthedocs.io/en/v2018.1.2/releases/v2018.1.2.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.1.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.1.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.1.2)

### Neue Fehler
- diese Version hat einen Fehler, wodurch beim Laden von Kernel-Modulen die Abhängigkeiten nicht korrekt geladen werden ([#1580](https://github.com/freifunk-gluon/gluon/issues/1580)). Dadurch konnte unter bestimmten Umständen der batman-adv-Treiber nicht geladen werden, und das Gerät war nicht im Mesh-Netztwerk erreichbar.

#### Fehlerbehebungen
- respondd schickt jetzt die vollständige Liste der IPv6-Adressen eines Knotens ([#1523](https://github.com/freifunk-gluon/gluon/issues/1523))
- die Knöpfe der FRITZ!Box 4020 haben jetzt das korrekte Verhalten ([#1544](https://github.com/freifunk-gluon/gluon/issues/1544))
- es gab einige Bugfixes für batman-adv 2018.1

#### neue Geräte-Unterstützung
- die Unterstützung für den TP-Link C2600 wurde als "eingeschränkt" markiert, weil die WLAN-Verbindung häufig abbricht ([#1505](https://github.com/freifunk-gluon/gluon/issues/1505)). Das Gerät wird nur unterstützt, wenn Gluon mit dem BROKEN-Flag kompiliert wird.


### 2018.1.1
**Veröffentlichungsdatum**: 28.08.2018  
**offizielle Versionshinweise**: [2018.1.1](https://gluon.readthedocs.io/en/v2018.1.1/releases/v2018.1.1.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.1.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.1.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.1.1)

#### Fehlerbehebungen
- Autoupdater-Fehler ([#1496](https://github.com/freifunk-gluon/gluon/issues/1496)) aus der 2018.1 behoben
- ARP-Problem ([#1488](https://github.com/freifunk-gluon/gluon/issues/1488)) aus der 2018.1 behoben
- Kompilier-Probleme auf neueren Betriebssystemen (mit glibc 2.28) behoben


### 2018.1
**Veröffentlichungsdatum**: 08.07.2018  
**offizielle Versionshinweise**: [2018.1](https://gluon.readthedocs.io/en/v2018.1/releases/v2018.1.html)  
**Unterstützte Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2018.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2018.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2018.1)

#### Neue Fehler
- diese Version hat einen Fehler im Autoupdate-System, wodurch es zum Verlust der Knoten-Konfiguration kommen kann, wenn beim Update ein Download-Mirror verwendet wird ([#1496](https://github.com/freifunk-gluon/gluon/issues/1496)).
- diese Version hat einen Fehler beim Versenden von ARP-Paketen, wodurch der Knoten von seinen Nutzern evtl. nicht mehr per IPv4 erreichbar ist ([#1488](https://github.com/freifunk-gluon/gluon/issues/1488)).
- diese Version hat einen Fehler im Autoupdate-Systen, wodurch beim Vergleich von Firmware-Versionen in manchen Fällen eine neuere Version nicht als solche erkannt wurde ([#208](https://github.com/freifunk-gluon/packages/issues/208))


#### Neuerungen
Zu viele neue Features, um sie hier detailliert zu beschreiben: Feature Flags, Multidomain-Support, VXLAN für Kabel-Mesh-Verbindungen, IGMP/MLD-Segmentierung, gluon-ebtables-limit-arp, verbesserte Statusseite...

#### Neue Geräte-Unterstützung
- A5
  - V11 (nur 11s-Mesh)
- ALFA NETWORK
  - AP121F
- AVM
  - FRITZ!Box 4020
- D-Link
  - DIR615 (D1, D2, D3, D4, H1) (nur 11s-Mesh)
- GL Innovations
  - GL-MT300A (nur 11s-Mesh)
  - GL-MT300N (nur 11s-Mesh)
  - GL-MT750 (nur 11s-Mesh)
- LeMaker
  - Banana Pi (M1)
- OpenMesh
  - A40
  - A60
  - OM2P v4
  - OM2P-HS v4
- TP-Link
  - Archer C2600 (nur 11s-Mesh)
  - Archer C59 v1 (nur 11s-Mesh)
  - CPE210 v2
  - TL-WA901ND v5
- VoCore
  - VoCore 2 (nur 11s-Mesh)
  - VoCore (8MB, 16MB) (nur 11s-Mesh)
- ZyXEL
  - NBG6716

#### Umstellungen
- auf einigen Geräten (TP-Link CPE/WBS 210/510) wird jetzt für den Flash-Speicher ein neues Layout verwendet. Deshalb sollte vor dem Upgrade auf die 2018.1 zuerst die 2017.1.8 installiert werden.


### 2017.1.8
**Veröffentlichungsdatum**: 30.04.2018  
**offizielle Versionshinweise**: [2017.1.8](https://gluon.readthedocs.io/en/v2017.1.8/releases/v2017.1.8.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.8/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.8) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.8)

#### Fehlerbehebungen
- verschiedene Batman-Probleme behoben
    - beim Start des Batman-Interfaces kam es zu Hängern
    - ein Fehler führt durch viel Verwaltungsdatenverkehr zu hoher Last

#### Neuerungen
- Linux Kernel auf v4.4.129 aktualisiert
- die Beschreibung des Kontaktinformations-Feldes im Konfigurationsmodus wurde um einen DSGVO-Passus erweitert
- das Kontaktinformations-Feld kann nicht mehr als Pflichtfeld in der Firmware festgelegt werden

#### neue Geräte-Unterstützung
- GL.iNet
    - GL-AR750
- TP-Link
    - Archer C7 v4
    - TL-WR940N v6
- Ubiquiti
    - UniFi AC Mesh


### 2017.1.7
**Veröffentlichungsdatum**: 30.04.2018  
**offizielle Versionshinweise**: [2017.1.7](https://gluon.readthedocs.io/en/v2017.1.7/releases/v2017.1.7.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.7/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.7) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.7)

#### Fehlerbehebung
- Ein Problem mit dem Booten von Ubiquiti-Geräten wurde behoben.


### 2017.1.6
**Veröffentlichungsdatum**: 16.04.2018  
**offizielle Versionshinweise**: [2017.1.6](https://gluon.readthedocs.io/en/v2017.1.6/releases/v2017.1.6.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.6/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.6) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.6)

#### Fehlerbehebungen
- Das Abstürzen aller Knoten bei Neustart eines Gateways wurde behoben.
- Der DNS-Cache auf den Knoten wurde deaktiviert, weil er Probleme mit DNSSEC verursacht hat.


### 2017.1.5
**Veröffentlichungsdatum**: 31.01.2018  
**offizielle Versionshinweise**: [2017.1.5](https://gluon.readthedocs.io/en/v2017.1.5/releases/v2017.1.5.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.5/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.5) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.5)

### Geräte-Unterstützung
- TP-Link TL-WR1043N v5
- Ubiquiti EdgeRouter-X
- Ubiquiti EdgeRouter-X SFP

### Fehlerbehebungen
- ein Kompilierfehler bei leerem Modul-Ordner wurde behoben
- ein Fehler mit Ethernet Verbindungsbeeinträchtigungen bei hohem Durchsatz auf einigen Geräten wurde behoben
- Tunneldigger wurde aktualisiert um Verbindungen zu Servern mit neueren Kernel-Versionen zu unterstützen
- `batman-adv Bridge Loop Avoidance` mit `gluon-ebtables-filter-multicast` wieder funktionstüchtig gemacht


### 2017.1.4
**Veröffentlichungsdatum**: 15.11.2017  
**offizielle Versionshinweise**: [2017.1.4](https://gluon.readthedocs.io/en/v2017.1.4/releases/v2017.1.4.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.4/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.4) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.4)

#### Fehlerbehebungen
- LEDE wurde auf den aktuellsten, stabilen Stand gebracht  
  inklusive verschiedener Behebungen für Sicherheitslücken und Programmfehler
    - KRACK-Lücke wurde behoben
    - OPKG funktioniert wieder
- PoE-Passthrough lässt sich wieder über die site.conf und die Erweiterten Einstellungen einstellen
- ein Problem DNS-Auflösung für Mesh-VPN (fastd/tunneldigger) für ARM-Geräte wurde behoben
- ein Kompilier-Problem wurde behoben

#### Neuerungen
- GL Innovations GL-AR300M wird nun unterstützt


### 2017.1.3
**Veröffentlichungsdatum**: 11.10.2017  
**offizielle Versionshinweise**: [2017.1.3](https://gluon.readthedocs.io/en/v2017.1.3/releases/v2017.1.3.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.3/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.3) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.3)

#### Fehlerbehebungen
- dnsmasq wurde auf v2.78 upgegradet, wodurch die folgenden Schwachstellen behoben wurden CVE-2017-13704, CVE-2017-14491, CVE-2017-14492, CVE-2017-14493, CVE-2017-14494, 2017-CVE-14495 und 2017-CVE-14496  
davon betrifft nur eine Schwachstelle Gluon im Normalbetrieb
- der Linux Kernel wurde auf v4.4.89 upgegradet, wodurch mehrere Sicherheitslücken geschlossen wurden
- das Filtern von Multicast-Paketen zwischen den Schnittenstellen von Mesh und lokalem Knoten wurde repariert
- beim Kompilieren werden Autoupdater-URLs welche nicht mit `http://` beginnen abgelehnt
- MAC-Adressen von frisch installierten TP-Link TL-WR1043ND v4 wurden repariert


### 2017.1.2
**Veröffentlichungsdatum**: 14.08.2017  
**offizielle Versionshinweise**: [2017.1.2](https://gluon.readthedocs.io/en/v2017.1.2/releases/v2017.1.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.2)

#### Neuerungen
- die Einstellung von `gw_mode` wird nun bei Updates nicht mehr überschrieben
- eine neue Option ermöglicht die Konfiguration des batman-adv-Routing-Algorithmusses (BATMAN IV oder BATMAN V)

#### Fehlerbehebungen
- der Abbild-Generierungs-Code für einige Geräte wurde repariert, was mehrere Probleme löst
    - Allnet-Abbilder funktionieren wieder
    - OpenMesh-Geräte behalten nun bei Updates wieder ihre Konfiguration (das Problem entstand mit [Gluon 2017.1](#gluon-versionen_2017-1))
- der Umgang von Fehlern beim sysupgrade wurde verbessert  
  wenn sich beim Vorgang einige Prozesse nicht ordnungsgemäß beenden lassen, meist aufgrund von Kernel-Fehlern, startet der Knoten nun neu, anstatt für immer zu hängen
- im Konfigmodus funktioniert nun auch mit Tunneldigger und nicht nur fastd die Anzeige, ob VPN an- oder abgeschaltet ist
- der an-/aus-Zustand von VPN wird bei einer Migration zwischen fastd und Tunneldigger korrekt übertragen


### 2017.1.1 
**Bug-Hinweis:** OpenMesh-Geräte verlieren bei Updates ihre Konfiguration.

**Veröffentlichungsdatum**: 03.07.2017  
**offizielle Versionshinweise**: [2017.1.1](https://gluon.readthedocs.io/en/v2017.1.1/releases/v2017.1.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1.1)

#### Fehlerbehebungen
- das Update-Manifest wurde erweitert, um automatische Upgrades von alten x86-kvm- und x86-xen_domu-Systemen auf das neue x86-generic-Abbild zu ermöglichen
- ein Bug in [Gluon 2017.1](#gluon-versionen_2017-1) verhinderte das Schreiben auf den Flash-Speicher auf Ubiquiti PicoStations mit bestimmten Bootloader-Versionen  
  betroffene Geräte können nur über TFTP-Wiederherstellung wieder zum Laufen gebracht werden
- batman-adv Multicast-Optimierungen wurden deaktiviert um ein Problem, bei dem viel Verwaltungsdatenverkehr auftritt zu verhindern


### 2017.1
**Hinweis:** Dies ist die erste Gluon-Version welche auf LEDE, statt auf OpenWrt basiert.  
**Bug-Hinweis:** Ein Bug verhindert das Schreiben auf den Flash-Speicher auf Ubiquiti PicoStations mit bestimmten Bootloader-Versionen.  
Betroffene Geräte können nur über TFTP-Wiederherstellung wieder zum Laufen gebracht werden.  
**Bug-Hinweis 2:** OpenMesh-Geräte verlieren bei Updates ihre Konfiguration.

**Veröffentlichungsdatum**: 10.06.2017  
**offizielle Versionshinweise**: [2017.1](https://gluon.readthedocs.io/en/v2017.1/releases/v2017.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2017.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2017.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2017.1)

#### Geräte-Unterstützung
- TP-Link
    - TL-WA730RE v1
    - TL-WA7210N v2
    - RE450
    - WBS210 v1.20
    - WBS510 v1.20
- Ubiquiti
    - AirGateway LR
    - AirGateway PRO
    - Rocket M2/M5 Ti
    - UniFi AP LR

**Hinweis:** Geräte mit nur 4MB Speicherplatz werden nun speziell behandelt, um weiterhin einen Betrieb zu gewährleisten. Diese Geräte können keine opkg-Pakete mehr nachinstallieren.  
Für eine Übersicht an Geräten welche dies betrifft, lohnt sich ein Blick auf List der unterstützten Hardware: [ar71xx-tiny](https://gluon.readthedocs.io/en/v2017.1/index.html#ar71xx-tiny)

#### Änderungen
- Linux-Kernel-Version von 3.18.x auf 4.4.x angehoben
- das Kompilier-System wurde extrem vereinfacht und beschleunigt
- *output/modules* wurde in *output/packages* umbenannt
- der gleiche Wert der für *GLUON_RELEASE* übergeben wird muss auch bei `make manifest` angegeben werden
- Übersetzungen-Unterstützung für die Statusseite wurde hinzugefügt  
  zusätzlich zu Deutsch sind nun auch Englisch und Russisch verfügbar
- DNS-Cache auf Knoten für Clients ist nun möglich
- L2TP über tunneldigger wurde als alternatives VPN-System verfügbar gemacht  
    - Verschlüsselung wird nicht unterstützt
    - Tunnel über IPv6 wird aktuell nicht unterstützt
    - fastd und L2TP können nicht in der gleichen Firmware eingesetzt werden
- das neue Paket *gluon-ebtables-source-filter* wurde hinzugefügt  
  dieses kann zum Filtern von Datenverkehr unerwünschter Herkunft verwendet werden
- die *LuCI* Basis-Bibliotheken wurden durch eine entschlackte Version namens *gluon-web* ersetzt  
  Pakete die darauf aufbauten müssen angepasst werden

#### Fehlerbehebungen
- ein paar Probleme mit Netzwerk- und batman-adv-Konfigurationen, welche zu Abstürzen oder unvollständigen Einrichtungen führen konnte, wurden behoben
- ein paar Verbesserungen erhöhen die Stabilität des ath9k-WLAN-Treibers

#### Umstellungen
- *gluon-legacy*-Pakete existieren nicht mehr
- _gluon-luci-*_-Pakete wurden in _gluon-web-*_ umbenannt
- *gluon-luci-portconfig* wurde in *gluon-web-network* umbenannt
- das *gluon-next-node*-Paket wurde in den Gluon-Kern integriert und muss nicht mehr eingebunden werden
- die Konfiguration von *fastd* wurde leicht verändert um einige Optionen mit einem eventuell konfigurierten *tunneldigger* zu teilen
- die *opkg.openwrt*-Option wurde in *opkg.lede* umbenannt


### 2016.2.7

**Veröffentlichungsdatum**: 14.08.2017  
**offizielle Versionshinweise**: [2016.2.7](https://gluon.readthedocs.io/en/v2016.2.7/releases/v2016.2.7.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.7/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.7) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.7)

#### Fehlerbehebungen
- der Umgang von Fehlern beim sysupgrade wurde verbessert  
  wenn sich beim Vorgang einige Prozesse nicht ordnungsgemäß beenden lassen, meist aufgrund von Kernel-Fehlern, startet der Knoten nun neu, anstatt für immer zu hängen


### 2016.2.6
**Bug-Hinweis:** Ein Problem mit dem Umgang von Fehlern beim sysupgrade (wenn sich beim Vorgang einige Prozesse nicht ordnungsgemäß beenden lassen, meist aufgrund von Kernel-Fehlern) führt dazu, dass Knoten für immer hängt.  
Für ein erfolgreiches Update muss der Knoten eventuell kurz vom Strom getrennt und das Update direkt danach noch ein mal durchgeführt werden.

**Veröffentlichungsdatum**: 10.06.2017  
**offizielle Versionshinweise**: [2016.2.6](https://gluon.readthedocs.io/en/v2016.2.6/releases/v2016.2.6.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.6/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.6) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.6)

#### Geräte-Unterstützung
- TP-Link TL-WR841N/ND v12

#### Fehlerbehebungen
- die sysupgrade Prozedur wurde umgebaut um ein Problem beim Update von x86 Knoten zu beheben  
    - dieses trat auf, wenn die kernel Partition beim Upgrade in Größe zunahm  
    - dies tritt zum Beispiel bei einem Update auf LEDE auf  
    - durch diese Änderung wird die SSH-Verbindung zu einem Knoten bereits am Anfang eines Upgrade beendet und es ist keine Einsicht in den Vorgang mehr möglich
- eine Sicherheitslücke wurde geschlossen ([Gluon-Ticket](https://github.com/freifunk-gluon/gluon/issues/1097))  
  in Standard-Konfigurationen von Gluon, sollte diese Schwachstelle nicht zum tragen kommen, da die betroffene Komponente deaktiviert ist, was auch auf die Bremer Firmware zutrifft
- ein Problem mit dem roaming wurde behoben
- ein Problem beim Kompilieren mit OpenSSL 1.1 wurde behoben
- ein Problem beim Kompilieren mit langen Pfaden wurde behoben


### 2016.2.5

**Veröffentlichungsdatum**: 09.04.2017  
**offizielle Versionshinweise**: [2016.2.5](https://gluon.readthedocs.io/en/v2016.2.5/releases/v2016.2.5.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.5/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.5) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.5)

#### Fehlerbehebungen
- ein B.A.T.M.A.N. compat 15 Fehler, welcher zum Absturz führte, wurde behoben  
*Dieser Fehler betrifft die Bremer Infrastruktur nicht, da zu diesem Zeitpunkt B.A.T.M.A.N. compat 14 eingesetzt wird.*


### 2016.2.4

**Veröffentlichungsdatum**: 13.03.2017  
**offizielle Versionshinweise**: [2016.2.4](https://gluon.readthedocs.io/en/v2016.2.4/releases/v2016.2.4.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.4/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.4) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.4)

#### Fehlerbehebungen
- Hohe Load wegen des neuen respondd-Initscripts ist behoben
- Der abgeschaltete Mirror ftp.all.kernel.org wurde ersetzt
- sysupgrade funktioniert nun auf x86-Geräten besser

### Sonstige Änderungen
- Das Autoupdater-Manifest enthält nun, als Vorbereitung auf die kommende neue Version des Autoupdaters, auch SHA256-Hashes der Images statt wie bisher nur SHA512


### 2016.2.3

**Veröffentlichungsdatum**: 13.02.2017  
**offizielle Versionshinweise**: [2016.2.3](https://gluon.readthedocs.io/en/v2016.2.3/releases/v2016.2.3.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.3/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.3) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.3)

#### Geräte-Unterstützung
- hinzugefügt:
    - TP-Link TL-WR940N v4
    - TP-Link TL-WR1043ND v4
- entfernt:
    - Meraki Geräte (MR12/16/62/66)  
    *(werden wieder hinzugefügt, wenn das Problem, dass sie alle die gleiche MAC-Adresse haben, behoben wurde)*

#### Fehlerbehebungen
- der Autoupdater geht mit timeouts seiner wget-Instanz nun besser um  
  *(in [2016.2.2](#gluon-versionen_2016-2-2) konnte der Autoupdater bei einem timeout bis zum nächsten Neustart festhängen und keine Updates mehr ziehen)*
- respondd wird nun bei einem crash automatisch neugestartet  
  *(trat in der vorherigen Version relativ häufig auf; warum ist unklar)*


### 2016.2.2
**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern aktualisiert nach längerer Betriebszeit bis zum nächsten Neustart gar nicht mehr.

**Veröffentlichungsdatum**: 18.12.2016  
**offizielle Versionshinweise**: [2016.2.2](https://gluon.readthedocs.io/en/v2016.2.2/releases/v2016.2.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.2)

#### Unterstützung für weitere TP-Link-Geräte
- CPE210/510 mit EU/US Standard-Firmware-Versionen
- TL-WA801N/ND v3
- TL-WR841ND v11 mit EU/US Standard-Firmware-Versionen

#### Fehlerbehebungen
- eine Reihe Fehler, welche mit [2016.2.1](#gluon-versionen_2016-2-1) und [2016.2](#gluon-versionen_2016-2) auftraten, wurden behoben
- vertauschte, initiale Zuordnung von WAN/LAN auf der CPE210 wurde behoben
- LED-Anzeige der Empfangsstärke verbraucht nun deutlich weniger Leistung und flackert weniger stark
- `/tmp`-Verzeichnis wird beim Kompilieren nicht mehr verwendet (konnte zu Daten auf ungewollten Partitionen führen)

#### bekannte Bugs
- wget-Instanz des Autoupdaters blockiert eventuell den Autoupdater bis zum nächsten Neustart, bei einem timeout 


### 2016.2.1
**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern aktualisiert nach längerer Betriebszeit bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis**: Beim Aufsplitten des gemeinsamen Profils von CPE210 und CPE510 in zwei einzelne Profile, ist ein Fehler unterlaufen, welcher WAN- und LAN-Port der CPE210 verdreht. Der Fehler tritt nur bei einem kompletten Neuflash auf, nicht bei Autoupdates.  
Dies beeinträchtigt den normalen Betrieb nicht, ist aber unschön und kann bei erweiterter, manueller Konfiguration zu Verwirrung führen.

**Veröffentlichungsdatum**: 08.11.2016  
**offizielle Versionshinweise**: [2016.2.1](https://gluon.readthedocs.io/en/v2016.2.1/releases/v2016.2.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.1)

- WLAN-Treiber Aktualisierungen  
  *die Stabilität ist immer noch nicht perfekt, sollte aber besser sein als in den 2016.1.x Releases*
    - alle Änderungen, welche seit [2016.2](#gluon-versionen_2016-2) Probleme verursachen wurden rückgängig gemacht
    - alle Änderungen, welche seit [2016.2](#gluon-versionen_2016-2) die Unterstützung für ath10k (Archer) mit sich brachten, wurden beibehalten
- die Statuspage lässt sich jetzt auch mit deaktivierten Cookies und local storage aufrufen und benutzen
- Kernel auf 3.18.44 aktualisiert um 2 Sicherheitslücken zu schließen
- Unterstützung für TL-WA901D v4 hinzugefügt


### 2016.2
**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern aktualisiert nach längerer Betriebszeit bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis2:** Laut den Gluon-Entwicklern und anderen Communities gibt es seit dieser Version Probleme mit ath9k, wodurch auf vielen unseren Geräten es zu verschwundenen und nicht sichtbaren WLANs und ständigen Neustarts kommen könnte.  
Aus diesem Grund haben wir das Release von Firmware basierend auf [Gluon 2016.2](#gluon-versionen_2016-2) zurückgenommen und verzögert.

**Veröffentlichungsdatum**: 21.09.2016  
**offizielle Versionshinweise**: [2016.2](https://gluon.readthedocs.io/en/v2016.2/releases/v2016.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2)

- der "Expertenmodus" ist nun zu "Erweiterte Einstellungen" umbenannt worden

#### neue Funktionen
- Unterstützung für eine Reihe an neuen Geräten; vor allem solche mit ath10k Chipsatz/Treiber
    - offizielle Unterstützung für Archer C5/C7 und andere ath10k-Geräte durch Option zum Auswählen für den im Image installierten Mesh-Modus (IBSS oder 11s)
- viele UBNT Airmax XM Modell werden nun richtig erkannt und nicht mehr nur als "Bullet" angezeigt
- neue Option zum Behalten der manuell eingestellten WLAN-Channel während eines Updates
- PoE-Passtrough kann nun in der site.conf und auch beim Einrichten im Konfigurationsmodus in den Erweiterten Einstellungen der TP-Link CPE 210/510 eingestellt werden
- das Feld "Höhe" kann nun von der Community im Konfigurationsmodus versteckt werden
- das Feld "Kontakt" kann von der Community nun verpflichtend gemacht werden
- "hostnames" können jetzt alle UTF-8 Zeichen enthalten
- der SSH-Server "dropbear" wurde aktualisiert und erhält so weitere SSH Verschlüsselungsmethoden und lässt veraltete fallen (DSA), welches die Zeit für den ersten Start und den generelle Verbindungsaufbau verkürzt
- 802.11b ist nun deaktivierbar (verhindert langsame Übertragungsrate für alle Geräte an einem Knoten, solange ein einzelnes veraltetes Gerät verbunden ist)

#### Fehlerbehebungen
- die Stabilität des ath9k WLAN-Treiber wurde bedeutend verbessert
- multiple unnötig laufende Instanzen vom Autoupdater werden nun mit einem Lockfile verhindert
- ein Fehler von fest eingestellten DNS-Servern seit [2016.1.6](#gluon-versionen_2016-1-6) wurde behoben


### 2016.1.6
**Bug-Hinweis:** In dieser Version gibt es ein Problem mit statisch konfigurierten DNS-Servern. fastd kann dann keine Verbindung zu einem Gateway aufbauen.

**Veröffentlichungsdatum**: 07.09.2016  
**offizielle Versionshinweise**: [2016.1.6](https://gluon.readthedocs.io/en/v2016.1.6/releases/v2016.1.6.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.6/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.6) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.6)
- einige Fehler beim Kompilieren behoben
- Unterstützung für link-lokale IPv6-DNS Server implementiert
- Verbesserung der Empfangsleistung für CPE210/510 um etwa 20db
- Wechsel der WAN/LAN-Port Zuordnung bei Ubiquiti UAP Pro (PoE-Port ist jetzt WAN, wie auch Standard bei anderen Geräten)
- generelle Treiberverbesserungen und -fehlerbehebungen
- Unterstützung für Ländercodes der neuen Firmwares für TP-Link Archer C7 v2


### 2016.1.5
**Veröffentlichungsdatum**: 26.05.2016  
**offizielle Versionshinweise**: [2016.1.5](https://gluon.readthedocs.io/en/v2016.1.5/releases/v2016.1.5.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.5/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.5) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.5)
- Unterstützung für 9 weitere Geräte von OpenMesh, Ubiquiti und TP-Link  
  insbesondere der TL-WR841N/ND v11
- einige Fehler beim Kompilieren behoben
- einige Fehler, welche ab [2016.1.4](#gluon-versionen_2016-1-4) auftraten
  - 5-Ghz-Frequenzband auf Archer C5/C7 funktioniert nun  
    **Hinweis:** auf dem 5-Ghz-Frequenzband ist kein Mesh möglich
  - Fehler mit VLANs und IBSS behoben
- auf allen Ubiquiti AirMAX Geräten kann die Firmware nun direkt installiert werden, ohne das zuvor nötige Downgrade auf AirOS 5.5.x durchführen zu müssen


### 2016.1.4
**Veröffentlichungsdatum**: 27.04.2016  
**offizielle Versionshinweise**: [2016.1.4](https://gluon.readthedocs.org/en/v2016.1.4/releases/v2016.1.4.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.4/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.4) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.4)
- umfassendes WLAN-Treiber-Update
- einige Fehlerbehebungen für das Kompilieren; auch bei Parallelisierung


### 2016.1.3
**Veröffentlichungsdatum**: 31.03.2016  
**offizielle Versionshinweise**: [2016.1.3](https://gluon.readthedocs.org/en/v2016.1.3/releases/v2016.1.3.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.3/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.3) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.3)
- Unterstützung für 2 weitere Geräte
- zufälliges Aufhängen beim Boot wurde behoben
- Gluon unterstützt nun auch Systeme, welche LibreSSL anstatt von OpenSSL verwenden


### 2016.1.2
**Veröffentlichungsdatum**: 09.03.2016  
**offizielle Versionshinweise**: [2016.1.2](https://gluon.readthedocs.org/en/v2016.1.2/releases/v2016.1.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.2)
- Unterstützung für FUTRO Thin Clients (x86) (gut als Offloaders)


### 2016.1.1
**Veröffentlichungsdatum**: 02.03.2016  
**offizielle Versionshinweise**: [2016.1.1](https://gluon.readthedocs.org/en/v2016.1.1/releases/v2016.1.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.1)
- Unterstützung für 2 weitere Geräte
- opkg repository key wird nicht mehr bei jedem build überschrieben
- Gluon kann jetzt direkt auf Airmax M XM/XW mit AirOS 5.6.x installiert werden, kein Downgrade mehr nötig
- bug fixes für die neue Statusseite
- config mode fixes
- Zugang zum failsave mode für TL-WDR4900 behoben


### 2016.1
###### *urspr. 2015.2*
**Veröffentlichungsdatum**: 08.02.2016  
**offizielle Versionshinweise**: [2016.1](https://gluon.readthedocs.org/en/v2016.1/releases/v2016.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1)
- Unterstützung für mehr Geräte, vor allem:
  - TP-Link TL-WR841 v10
  - CPE210/220/510/520 v1.1
  - airGateway
  - airRouter
  - UniFi AP Outdoor+
- neue Status-Seite  
  - optisch ansprechend
  - Echtzeit-Grafiken für Signalstärke für alle Nachbar-Knoten
  - hilft beim genauen Ausrichten von Antennen
- 802.11s Support  
  ermöglicht Unterstützung von mehr Geräten, deren Treiber das jetzige Setup von gleichzeitigem ad-hoc- und infrastructure-mode nicht unterstützen


### 2015.1.2
**Veröffentlichungsdatum**: 09.08.2015  
**offizielle Versionshinweise**: [2015.1.2](https://gluon.readthedocs.org/en/v2015.1.2/releases/v2015.1.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2015.1.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2015.1.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2015.1.2)
- Unterstützung für mehr Geräte
- eigene Images (nur umbenannte Kopien) für einige Ubiquiti Geräte, welche bis jetzt das Bullet M Image benutzen mussten, für mehr Klarheit und Einfachheit
- Download-Link von OpenSSL korrigiert


### 2015.1.1
**Veröffentlichungsdatum**: 17.06.2015  
**offizielle Versionshinweise**: [2015.1.1](https://gluon.readthedocs.org/en/v2015.1.1/releases/v2015.1.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2015.1.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2015.1.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2015.1.1)
- Unterstützung für ein weiteres Gerät
- Download-Link von OpenSSL korrigiert
- Problem mit der LED-Anzeige für die Signalstärke bei TP-Link CPE210/510 behoben


### 2015.1
**Veröffentlichungsdatum**: 16.05.2015  
**offizielle Versionshinweise**: [2015.1](https://gluon.readthedocs.org/en/v2015.1/releases/v2015.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2015.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2015.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2015.1)
- Unterstützung für mehr Geräte
- Zweisprachiger Config-Mode (Deutsch; Englisch)
- Mesh-on-LAN
- Option um Mesh oder Client Netzwerke standardmäßig auszuschalten
- fastd "performance mode" mit ausgeschalteter Verschlüsselung
- optionales Feld für Höhe in Geo-Daten
- Vorbereitung von announced um alfred zu ersetzen
- Option um beim Aufruf des Autoupdaters temporär einen anderen Branch zu wählen
- vorgegebenes Namens-Prefix jetzt optional


### 2014.4
**Veröffentlichungsdatum**: 30.12.2014  
**offizielle Versionshinweise**: [2014.4](https://gluon.readthedocs.org/en/v2014.4/releases/v2014.4.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2014.4/index.html#supported-devices)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2014.4) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2014.4)
- Update auf OpenWRT 14.09 (Barrier Breaker)  
  mehr Stabilität und mehr Performance
- Unterstützung für mehr Geräte
- Privates WLAN bridged with WAN möglich
- fastd v16 mit UMAC  
  mehr Sicherheit und Performance
- Option um SSH-Keys fest in die Firmware zu integrieren
- Node-Status-Page erkennt Nachbar-Nodes und zeigt ihre Namen an und macht sie klickbar


### 2014.3.1

**Hinweis:** Auf Basis dieser Gluon Version wurde nie eine Freifunk Bremen Firmware entwickelt und gebaut. Dieser Eintrag dient nur der Vervollständigung der in Gluon getätigten Änderungen über Zeit.

**Veröffentlichungsdatum**: 20.10.2014  
**offizielle Versionshinweise**: [2014.3.1](https://gluon.readthedocs.org/en/v2014.3.1/releases/v2014.3.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2014.3.1/index.html#supported-devices)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2014.3.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2014.3.1)
- Fehler mit der neuen Statusseite durch leere gluon-announced Prozesse behoben
- Fehler mit der inkorrekten Entfernung von fastd peers aus der Konfiguration beim Upgrade, wenn sie aus der site.conf entfernt wurden behoben
- beim setzen eines SSH-Passworts im Experten Modus, werden bestehende SSH-Keys nicht mehr entfernt
- alfred Update sollte Fehler beheben
- DHCPv6 Fehler behoben
- WLAN-Stabilität verbessert
- Support für statische IP Konfiguration für den WAN-Port im Experten Modus
- Mesh-VPN kann über die site.conf nur standardmäßig aktiviert werden


### 2014.3
**Veröffentlichungsdatum**: 02.08.2014  
**offizielle Versionshinweise**: [2014.3](https://gluon.readthedocs.org/en/v2014.3/releases/v2014.3.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2014.3/index.html#supported-devices)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2014.3) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2014.3)
- Unterstützung für ein weiteres Gerät
- Autoupdater wurde neugeschrieben
  - geplante Updates mit Datumsangabe möglich
  - zeitlich verteiltes Update möglich mit Angabe eines Zeitraums
- erste Implementation von announced für querys von nodeinfo Daten für zukünftige Statuspage
- erste Implementation für fastd/VPN über IPv6
- Mesh-on-WAN hinzugefügt
- site.conf wird nach dem Kompilieren validiert
- ath9k verbessert für bessere WLAN Stabilität
- IPv6 nun präferiert für wget (Autoupdater und NTP)


### 2014.2
**Veröffentlichungsdatum**: 24.06.2014  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2014.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2014.2)
#### Fehlerbehebungen:
- Stark verbesserte Stabilität des ath9k-WLAN-Treibers (besonders auf
TP-Link-Hardware; auf einigen Ubiquiti-Geräten scheint es zwar besser
geworden zu sein, aber noch immer problematisch)

- Gluon-Knoten beantworten keine DNS-Requests auf dem WAN-Port mehr (war
problematisch bei Nodes mit öffentlicher IP auf dem WAN-Port wegen DNS
Amplification Attacks)

#### Support für neue Hardware:
- TP-Link TL-WR841N/ND v9
- TP-Link TL-WR842N/ND v2
- TP-Link TL-WA901N/ND v2
- TP-Link TL-MR3420 v2
- D-Link DIR-615 rev. E1
- D-Link DIR-825 rev. B1

#### Änderungen unter der Haube:
- Neues site.conf-Format auf Lua-Basis. Die site.conf wird jetzt als
ganzes Teil der Firmware, was sie deutlich flexibler macht. Ein guter
Teil unserer Skripte in der Firmware wurde von Shell nach Lua portiert.
(Aktuell wird beim Bauen nur die Syntax der site.conf überprüft, nicht
aber ob der Inhalt sinnvoll ist... das wird im nächsten Release behoben)
- gluon-alfred sendet seine Daten jetzt gzip-komprimiert (großer
Vorteil: ein Datenpaket passt jetzt in einen einzelnen Ethernet-Frame)
- Verschiedenste Erweiterungen der Daten, die gluon-alfred sammelt
(Speicherverbrauch, Anzahl der Prozesse)
- Viele OpenWrt-make-targets funktionieren jetzt auch mit Gluon (z.B.
`make package/fastd/install` um das Paket fastd zu bauen, und `make
target/linux/clean`, um den Kernel-Tree zu säubern)
- Neue Option opkg_repo in der site.conf, um das Default-opkg-Repo zu
überschreiben

Support für nicht-ar71xx-Platformen und VPN-Verbindungen über
IPv6-Internet-Anschlüsse haben es leider nicht mehr in dieses Release
geschafft, das wird dann in [Gluon 2014.3](#gluon-versionen_2014-3) nachgeliefert :D