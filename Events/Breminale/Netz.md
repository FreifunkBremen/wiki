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
* bessere Variante/Standort für Router am/auf Duschcontainer; direkt an Mozartstraße
* Kabel entlang der Wasserrohre und -schläuche ist gesetzlich nicht erlaubt (weiterführende Nachfrage bei Sternkultur läuft)
* Netzwerkkabel entlang von Stromkabeln werden stark gestört, deswegen wird der Hinweis von Nebirosh ernst genommen und Cat7e Kabel genommen

#### Bereiche
##### Deichwiesen
##### Himmlische Wiese
Der Tunnel ist mit 120 m erstmal zu lang für ein Netwerkkabel.  
Strom würde für uns and den Tunneleingang extra für uns gelegt werden.  
Lampions hängen entlang der himmlischen Wiese an der Straße und habe eine direkte Verbindung zum Backstage des Himmelwärts.
##### Treue

#### Vorschläge
Vorschlag (nukeUS):

erstmal bis zu 30 + x (x = Anzahl von 5 GHz Nanostations die wir noch zusätzlich [zB leihweise] bekommen könnten) WDRs oben auf dem Deich entlang der 700m relativ gleichmässig verteilen.
Dazu leider wieder Daisy-Chain (http://en.wikipedia.org/wiki/Network_topology#Daisy_chain oder schön kurz [und mit A-B-C-D-E und A-B-C-D-E-A] auch hier: http://en.wikipedia.org/wiki/Daisy_chain_%28electrical_engineering%29#Network_topology ) bzw. Kaskadierung (wobei der Begriff eher in der Elektrik eingesetzt wird: http://de.wikipedia.org/wiki/Kaskadierung).

Also muss die Schirmung verbunden werden (ich würde die einfach eineinanderzwirbeln und haardünne KupferAdern drumwickeln und es verlöten).

Man könnte auf eine lineare Topologie setzen, also einen Strang oder 2 oder gar 3 parallele, und dann mit Cat7 beginnen und zum Ende hin (Richtung KunstHalle und KraftWerk Hastedt) dann mit Cat6 weitermachen und am Ende noch Cat 5 verbraten.

Oder eben eine ringförmige Topologie (wobei sich die Kabel nur wenige Meter entfernt voneinander im Baum befinden würden, oder gar als Paar verlegt werden würden) bei der es dann aber wahrscheinlich Sinn macht komlett dieselbe KabelQualität einzusetzen (hab jetzt keine Lust das weiter zu durchdenken).

Auf jeden Fall würde ich die WDRs auf die Seite der Bäume hängen wo sie zur Strasse blicken, so dass sie möglichst nicht nach unten senden und sich somit auch nicht soviele Clients von unten damit verbinden und die Nanos nicht durch die WDRs gestört werden (der Baum blockt das dann ja) und auf den WDRs Gluon laufen lassen.

Clients die sich auf der DeichSchräge aufhalten, können sich dann schon noch verbinden, aber eben nicht direkt zu dem WDR (aus ihrer perspektive hinter dem) Baum der am nächsten ist, sondern zu einem weiter links oder rechts.

Und mit den Nanos sollten sich die Clients die sich auf der DeichSchräge aufhalten möglichst nicht verbinden, da sie mit den Clients unten genug zu tuen haben.

Das kann man durch ein Blech verhindern. Dazu unten mehr.


Man hätte immernoch direkt 2 Ports frei für jew. eine meiner 30 Stück + x (x = Anzahl von 5 GHz Nanostations die wir noch zusätzlich [zB leihweise] bekommen könnten) NanoStation 5 loco (5GHz) und jew. an jedem 2. Baum (wären bei 15 Stück ca 500 E, gerne aber auch an jeden eine, dann 1000E)eine noch anzuschaffende Nanostation M2 loco (2.4 GHz)  oder könnte mit einem HaushaltsSwitch noch mehr NSs dranhängen.

Auf allen würde AirOS bleiben und sie wären als AccesPoint konfiguriert. Die einzelnen WDRs zählen die Clients dann trotzdem und man hat eine schöne Ansicht im MeshViewer und en Stats.

AUF JEDEN FALL würde ich in Erwägung ziehen (informieren, recherchieren, fragen) die Nanos horizontal aufzuhängen, auf die Weser zu zielen und sogar dann rechts und links daneben und ev. nach unten hin ein KuchenBlech-grosses Blech (zB von alten TowerPCs und HeizungsAnlagen, ich habe aber auch Blei und man kann auf SchrottPlätzen schauen) hinzubauen damit die quasi Scheuklappen haben und nur die Signale aus einem schmalen Slot empfangen für den sie zuständig sind.

Jede Gruppe aus WDR+Nano(s) braucht aber eben vor Ort in sagen wir mal weniger als 30m Entfernung vom EinsatzOrt eine 220V-SchukoSteckDose damit es nicht unwirtschaftlich wird bzw. überhaupt funktioniert.

Man könnte die Nanos auch immer so verteilen dass immer nur eine 2.4 GHz an einem Baum hängt und dann wieder eine 5 GHz nach X Metern, damit die sich nicht gegenseitig stören (obwohl es ja immerhin getrennte Bänder sind ist das ja möglich).

Der VerteilungsAbstand der WDRs sollte mMn rel. gleichmässig sein, aber an den Stellen wo unten viel los ist könnte man auch noch zusätzlich Richtfunk mit NanoBeams von Nebi und Emi oder noch zu kaufende einsetzen und unten dann an das Ende der RichtfunkStrecke WDRs hängen.

Oder man geht da mal doch mit einem Cat7 zu so einer Insel entlang von SS-Kabeln runter wenn das unter 100m sind und bindet so 1-2 HotSpotInseln (als nicht im Sinne von AccessPoints, sondern Orte wo MenschenMassen sein werden) an.


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
