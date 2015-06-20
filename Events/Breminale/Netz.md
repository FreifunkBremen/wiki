## Ziele

### Allgemein

Jeder Besucher der Breminale sollte über unser Netz einen möglichst performanten Zugang zum Internet erhalten, sowie auf Dienste von uns zugreifen können. Am besten:

* Ausreichend Access-Points für alle Besucher (10-20k) auf dem gesamten Gelände (25.000 m²).
* Unbegrenzte Bandbreite und geringe Latenz ins Internet.
* Egal was ausfällt, der Rest sollte weiter funktionieren.

Welche Ziele wir davon wie weit erreichen können, hängt ab von:
* Freiwilligen Helfern
* Leihgaben
* Finanzierung der Internet-Anbindung und benötigter Materialien ([[Events/Breminale/Finanzierungen]])

### Wir wünschen uns

* Möglichst viele Helfer
* Zentraler Router auf dem Gelände. Ein Ersatzgerät wäre gut.
* Switches: Gbit-Switches wo möglich.
* Access-Points: Möglichst Dual-Band.
* Kabel und sonstiges Material
* Evtl. Richtfunk-Antennen

Genauere Auflistung von Material und Stückzahlen:
[[Events/Breminale/Material]]

## Umsetzung

### Haftung

Es gibt zwei Varianten, wovon die Variante ohne VPN performanter und weniger störanfällig ist:

1. ~~Sternkultur ist Anschlussinhaber, Traffic wird über VPN von Mortzu getunnelt~~
2. Digineo GmbH ist Anschlussinhaber, Traffic geht direkt raus. "Wird wohl gehen"

### Komponenten (haben wir sicher)

* Gbit-Fiber und Transceiver (SFP-Modul) von LWLCOM
* 100m SingleMode Patchkabel und Adapter (Walter)
* Zentraler Router: EdgeRouter Lite (Julian), Backup: ?
* Switch: HP 1920-8G mit SFP (Julian)
* Kleine Debian-Kiste für Monitoring und andere Dienste (Julian), Backup?
* WDR3600/WDR4300 als Nodes (Julian und nukeUS)

### Router-Konfiguration

* IPv4-Netz: 10.169.128.0/19 ist noch frei
* IPv6-Netz: wird von LWLCOM zugewiesen
* DNS-Cache und Forwarder
* GRE-Tunnel zu einem VPN-Server für Verbindung zum restlichen Freifunk-Netz (Redundanz ist nicht so wichtig).

### Router-Standort
* **Sternkultur Büro-Container**  
  Standort Höhe Deichstraße; nicht 100% sicher nachts (nächtliche Abschaltung und Lagerung im Lager-Container?)
* **Sternkultur Lagercontainer**  
  Standort Höhe Deichstraße; immer bewacht, dickes Schloss, Zugriff auf die Hardware erschwert
* **Duschcontainer der Darsteller** - aktuell bevorzugte Variante  
  Standort Höhe Mozartstraße  
  direkt bei LWLcom Uplink; nicht im Dach möglich, nur auf dem Dach oder daneben; nicht 100% sicher, jedoch keiner vermutet Server-Hardware dort, wir sparen uns 160 Meter an Kabeln für die Anbindung; umzäunt aber nicht gesichert
  10 Meter Glasfaser-Verlängerung benötigt, sowie eine wasserfeste Box 

### Node-Konfiguration

* Angepasste Freifunk-Firmware mit einem "Breminale-Key"
* Kein Meshing
* Firewall: Vollständig deaktivieren für br-wan?
* Bridges:
  * br-client: Freifunk-Netz
  * br-wan: Management-Netz
* Switch-Konfiguration
  * VLAN 1: Management-Netz
  * VLAN 2: Freifunk-Netz
  * VLAN 3: Büro-Netz
  * ein eigenes untagged VLAN pro Port zur Ermittlung der Topologie (corny: habe ich jplitza so richtig verstanden?)
* WLANs:
  * bremen.freifunk.net (unverschlüsselt) an br-client
  * management (WPA2-PSK) an br-wan
* WLAN-Kanäle und Sendeleistung:
  * 2.4 GHz: Kanäle 1,5,9,13 und 10 dBm Sendeleistung (Empfehlung von morpheus)
  * 5 GHz: Kanäle 100-140
* Announced soll die Anzahl der 2.4 und 5 GHz-Clients getrennt ausgeben.


### Node-Standorte
* in den Stromverteilerkästen; zum Weiterleiten
* in Ständen zwischen den Musikzelten
* in Bierständen
* Musikzelte? niedrigere Priorität (Ansprechpartner ist der Elektriker oder Max; selten ein Zelt-Beauftragter)

### Management und Monitoring

* Muss auch ohne Internet funktionieren
* Konfiguration der Nodes: Shell-Scripting, Ansible, ... ?
* Monitoring: Icinga, Karte mit Router-Positionen, ... ?
* ...

### Verkabelung

#### Aufbau
Sobald am Mi 08.07. die Verlegung der Stromkabel erfolgt, können wir starten die Netzwerkkabel an ihnen entlang zu legen und mit Kabelbindern festzumachen. Brilliant wäre es am Do 09.07. zum Ende des Tages fertig zu sein, damit wir am Fr 10.07. uns nicht in die Quere kommen mit den "Zeltaufbauern".

#### Infos
* LWLcom Glasfaser-Anschluss auf Höhe Mozartstraße
* Sternkultur Büro-Container auf Höhe Deichstraße
* bessere Variante/Standort für Router am/auf Duschcontainer; direkt an Mozartstraße
* Kabel entlang der Wasserrohre und -schläuche ist gesetzlich nicht erlaubt (weiterführende Nachfrage bei Sternkultur läuft)
* Netzwerkkabel entlang von Stromkabeln werden stark gestört, deswegen wird der Hinweis von Nebirosh ernst genommen und Cat7e Kabel genommen

#### Bereiche

##### Deichwiesen

Wurde beim [Treffen](/Events/Breminale/Treffen/2015_06_15-viertes-Breminale-Treffen) entschieden:

* Verkabelung der Stromkästen: Cat.7 und Netzwerkdosen/Patchpanels mit zentraler Erdung
* Kürzere Strecken mit höchstens 10 Metern Starkstrom: Cat.5e-Patchkabel

Falls nicht genug Kabel vorhanden, wird nicht die Breminale hoch UND runter (im Deichknick UND and der Weser) verkabelt, sondern nur im Deichknick. Die Reichweite der Router sollte ausreichen.

##### Himmlische Wiese
Der Tunnel ist mit 120 m erstmal zu lang für ein Kupferkabel.
Strom würde für uns and den Tunneleingang extra für uns gelegt werden.
Lampions hängen entlang der himmlischen Wiese an der Straße und habe eine direkte Verbindung zum Backstage des Himmelwärts. In die Stände/Zelte kommen WDR-Nodes. Zwei Optionen für die Anbindung:
* Richtfunk mit NanoStations über die Straße
* LWL-Kabel durch den Tunnel (200m evtl. von Walter)

##### Treue
* Richtfunk mit NanoStations vom Fahnenmast zum Schiff
* Auf und im Schiff normale WDR-Nodes

### Strukturübersicht (nicht aktuell)
Hier eine kleine [(Google-) Karte](https://www.google.de/maps/@53.0708917,8.8166142,16z/data=!3m1!4b1!4m2!6m1!1szLIdiavRRcUY.kHkfMt2Tp8Dk?hl=de) [[Detailiert](https://www.google.com/maps/d/edit?mid=zLIdiavRRcUY.kHkfMt2Tp8Dk)], für den mögliche Aufbau.

Diese sollte nachher genutzt werden um die Geräte nachzuverfolgen, damit nichts verloren geht.
