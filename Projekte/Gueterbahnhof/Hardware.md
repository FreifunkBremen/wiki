
## Übersicht verbauter Hardware: 

* 6x TP-Link Archer C7
* 4x TP-Link CPE210 ('hof', 'garten', bei tor11 und 'spedition')
* 2x Ubiquiti Nanobeam AC 19 (Richtung Schlachthof und Radstation)
* 4x TP-Link WR1043
* 1x TP-Link WR940
* 1x TP-Link WR841 (temporär, zum Debuggen)
* einiges an Kabel, teils Patch-Kabel, teils selbst aufgelegt/gecrimpt


## aktuelle Standorte

### Dach (süd)
Auf dem Dach hat Nico einen schicken Mast installiert, daran befestigt sind aktuell 2 CPE210 und die Ubiquiti-Nanobeam zum Internet-Zugangspunkt beim Schlachthof ("Uplink"). 

### Dach (nord)
Auf dem nördlichen Dach hat Nico einen schicken Mast angebracht, daran befestigt ist aktuell eine Ubiquiti-Nanobeam zur Radstation.

### 2.OG 
Im 2.OG sind aktuell 2 Archer C7 im Einsatz, einer regelt hauptsächlich den Verkehr (Mesht mit allem), der Andere hängt neben dem Aufenthaltsraum/Küche.

### 1.OG
im 1.OG steht ein WR1043 auf einem Podest auf dem Flur. An diesem Router soll demnächst ein gatemon (kleiner Raspberry-PI, der schaut, ob das Netz in Ordnung ist, hilft bei der Fehlersuche sehr, Link:https://github.com/FreifunkBremen/gatemon) betrieben werden.

### "lange Hallen"
Auf den beiden Hallen steht jeweils 1 CPE210 auf dem Dach auf einem Betonsockel (extra dafür von den Jungs vor Ort gegossen!). 
Per 10m-Kabel ist jeweils ein Archer C7 angeschlossen, der das WLAN als Client-Netz verteillt. 
Die Standorte sind: Bei der "Spedition" und ca. gegenüber bei Tor11.

### Keller
Im Keller hängt bei den Bandräumen ein Archer C7, das WLAN wurde abgeschaltet, auf den gelben Ports kommt Client-Netz (also Internet) raus. 
Das orangene Kabel liefert das Mesh-Netz, muss daher immer im blauen Port eingesteckt sein. 
Damit genug Ports zur Versorgung der Proberäume zur Verfügung stehen, hängt am Archer aktuell ein 5-Port USB-Switch. 

### Ateliers zwischen Künstlerhaus und längerer Halle
An der beschriebenen Stelle hängt ein WR1043 "auf dem Gang". Er hängt per Mesh an einem Archer C7 im 2.OG.

### Tor 25
Bei Tor25 ist nun auch ein Router (1043er) gelandet. 

### Tor40
Bei Tor40 wurde im Januar ein Router (1043er) verbaut, er hängt per Outdoor-Kabel via Zwischendecke direkt am agffgb03 (aka Zentrale)

### Linie7
Bei Linie7 ist ein Archer-C7 im Einsatz, der hängt per Outdoor-Kabel am Tor40-Router.
Der Name: agffgb10

### Offene Ateliers
zwischen Linie7 und Schaulust sind Ateliers, da steht ein WR940-Router.

### Schaulust
Archer C7 ist von Linie7 her angebunden. Anbindung zur Spedition folgt demnächst.

## nächste Standorte

### Veranstaltungsraum zwischen Schaulust und Spedition
Hier kommt demnächst der WR940 rein, der verbindet dann agffgb12 und 'Spedition'.

### erstmal verschoben: Ende der Gleishalle / Querlenker
Am Ende der Gleishalle kommt vielleicht noch einie Installation hin, um die Obdachlosen hinter dem GB zu versorgen. 
Die Querlenker wären dann Nutznießer. Sinnvolle Installation ist vmtl eine CPE für Richtfunk und eine AC-Mesh mit Antenne zur Versordung der Clients (wie ehemals CafeSand)
