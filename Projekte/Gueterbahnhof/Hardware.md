## Übersicht verbauter Hardware: 

* 6x (+ X) TP-Link Archer C7
* 4x TP-Link CPE210 ('hof', 'garten', bei tor11 und 'spedition')
* 2x Ubiquiti Nanobeam AC 19 (Richtung Schlachthof und Radstation)
* 5x TP-Link WR1043
* 1x TP-Link WR940
* 1x TP-Link WR841 (temporär, zum Debuggen)
* einiges an Kabel, teils Patch-Kabel, teils selbst aufgelegt/gecrimpt


## aktuelle Standorte

### Künstlerhaus

#### Dach (süd)
Auf dem Dach hat Nico einen schicken Mast installiert, daran befestigt sind aktuell 2 CPE210 und die Ubiquiti-Nanobeam zum Internet-Zugangspunkt beim Schlachthof ("Uplink"). 
Nächster Meshender Router im Künstlerhaus: GB-KH-E3-1a

#### Dach (nord)
Auf dem nördlichen Dach hat Nico einen schicken Mast angebracht, daran befestigt ist aktuell eine Ubiquiti-Nanobeam zur Radstation.
Nächster Meshender Router im Künstlerhaus: GB-KH-E3-2

#### 2.OG 
Im 2.OG sind aktuell 2 Archer C7 im Einsatz, einer regelt hauptsächlich den Verkehr (Mesht mit allem), der Andere hängt neben dem Aufenthaltsraum/Küche.

#### 1.OG
im 1.OG steht ein WR1043 auf einem Podest auf dem Flur. An diesem Router soll demnächst ein gatemon (kleiner Raspberry-PI, der schaut, ob das Netz in Ordnung ist, hilft bei der Fehlersuche sehr, Link:https://github.com/FreifunkBremen/gatemon) betrieben werden.

#### Keller
Im Keller hängt bei den Bandräumen ein Archer C7, das WLAN wurde abgeschaltet, auf den gelben Ports kommt Client-Netz (also Internet) raus. 
Das orangene Kabel liefert das Mesh-Netz, muss daher immer im blauen Port eingesteckt sein. 
Damit genug Ports zur Versorgung der Proberäume zur Verfügung stehen, hängt an dem Archer C7 aktuell ein 5-Port USB-Switch. 

### Lange Hallen

#### Rechte Seite 

##### Ateliers zwischen Künstlerhaus und längerer Halle
An der beschriebenen Stelle hängt ein WR1043 "auf dem Gang". Er hängt per Mesh an einem Archer C7 (Name:GB-KH-E3-2) im 2.OG und mesht wiederum mit Router GB-KH-E1-2

##### Tor 25 bis Tor 1
Bis Tor 1 sind nun Kabel und Router verlegt. 

* Tor 25 (GB-RT-1) ist ein Router (1043er) gelandet.  (kontakt: a.b. / tor 26?)
* Tor XX  (GB-RT-2) ist ein Router. (kontakt: shakespeare)
* Tor 13/14 (GB-RT-3) ist ein Router. (kontakt: k.s.)
* Tor 11 (GB-RT-4) ist ein Router, hier war auch die vorherige Mesh Installation auf dem Dach. (kontakt: m.l.r. / j.m.)
* Tor 9 (GB-RT-5) ist ein Archer C7. (kontakt: t.l.)
* Tor 7 (GB-RT-6) ist ein Archer C7. (kontakt: r.w.)
* Tor 5 (GB-RT-7) ist ein Archer C7. (kontakt: j.t.)
* Tor 4 (GB-RT-8) ist ein Archer C7. (kontakt: j.ö.)
* Tor 1 (GB-RT-9) ist ein Archer C7. (kontakt: t.s.)

Die Tore hier haben dünnere Wände und viele Lagerorte. Die Abstände der Router variert hier regelmäßig und muss vielleicht je nach Nutzung und Entwicklung nachverdichtet werden. Die Netzwerkabel können dort alle bequem auf einer vorhandne Kabeltrasse geführt werden.
Ein häufiges Problem sind die Zugänge zum Strom. Viele Hallen Nutzer*innen schalten ihren Hauptschalter bei Abwesenheit aus. Hier sind mit Uwe (vom GB) spezielle Lösungen entwickelt worden oder auf PoE Geräte umgeschwenkt worden. Bei Freifunk Ausfällen auf dieser Seite ist fehlender Strom immer in Betracht zu ziehen.


#### Linke Seite

##### Tor40
Bei Tor40 wurde im Januar ein Router (1043er) verbaut, er hängt per Outdoor-Kabel via Zwischendecke direkt am agffgb03 (aka Zentrale)

##### Linie7
Bei Linie7 ist ein Archer-C7 im Einsatz, der hängt per Outdoor-Kabel am Tor40-Router.
Der Name: agffgb10

##### Offene Ateliers
zwischen Linie7 und Schaulust sind Ateliers, da steht ein WR940-Router.
Da hier die Wände im Gegensatz zur den Toren auf der anderen Seite wesentlich robuster sind. Wurde zur Nachverdichtung ein weitere Router (Archer C7) in den dichten Ateliers zwischen Linie 7 und Schauluft angebracht. Momentan noch per WIFI Mesh, so lange bis eine Kabelinstallation möglich ist. 

##### Schaulust
Archer C7 ist von Linie7 her angebunden. Anbindung zur Spedition folgt demnächst.

##### Veranstaltungsraum zwischen Schaulust und Spedition
Hier hängt nun ein WR1043 in einer Ecke. Dies war der Ringschluss-Router in diesem Gebäudeteil.

## Sonstiges 

### Container-Kiosk
Auf dem Gelände Eingang steht ein zum Kiosk und Parkwächterhäusche ausgebauter Container. Dieser ist zwar im LT Schema benannt, weil er sich auf dieser Seite befinden, aber defacto über einen bestehenden Wasser- und Stromkabelkanal mit an die RT Reihe angeschlossen. 

### austehend: Ringschluss
Wegen der häufigen Stromprobleme wollen wir dauerhaft einen Ringschluss zwischen Spedition und der rechten Hallenseite vollziehen

### erstmal verschoben: Ende der Gleishalle / Querlenker
Am Ende der Gleishalle kommt vielleicht noch einie Installation hin, um die Obdachlosen hinter dem GB zu versorgen. 
Die Querlenker wären dann Nutznießer. Sinnvolle Installation ist vmtl eine CPE für Richtfunk und eine AC-Mesh mit Antenne zur Versordung der Clients (wie ehemals CafeSand)
