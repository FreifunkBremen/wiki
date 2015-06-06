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

* Drei Varianten für das Switch: ([siehe Tests](http://wiki.bremen.freifunk.net/Events/Breminale/Netzwerk-und-LeistungsTests))
 1. Batman auf einzelne Ports  
    Verkabelung mit Redundanz möglich, Durchsatzverringerung, belastung der Node-CPU, welche schon durch die vielen Clients gefordert ist
 2. Software-Bridge mit STP  
    Verkabelung mit Redundanz möglich, Durchsatzverringerung
 3. kein STP und kein Batman  
    keine Verkabelung mit Redundanz möglich, außer einzelne manuelle Hardware-"Breaks"
* 2.4 GHz: Kanäle 1,5,9,13 und 10 dBm Sendeleistung (Empfehlung von morpheus)
* 5 GHz: Kanäle 100-140
* Angepasste Freifunk-Firmware mit SSH-Keys
* Meshing über WLAN abgeschaltet

### Node-Standorte
* in den Stromverteilerkästen; zum Weiterleiten
* in Ständen zwischen den Musikzelten
* in Bierständen (Termin für Besichtung von Beispiel-Bierständen wird organisiert)
* Musikzelte? niedrigere Priorität

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
* Entfernung von Glasfaser zu Container 140m; mit 160m Kabel auf jeden Fall rechnen
* bessere Variante/Standort für Router in Duschcontainer; direkt an Mozartstraße

#### Bereiche
##### Deichwiesen
##### Himmlische Wiese
Der Tunnel ist mit 120 m erstmal zu lang für ein Netwerkkabel.  
Strom würde für uns and den Tunneleingang extra für uns gelegt werden.  
Lampions hängen entlang der himmlischen Wiese an der Straße und habe eine direkte Verbindung zum Backstage des Himmelwärts.
##### Treue

#### Vorschläge
Vorschlag (Julian):
* Nodes (WDR3600 oder WDR4300) in Abständen von 50-100 Metern installieren, untereinander verkabeln und auf die verfügbaren WLAN-Kanäle verteilen.
* Kabel sollte robust sein und für spätere Projekte wiederverwendet werden können.
* Zentraler Router für DHCP, DNS, VPN, Load-Balancing und Traffic-Shaping

Vorschlag (Eike): (nicht aktuell, da Kabel von uns Freifunkern selbst verlegt werden)
* Das Netzwerkkabel sollte von den Personen mitverlegt werden die die Stände mit Strom verkabeln. Es wird sicher einen Plan geben was wo hinkommt auf der Breminale. Da könnten wir entsprechend markieren wo Access-Points hinsollen. Kabel dann am besten von der Rolle und wir müssen da Stecker oder Dosen anbringen.


Vorschlag (nukeUS): (nicht aktuell, Kabel werden entlang der Stromkabel gelegt, Zelte im Moment nicht explizit abgedeckt)
* Nodes (wenn nicht outdoor, dann in BrotDosen oder sonstwas für Boxen) auf vorhandenen Masten entlang des UferWeges auf der Seite zur Weser UND (mit Versatz) auf der Linie wo die DeichSchräge beginnt (Knick). So würden die Kabel beim Abbau (zB der Zelte) nicht stören. Man könnte den ein oder anderen Node aber auch in den höchsten Punkt von den Zelten hängen.

### Strukturübersicht (nicht aktuell)
Hier eine kleine [(Google-) Karte](https://www.google.de/maps/@53.0708917,8.8166142,16z/data=!3m1!4b1!4m2!6m1!1szLIdiavRRcUY.kHkfMt2Tp8Dk?hl=de) [[Detailiert](https://www.google.com/maps/d/edit?mid=zLIdiavRRcUY.kHkfMt2Tp8Dk)], für den mögliche Aufbau.

Diese sollte nachher genutzt werden um die Geräte nachzuverfolgen, damit nichts verloren geht.
