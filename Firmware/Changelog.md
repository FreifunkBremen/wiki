# Firmwareversions Changelog

Diese Seite dokumentiert oberflächlich und als Übersicht alle Änderungen an der Freifunk Bremen Firmware sowie den zugrunde liegenden Gluon Versionen. Für detailliertere Änderungen kann den jeweilinge Links zum Quellcode gefolgt werden.

- [**Freifunk Bremen Versionen**](#freifunk-bremen-versionen)  
  eine Liste aller Freifunk Bremen Firmware Versionen mit allen Bremen-spezifischen Änderungen sowie bedeutenden Änderungen beim Sprung auf eine neue Gluon Basis
- [**Gluon Versionen**](#gluon-versionen)  
  eine Liste aller Gluon Versionen mit einer übersetzten und vereinfachten Liste der Neuerungen und Fehlerkorrekturen


## Freifunk Bremen Versionen

Der Quellcode der Freifunk Bremen Firmware liegt bei [Github](https://github.com/FreifunkBremen/gluon-site-ffhb).  
Die verschiedenen Varianten der Freifunk Bremen Firmware werden auf entsprechenden [[Varianten]]-Wiki-Seite erklärt.Die Firmware-Images der Freifunk Bremen Software sind auf dem [Download-Server](https://downloads.bremen.freifunk.net/firmware/) zu finden.  
Die jeweiligen Unterordner haben folgende Bedeutungen:


- [**`all`**](https://downloads.bremen.freifunk.net/firmware/all/) listet die Ordner aller einzelnen Versionen der Freifunk Bremen Firmware auf  
- [**`nightly`**](https://downloads.bremen.freifunk.net/firmware/nightly/) verweist auf den gleichen Inhalt wie [**`testing`**](https://downloads.bremen.freifunk.net/firmware/testing/), da wir aktuell keine nächtlichen Builds erstellen und veröffentlichen.
- [**`stable`**](https://downloads.bremen.freifunk.net/firmware/stable/) verweist auf die Images der aktuell als stabil deklarierten Firmwareversion  
- [**`testing`**](https://downloads.bremen.freifunk.net/firmware/testing/) verweist auf die Images der aktuell im Test befindlichen Firmwareversion

*Falls sich Geräte auf dem `exp`-Branch befinden, so werden sie keine Updates beziehen, da dies kein offizieller Branch ist und die Einstellung durch einen Fehler entstanden ist.  
Experiementelle Firmware-Versionen werden nicht offiziell unterstützt und werden meist für extrem frühe Tests verwendet. Normalerweise sollte als Branch `testing` eingestellt sein, damit sie sich später bei einer stabilien Veröffentlichung Updates holen.*

Branch        | aktuelle Version                                                    | signed by
---           | ---                                                                 | ---
**`stable`**  | [2016.2.3+bremen1](#freifunk-bremen-versionen_2016-2-3-bremen1)     | `SimJoSt`, `corny`
**`testing`** | [2016.2.4+bremen1](#freifunk-bremen-versionen_2016-2-4-bremen1)     | `nightly-builder`, `SimJoSt`

Es folgt eine Liste aller Freifunk Bremen Firmware-Versionen mit allen Bremen-spezifischen Änderungen sowie bedeutenden Änderungen beim Sprung auf eine neue Gluon Basis.

### 2016.2.4+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [24.03.2017](http://downloads.bremen.freifunk.net/firmware/all/2016.2.4+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.4+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.4+bremen1)  
**gluon-Version**: [2016.2.4](#gluon-versionen_2016-2-4)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.4+bremen1/)

- gluon-radv-filterd aktualisiert aus dem Gluon-PR
  - Hatte einen Fehler im Code der für das Parsen der Originators zuständig war
- vpn04 entfernt
  - Hatte massive Probleme mit Abstürzen und stand bei Hetzner
- Paket gluon-alfred entfernt
  - Mit dem Wechsel auf die neue Webseite, den neuen Meshviewer und damit Yanic und respondd wird Alfred endlich nicht mehr gebraucht

### 2016.2.3+bremen3
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [03.03.2017](https://downloads.bremen.freifunk.net/firmware/all/2016.2.3+bremen3/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.3+bremen3) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.3+bremen3)  
**gluon-Version**: [2016.2.3](#gluon-versionen_2016-2-3)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.3+bremen3/)

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
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.3+bremen2/)

**Bug-Hinweis:** Durch die unvollständige Aktualisierung von gluon-radv-filterd könnte dieses Paket in einem vollkommen kaputten Zustand sein. Bitte stattdessen 2016.2.3+bremen3 verwenden!

- Altes Übergangspaket gluon-wan-dnsmasq-static entfernt, das eine Bremen-spezifische Konfiguration in die seit Mitte 2015 in Gluon integrierte Konfiguration überführt
- gluon-radv-filterd aktualisiert aus dem Gluon-PR (leider unvollständig, weswegen +bremen3 fällig wurde)

### 2016.2.3+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [03.03.2017](https://downloads.bremen.freifunk.net/firmware/all/2016.2.3+bremen1/sysupgrade/stable.manifest)    
**Veröffentlichung auf dem `testing`-Branch**: [13.02.2017](https://downloads.bremen.freifunk.net/firmware/all/2016.2.3+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.3+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.3+bremen1)  
**gluon-Version**: [2016.2.3](#gluon-versionen_2016-2-3)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.3+bremen1/)

- Update auf Gluon 2016.2.3
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
**Veröffentlichung auf dem `testing`-Branch**: [19.12.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.2.2+bremen1/sysupgrade/testing.manifest)   
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.2+bremen1)  
**gluon-Version**: [2016.2.2](#gluon-versionen_2016-2-2)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.2.2+bremen1/)

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern updated nach längerer Uptime bis zum nächsten Neustart gar nicht mehr.

- Update auf Gluon 2016.2.2
    - Unterstützung für 3 neue TP-LINK Geräte
    - einige Fehler seit [2016.2.1](#gluon-versionen_2016-2-1) und [2016.2](#gluon-versionen_2016-2) behoben  
      inkl. vertauschtem WAN/LAN-Port auf CPE210 bei initialem Flash

#### bekannte Bugs
- wget-Instanz des Autoupdaters blockiert eventuell den Autoupdater bis zum nächsten Neustart, bei einem timeout 


### 2016.2.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [08.11.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.2.1+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2.1+bremen1)  
**gluon-Version**: [2016.2.1](#gluon-versionen_2016-2-1)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern updated nach längerer Uptime bis zum nächsten Neustart gar nicht mehr.

- Update auf Gluon 2016.2.1
    - WLAN-Treiber Probleme behoben
- Bug: auf CPE210 WAN- und LAN-Port bei kompletten Neuflash verdreht


### 2016.2+bremen2
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2+bremen2)  
**gluon-Version**: [2016.2](#gluon-versionen_2016-2)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern updated nach längerer Uptime bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis2:** Laut den Gluon Entwicklern und anderen Communites gibt es seit dieser Version Probleme mit ath9k, wodurch auf vielen unseren Geräten es zu verschwundenen und nicht sichtbaren WLANs und ständigen Neustarts kommen könnte.  
Aus diesem Grund haben wir das Release von Firmware basierend auf Gluon 2016.2 zurückgenommen und verzögert.

- 802.11b deaktiviert
- Paket gluon-radv-filterd aufgenommen (lässt nur das IPv6 Router Advertisement vom laut batman-adv besten Gateway durch)
- Unseren OpenWrt-Proxy in `/etc/opkg/distfeeds.conf` eingetragen (dadurch funktioniert `opkg update` nun auch auf Knoten ohne WAN-Anschluss)


### 2016.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
<!--[07.10.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.2+bremen1/sysupgrade/testing.manifest)-->  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.2+bremen1)  
**gluon-Version**: [2016.2](#gluon-versionen_2016-2)  
**Download**: *nicht mehr verfügbar*

**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern updated nach löngerer Uptime bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis2:** Laut den Gluon Entwicklern und anderen Communites gibt es seit dieser Version Probleme mit ath9k, wodurch auf vielen unseren Geräten es zu verschwundenen und nicht sichtbaren WLANs und ständigen Neustarts kommen könnte.  
Aus diesem Grund haben wir das Release von Firmware basierend auf Gluon 2016.2 zurückgenommen und verzögert.

- Update auf Gluon 2016.2
    - ath10k-Geräte wie Archer C5/C7 unterstützen nun Meshing auf 5 Ghz
    - manuell eingestellte WLAN-Channel können nun mit einer Option updatefest gemacht werden
    - Knoten-Namen können nun all UTF-8 Zeichen enthalten
    - SSH-Server auf den Knoten aktueller und performanter
    - Fehler im Autoupdater (multiple Instanzen) behoben
- das Feld "Höhe" wird im Konfigurationsmodus nicht mehr angezeigt (solange nicht schon ein Wert gesetzt wurde)


### 2016.1.6+bremen1.1
**Bug-Hinweis:** In Gluon 2016.1.6 gibt es ein Problem mit statisch konfigurierten DNS-Servern. fastd kann dann keine Verbindung zu einem Gateway aufbauen.

**Veröffentlichung auf dem `stable`-Branch**: [23.11.2016](http://downloads.bremen.freifunk.net/firmware/all/2016.1.6+bremen1.1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [11.10.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1.6+bremen1.1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.6+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.6+bremen1)  
**gluon-Version**: [2016.1.6](#gluon-versionen_2016-1-6)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.1.6+bremen1.1/)

*Bei Firmware-Version [2016.1.6+bremen1](#freifunk-bremen-versionen_2016-1-6-bremen1) wurden keine Images für die TP-Link Archer C5/C7 generiert. Diese Version ist auf ein erneuter Build auf dem gleichen Quellcode, jedoch mit Archer C5/C7 Images.*


### 2016.1.6+bremen1
**Bug-Hinweis:** In Gluon 2016.1.6 gibt es ein Problem mit statisch konfigurierten DNS-Servern. fastd kann dann keine Verbindung zu einem Gateway aufbauen.

**Veröffentlichung auf dem `stable`-Branch**: [07.10.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1.6+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [20.09.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1.6+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.6+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.6+bremen1)  
**gluon-Version**: [2016.1.6](#gluon-versionen_2016-1-6)  
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2016.1.6
    - deutlich verbesserter Empfang auf TP-Link CPE210/510 (etwa 20db)
- Option zum Abschalten der fastd-Verschlüsselung für die VPN-Verbindung zu den Freifunk Bremen Gateways für den Konfigurationsmodus hinzugefügt
- die Region für die Firmware wurde auf `EU` gesetzt, so dass das Aufspielen von Freifunk Bremen Firmware auf Archer C7 Geräten mit aktueller Standard-Firmware möglich ist


### 2016.1.5+bremen1
**Veröffentlichung auf dem `stable`-Branch**: [03.07.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1.5+bremen1/sysupgrade/stable.manifest)  
**Veröffentlichung auf dem `testing`-Branch**: [26.05.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1.5+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.5+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.5+bremen1)  
**gluon-Version**: [2016.1.5](#gluon-versionen_2016-1-5)  
**Download**: [Images](http://downloads.bremen.freifunk.net/firmware/all/2016.1.5+bremen1/)

- Unterstützung für TP-Link Archer C5/C7 wiederhergestellt  
  **Hinweis:** auf dem 5 Ghz Frequenzband ist kein Mesh möglich 
- Unterstützung für TP-Link WR841N/ND v11


### 2016.1.4+bremen2
**Veröffentlichung auf dem `stable`-Branch**: 24.05.2016  
**Veröffentlichung auf dem `testing`-Branch**: [06.05.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1.4+bremen2/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.4+bremen2) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.4+bremen2)  
**gluon-Version**: [2016.1.4](#gluon-versionen_2016-1-4)  
**Download**: *nicht mehr verfügbar*

- ~~Unterstützung für TP-Link Archer C5/C7~~  
  ~~**Hinweis:** auf dem 5 Ghz Frequenzband ist kein Mesh möglich~~  
  **Hinweis:** Aufgrund eines Fehlers spezifisch in Gluon 2016.1.4 funktioniert das 5Ghz-Modul der Archer-Geräte überhaupt nicht ([Gluon-Issue](https://github.com/freifunk-gluon/gluon/issues/758))  
  die Images für die Archer-Geräte wurden vom Download-Server entfernt


### 2016.1.4+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.4+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.4+bremen1)  
**gluon-Version**: [2016.1.4](#gluon-versionen_2016-1-4)  
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2016.1.4
- Port und MTU für Mesh-VPN geändert. **Dies erfordert ggf. eine Änderung in den Freigaben der Fritzbox!** Der neue Port ist UDP 50000, der alte war UDP 10000.


### 2016.1.3+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: nie  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.3+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.3+bremen1)  
**gluon-Version**: [2016.1.3](#gluon-versionen_2016-1-3)  
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2016.1.3


### 2016.1.2+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [19.03.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1.2+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1.2+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1.2+bremen1)  
**gluon-Version**: [2016.1.2](#gluon-versionen_2016-1-2)  
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2016.1.2


### 2016.1+bremen1
**Veröffentlichung auf dem `stable`-Branch**: nie  
**Veröffentlichung auf dem `testing`-Branch**: [18.02.2016](https://downloads.bremen.freifunk.net/firmware/all/2016.1+bremen1/sysupgrade/testing.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2016.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2016.1+bremen1)   
**gluon-Version**: [2016.1](#gluon-versionen_2016-1)  
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2016.1
- vpn05 hinzugefügt
- eigenes opkg-Repository für die Kernel Module für Freifunk Bremen hinzugefügt
- TP-Link WR841N/ND v10 Unterstützung


### 2015.2+bremen3~exp
**Release-Datum**: [25.12.2015](https://downloads.bremen.freifunk.net/firmware/all/2015.2+bremen3~exp/sysupgrade/exp.manifest)  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.2+bremen3-exp) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.2+bremen3-exp)   
**gluon-Version**: [2015.2](#gluon-versionen_2016-1) (unfertig; noch in der Entwicklung)  
**Download**: *nicht mehr verfügbar*

- auf den aktuellsten Entwicklungsstand von Gluon 2015.2 upgedated


### 2015.1.2+bremen3
**Veröffentlichung auf dem `stable`-Branch**: [30.12.2015](https://downloads.bremen.freifunk.net/firmware/all/2015.1.2+bremen3/sysupgrade/stable.manifest)   
**Veröffentlichung auf dem `testing`-Branch**: [18.12.2015](https://bremen.freifunk.net/blog/2015/12/30/v2015-1-2-bremen3-wird-stable.html)  
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
**Release-Datum**: [15.12.2015](https://downloads.bremen.freifunk.net/firmware/all/2015.1.2+bremen3~testing/sysupgrade/testing.manifest) ([Blogpost](https://bremen.freifunk.net/blog/2015/12/16/v2015-1-2-bremen3-testing.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen3-testing) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen3-testing)   
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)    
**Download**: *nicht mehr verfügbar*

- IPv6-Präfix gewechselt
- Bugfixes
- Firmware-Mirror und Signing-Key von mortzu entfernt


### 2015.2+bremen2~exp
**Release-Datum**: 12.12.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.2+bremen2-exp) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.2+bremen2-exp)   
**gluon-Version**: [2015.2](#gluon-versionen_2016-1) (unfertig; noch in der Entwicklung)    
**Download**: *nicht mehr verfügbar*

- auf den aktuellsten Entwicklungsstand von Gluon 2015.2 upgedated
- fehlerhaftes Abschalten des WLAN-Moduls bei TP-Link TL-WR841 v10 Geräten bei [2015.2+bremen1~exp](#Freifunk-Bremen-Versionen_2015.2+bremen1~exp) behoben


### 2015.2+bremen1~exp
**Release-Datum**: 26.11.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.2+bremen1-exp) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.2+bremen1-exp)   
**gluon-Version**: [2015.2](#gluon-versionen_2016-1) (unfertig; noch in der Entwicklung)    
**Download**: *nicht mehr verfügbar*

- Update auf den aktuellen Entwicklungsstand des unfertigen Gluon 2015.2
- Support für TP-Link TL-WR841 v10


### 2015.1.2+bremen2
###### *urspr. [2015.1.2+bremen2~testing](#Freifunk-Bremen-Versionen_2015.1.2+bremen2~testing)*
**Release-Datum**: 08.11.2015  
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
**Release-Datum**: 06.09.2015   
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen2-testing) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen2-testing)   
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)    
**Download**: *nicht mehr verfügbar*

- neues Gateway VPN04 hinzugefügt


### 2015.1.2+bremen1~testing
**Release-Datum**: 29.08.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.2+bremen1-testing) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.2+bremen1-testing)  
**gluon-Version**: [2015.1.2](#gluon-versionen_2015-1-2)    
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2015.1.2


### 2015.1.1+bremen1
###### *ursrprünglich [2015.1.1+bremen1~testing](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.1+bremen1-testing)*
**Release-Datum**: 07.08.2015  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2015.1.1+bremen1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2015.1.1+bremen1)  
**gluon-Version**: [2015.1.1](#gluon-versionen_2015-1-1)    
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2015.1.1
- Node-Namen-Präfix `ffhb-` nicht mehr standardmäßig vorgegeben


### 2014.4+bremen0 - **erste Stable**
###### *ursprünglich [0.6~testing1](#Freifunk-Bremen-Versionen_0.6~testing1)*

**Release-Datum**: 28.06.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/06/28/erste-stabile-firmware.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v2014.4+bremen0) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v2014.4+bremen0)  
**gluon-Version**: [2014.4](#gluon-versionen_2014-4)    
**Download**: *nicht mehr verfügbar*

- die effizientere und schnellere fastd cipher salsa2012+umac hinzugefügt
- signing-key von corny hinzugefügt


### 0.6~testing1
**Release-Datum**: 03.05.2015 ([Blogpost](https://bremen.freifunk.net/blog/2015/05/03/neue-firmware.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v0.6-testing1) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v0.6-testing1)  
**gluon-Version**: [2014.4](#gluon-versionen_2014-4)    
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2014.4
- Link zum Eingeben des fastd key auf dem Server entfernt
- Kanalanalyse-Komponenten entfernt
- neues Gateway VPN03 hinzugefügt
- mesh ssid von mesh.ffhb zu mesh.ffhb.de geändert
- IPv6-Präfix zu 2001:bf7:540 geändert; weg von local zu public
- autoupdater URLs behoben


### 0.5~testing5
**Release-Datum**: 06.09.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/09/06/Neue-Testing-Channel-Survey.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v0.5-testing5) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v0.5-testing5)  
**gluon-Version**: [2014.3](#gluon-versionen_2014-3)    
**Download**: *nicht mehr verfügbar*

- Kanalanalyse-Komponenten integriert
- WLAN-Feintuning
  - 2,4Ghz-Kanalbreite von 40Mhz auf 20Mhz reduziert
  - Multicast-Rate auf 6 Mbit/s herabgesetzt (die Grenze ab wann 2 Knoten Meshen/sich verbinden)
- DHCP-Server und IPv6-Router hinter einem Node werden nicht mehr durchgelassen ("Funktion Internet" im Freifunk-Netz sonst leicht störbar)


### 0.5~testing4
**Release-Datum**: 08.08.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/08/08/Neue-Testing.html))  
**Github-Repository**: [Tag](https://github.com/FreifunkBremen/gluon-site-ffhb/releases/tag/v0.5-testing4) / [Commits](https://github.com/FreifunkBremen/gluon-site-ffhb/commits/v0.5-testing4)  
**gluon-Version**: [2014.3](#gluon-versionen_2014-3)    
**Download**: *nicht mehr verfügbar*

- Update auf Gluon 2014.3
- Ende der WLAN-Probleme (mit Überwachung evtl. Probleme)
- Autoupdater standardmäßig an


### 0.5~testing3
**Release-Datum**: 23.06.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/06/23/Facebook-und-Testing-3.html))  
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
- Signal-Abruch-Problem auf 2,4 Ghz
- TP-Link TL-WR841N/ND v9 macht Probleme


### 0.5~testing1 - **erste Testing**
**Release-Datum**: 24.03.2014 ([Blogpost](https://bremen.freifunk.net/blog/2014/03/24/testing-firmware.html))  
**gluon-Version**: [2014.2](#gluon-versionen_2014-2)    
**Download**: *nicht mehr verfügbar*

- alle Nightly-Geräte haben auf den Testing-Branch gewechselt
- Doppel-Key-Problem behoben



## Gluon Versionen

Der Quellcode von Gluon liegt bei [Github](https://github.com/freifunk-gluon/gluon).  
Die Dokumentation ist auf [gluon.readthedocs.io](https://gluon.readthedocs.io/) einsehbar.

Es folgt eine Liste aller Gluon Versionen mit einer übersetzten und vereinfachten Liste der Neuerungen und Fehlerkorrekturen.

### 2016.2.4

**Release-Datum**: 13.03.2017  
**offizielle Versionshinweise**: [2016.2.3](https://gluon.readthedocs.io/en/v2016.2.3/releases/v2016.2.4.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.4/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.4) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.4)

#### Bugfixes
- Hohe Load wegen des neuen respondd-Initscripts ist behoben
- Der abgeschaltete Mirror ftp.all.kernel.org wurde ersetzt
- sysupgrade funktioniert nun auf x86-Geräten besser

### Sonstige Änderungen
- Das Autoupdater-Manifest enthält nun, als Vorbereitung auf die kommende neue Version des Autoupdaters, auch SHA256-Hashes der Images statt wie bisher nur SHA512

### 2016.2.3

**Release-Datum**: 13.02.2017  
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

#### Bugfixes
- der Autoupdater geht mit timeouts seiner wget-Instanz nun besser um  
  *(in [2016.2.2](#gluon-versionen_2016-2-2) konnte der Autoupdater bei einem timeout bis zum nächsten Neustart festhängen und keine Updates mehr ziehen)*
- respondd wird nun bei einem crash automatisch neugestartet  
  *(trat in der vorherigen Version relativ häufig auf; warum ist unklar)*


### 2016.2.2

**Release-Datum**: 18.12.2016  
**offizielle Versionshinweise**: [2016.2.2](https://gluon.readthedocs.io/en/v2016.2.2/releases/v2016.2.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.2)

#### Unterstützung für weitere TP-Link-Geräte
- CPE210/510 mit EU/US Standard-Firmware-Versionen
- TL-WA801N/ND v3
- TL-WR841ND v11 mit EU/US Standard-Firmware-Versionen

#### Bugfixes
- eine Reihe Fehler, welche mit [2016.2.1](#gluon-versionen_2016-2-1) und [2016.2](#gluon-versionen_2016-2) auftraten, wurden behoben
- vertauschte, initiale Zuordnung von WAN/LAN auf der CPE210 wurde behoben
- LED-Anzeige der Empfangsstärke verbraucht nun deutlich weniger Leistung und flackert weniger stark
- `/tmp`-Verzeichnis wird beim Kompilieren nicht mehr verwendet (konnte zu Daten auf ungewollten Partitionen führen)

#### bekannte Bugs
- wget-Instanz des Autoupdaters blockiert eventuell den Autoupdater bis zum nächsten Neustart, bei einem timeout 


### 2016.2.1
**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern updated nach löngerer Uptime bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis**: Beim aufsplitten des gemeinsamen Profil von CPE210 und CPE510 in zwei einzelne Profile, ist ein Fehler unterlaufen, welcher WAN- und LAN-Port der CPE210 verdreht. Der Fehler tritt nur bei einem kompletten Neuflash auf, nicht bei Autoupdates.  
Dies beinträchtigt den normalen Betrieb nicht, ist aber unschön und kann bei erweiterter, manueller Konfiguration zu Verwirrung führen.

**Release-Datum**: 08.11.2016  
**offizielle Versionshinweise**: [2016.2.1](https://gluon.readthedocs.io/en/v2016.2.1/releases/v2016.2.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2.1)

- WLAN-Treiber Aktualisierungen  
  *die Stabilität ist imme rnoch nicht perfekt, sollte aber besser sein als in den 2016.1.x Releases*
    - alle Änderungen, welche seit [2016.2](#gluon-versionen_2016-2) Probleme verursachen wurden rückgängig gemacht
    - alle Änderungen, welche seit [2016.2](#gluon-versionen_2016-2) die Unterstützung für ath10k (Archer) mit sich brachten, wurden beibehalten
- die Statuspage lässt sich jetzt auch mit deaktivierten Cookies und local storage aufrufen und benutzen
- Kernel auf 3.18.44 aktualisiert um 2 Sicherheitslücken zu schließen
- Unterstützung für TL-WA901D v4 hinzugefügt


### 2016.2
**Bug-Hinweis:** Mit den Änderungen von 2016.2+ am Autoupdater, führt dieser nicht mehr zu Absturz der Knoten, sondern updated nach löngerer Uptime bis zum nächsten Neustart gar nicht mehr.

**Bug-Hinweis2:** Laut den Gluon Entwicklern und anderen Communites gibt es seit dieser Version Probleme mit ath9k, wodurch auf vielen unseren Geräten es zu verschwundenen und nicht sichtbaren WLANs und ständigen Neustarts kommen könnte.  
Aus diesem Grund haben wir das Release von Firmware basierend auf Gluon 2016.2 zurückgenommen und verzögert.

**Release-Datum**: 21.09.2016  
**offizielle Versionshinweise**: [2016.2](https://gluon.readthedocs.io/en/v2016.2/releases/v2016.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.2)

- der "Expertenmodus" ist nun zu "Erweiterte Einstellungen" umbenannt worden

#### neue Funktionen
- Unterstützung für eine Reihe an neuen Geräten; vor allem solche mit ath10k Chipsatz/Treiber
    - offizielle Unterstützung für Archer C5/C7 und andere ath10k-Geräte durch Option zum Auswählen für den im Image installierten Mesh-Modus (IBSS oder 11s)
- viele UBNT Airmax XM Modell werden nun richtig erkannt und nicht mehr nur als "Bullet" angezeigt
- neue Option zum Behalten der manuell eingestellen WLAN-Channel während eines Updates
- PoE-Passtrough kann nun in der site.conf und auch beim Einrichten im Konfigurationsmodus in den Erweiterten Einstellungen der TP-Link CPE 210/510 eingestellt werden
- das Feld "Höhe" kann nun von der Community im Konfigurationsmodus versteckt werden
- das Feld "Kontakt" kann von der Community nun verpflichtend gemacht werden
- "hostnames" können jetzt alle UTF-8 Zeichen enthalten
- der SSH-Server "dropbear" wurde aktualisiert und erhält so weitere SSH Verschlüsselungsmethoden und lässt veraltete fallen (DSA), welches die Zeit für den ersten Starts und der generelle Verbindungsaufbau verkürzt
- 802.11b ist nun deaktivierbar (verhindert langsame Übertragungsrate für alle Geräte an einem Knoten, solange ein einzelnes veraltetes Gerät verbunden ist)

#### Bugfixes
- die Stabilität des ath9k WLAN-Treiber wurde bedeutend verbessert
- multiple unnötig laufende Instanzen vom Autoupdater werden nun mit einem Lockfile verhindert
- ein Fehler von fest eingestellten DNS-Servern seit [2016.1.6](#gluon-versionen_2016-1-6) wurde behoben


### 2016.1.6
**Bug-Hinweis:** In dieser Version gibt es ein Problem mit statisch konfigurierten DNS-Servern. fastd kann dann keine Verbindung zu einem Gateway aufbauen.

**Release-Datum**: 07.09.2016  
**offizielle Versionshinweise**: [2016.1.6](https://gluon.readthedocs.io/en/v2016.1.6/releases/v2016.1.6.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.6/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.6) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.6)
- einige Fehler beim Kompilieren behoben
- Unterstützung für link-lokale IPv6-DNS Server implementiert
- Verbesserung der Empfangsleistung für CPE210/510 um etwa 20db
- Wechsel der WAN/LAN-Port Zuordnung bei Ubiquitii UAP Pro (PoE-Port ist jetzt WAN, wie auch Standard bei anderen Geräten)
- generelle Treiberverbesserungen und -fehlerbehebungen
- Unterstützung für Ländercodes der neuen Firmwares für TP-Link Archer C7 v2


### 2016.1.5
**Release-Datum**: 26.05.2016  
**offizielle Versionshinweise**: [2016.1.5](https://gluon.readthedocs.io/en/v2016.1.5/releases/v2016.1.5.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.5/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.5) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.5)
- Unterstützung für 9 weitere Geräte von OpenMesh, Ubiquiti und TP-Link
  - insbesondere der TL-WR841N/ND v11
- einige Fehler beim Kompilieren behoben
- einige Fehler, welche ab [2016.1.4](#gluon-versionen_2016-1-4) auftraten
  - 5 Ghz Frequenzband auf Archer C5/C7 funktioniert nun
  - Fehler mit VLANs und IBSS behoben
- auf alle Ubiquiti AirMAX Geräte kann die Firmware nun direkt installiert werden, ohne das vorher nötige Downgrade auf AirOS 5.5.x zu machen


### 2016.1.4
**Release-Datum**: 27.04.2016  
**offizielle Versionshinweise**: [2016.1.4](https://gluon.readthedocs.org/en/v2016.1.4/releases/v2016.1.4.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.4/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.4) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.4)
- umfassendes WLAN-Treiber-Update
- einige Fehlerbehebungen für das Kompilieren; auch bei Parallelisierung


### 2016.1.3
**Release-Datum**: 31.03.2016  
**offizielle Versionshinweise**: [2016.1.3](https://gluon.readthedocs.org/en/v2016.1.3/releases/v2016.1.3.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.3/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.3) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.3)
- Unterstützung für 2 weitere Geräte
- zufälliges Aufhängen beim Boot wurde behoben
- Gluon unterstützt nun auch Systeme, welche LibreSSL anstatt von OpenSSL verwenden


### 2016.1.2
**Release-Datum**: 09.03.2016  
**offizielle Versionshinweise**: [2016.1.2](https://gluon.readthedocs.org/en/v2016.1.2/releases/v2016.1.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2016.1.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2016.1.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2016.1.2)
- Unterstützung für FUTRO Thin Clients (x86) (gut als Offloaders)


### 2016.1.1
**Release-Datum**: 02.03.2016  
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
**Release-Datum**: 08.02.2016  
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
  ermöglicht Unterstützung von mehr Geräten, deren Treiber das jetzige Setup von gleichzeitigem ad-hoc- und infracstructure-mode nicht unterstützen


### 2015.1.2
**Release-Datum**: 09.08.2015  
**offizielle Versionshinweise**: [2015.1.2](https://gluon.readthedocs.org/en/v2015.1.2/releases/v2015.1.2.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2015.1.2/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2015.1.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2015.1.2)
- Unterstützung für mehr Geräte
- eigene Images (nur umbenannte Kopien) für einige Ubiquiti Geräte, welche bis jetzt das Bullet M Image benutzen mussten, für mehr Klarheit und Einfachheit
- Download-Link von OpenSSL korrigiert


### 2015.1.1
**Release-Datum**: 17.06.2015   
**offizielle Versionshinweise**: [2015.1.1](https://gluon.readthedocs.org/en/v2015.1.1/releases/v2015.1.1.html)  
**Unterstütze Hardware**: [Geräteliste](https://gluon.readthedocs.io/en/v2015.1.1/index.html#supported-devices-architectures)  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2015.1.1) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2015.1.1)
- Unterstützung für ein weiteres Gerät
- Download-Link von OpenSSL korrigiertd
- Problem mit der LED-Anzeige für die Signalstäkre bei TP-Link CPE210/510 behoben


### 2015.1
**Release-Datum**: 16.05.2015  
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
**Release-Datum**: 30.12.2014  
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

**Release-Datum**: 20.10.2014  
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
**Release-Datum**: 02.08.2014  
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
**Release-Datum**: 24.06.2014  
**Github-Repository**: [Tag](https://github.com/freifunk-gluon/gluon/releases/tag/v2014.2) / [Commits](https://github.com/freifunk-gluon/gluon/commits/v2014.2)
#### Bugfixes:
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
Teil unserer Scripte in der Firmware wurde von Shell nach Lua portiert.
(Aktuell wird beim Bauen nur die Syntax der site.conf überprüft, nicht
aber ob der Inhalt sinnvoll ist... das wird im nächsten Release behoben)
- gluon-alfred sendet seine Daten jetzt gzip-komprimiert (großer
Vorteil: ein Datenpaket passt jetzt in einen einzelnen Ethernet-Frame)
- Verschiedense Erweiterungen der Daten, die gluon-alfred sammelt
(Speicherverbrauch, Anzahl der Prozesse)
- Viele OpenWrt-make-targets funktionieren jetzt auch mit Gluon (z.B.
`make package/fastd/install` um das Paket fastd zu bauen, und `make
target/linux/clean`, um den Kernel-Tree zu säubern)
- Neue Option opkg_repo in der site.conf, um das Default-opkg-Repo zu
überschreiben

Support für nicht-ar71xx-Platformen und VPN-Verbindungen über
IPv6-Internet-Anschlüsse haben es leider nicht mehr in dieses Release
geschafft, das wird dann in Gluon 2014.3 nachgeliefert :D