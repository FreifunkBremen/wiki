## Termine

### [Breminale](http://www.breminale-festival.de/)
* Breminale-Beginn: Mi, 25.7., nachmittags
* Breminale-Ende: So, 29.7., nachts

### Aufbau / Abbau

## Kommunikation
* Anwesenheit: https://dudle.hackerspace-bremen.de/FFHB_auf_Breminale_2018/
* IRC: [#ffhb_events im Hackint](irc://irc.hackint.org/ffhb_events)
* Hackmd: https://hackmd.io/HPeyrnwxQD2Ny9fUaZoiKQ?both#

## TODO
Fördermittel einplanen.

Ideen und Wünsche sammeln.

- Router für Outdoorboxen
  - 10 Boxen sind vorhanden, mit Platz für insgesamt mindestens 20 Router in WDR-Größe
  - 5 GHz (oder Dualband)

- Outdoorboxen kaufen
  - Vergleich verschiedener Modelle: https://hackmd.io/b-IJDqOGRCSv_q9MIeq2fw

### Treffen 29.06.
Protokoll steht unter [[Treffen/2018_06_29-Breminale]].

## Während der Breminale

(übertragen aus dem HackMD)

## Status
### aktuelle Probleme
Beispielsweise kaputte Router, fehlende Netz-Konfiguration, fehlendes Material  
(dringende Probleme ruhig in **fett**):
- **Netz-Probleme**
    - Symptome
        - Knoten reden nicht mehr mit Nachbarn
        - stürzen nicht ab, laufen weiter
    - mögliche Ursachen
        - "komische" `mpcp`-Pakete (STP?)
        - evlt. Spannungsveränderungen wenn Bandsspielen
          *(`b.a.t.m.a.n. Probleme dadurch?`)*angeschlossen
    - mögliche Quellen
        - die letzten drei Boxen vor Tunnel
        - zweiter S16 Switch dachte an allen 4 Ports wäre etwas
            - Sicher? Die linken LEDs zeigen nur den PoE-Status, und da müssen vier leuchten, weil auf vier Ports passives PoE an ist.
- 100 Mbit-Verbindung zwischen zwei Knoten
    - was waren das an beiden Enden für Boxenkonfigurationen?


- `fd2f`-Adressen teilweise nicht aufrufbar
    - Ist zu erwarten, wir routen die auch nicht weiter. Die geistern im Breminale-Netz auch nur rum, weil manche Knoten die wohl einkompiliert haben.
- Freifunk-Knoten aus dem Bremer Netz über IPv6-Adressen teilweise nicht aufrufbar
- Freifunk-Manager
    - hängt wenn Bearbeitung und yanic-Live-Daten gleichzeitig
    - Workaround: yanic Daten werden nur sporadisch manuell eingespielt


### aktuelle Aufgaben:
- [breminale.json](https://github.com/FreifunkBremen/internal-maps/blob/master/breminale.geojson) über [geojson.io](http://geojson.io/#id=github:FreifunkBremen/internal-maps/blob/master/breminale.geojson&map=16/53.0698/8.8171) aktualisieren (Oliver)
    - [x] Zelt-Positionen eintragen (z.B. vom Lageplan.pdf in der Cloud)
    - [x] Stromkästen+Bezeichnungen am Deich ansehen und eintragen
    - [ ] Stromkasten-Bezeichnungen von breminale.geojson auf Papíer-Plan übertragen
- ~~Mesh AC flashen (Anleitung: https://hackmd.io/SINSRav6R5m5TATQc7UZ8g)~~

### Netz-Plan
[breminale.json](https://github.com/FreifunkBremen/internal-maps/blob/master/breminale.geojson) über [geojson.io](http://geojson.io/#id=github:FreifunkBremen/internal-maps/blob/master/breminale.geojson&map=16/53.0698/8.8171)

Start          | Kabelart & Länge   | Ende
-------------- | ---------- | ----
LWLcom-Uplink  | LWL        | Orga-Container
Orga-Container | Kupfer 20m | Bauwagen
Bauwagen       | Kupfer 50m | Stromkasten vor Deichgraf
Bauwagen       | Kupfer 50m | Stromkasten zwischen Deichgraf und Flut
Bauwagen       | LWL 200m   | Bremen 1
Bremen 1       | 2x LWL 100m, *1x 50m unnütz*, 1x 50m | Wohnzimmer
Wohnzimmer     | LWL 300    | Himmlische Wiese

#### Weitere Planung der OBO-Verkabelung (ollibaba)
Das haben Gesche und Oliver sich am So. ausgedacht, um Mesh ACs und OBOs zu verteilen:
- zwischen Fähre und Flut:
    - (1 OBO steht schon am Stromkasten (B43?))
    - 1 OBO in den Backstage-Bereich von Flut beim Sechseck-Zelt

- zwischen Flut und Bre4-Zelt:
    - S16-Switch am Stromkasten
    - 4x Mesh AC an die Masten in der Nähe vom Stromkasten
    - PoE-Injektor für S16-Switch bei 273
    - 1x 50m LAN von 273 zu A204

- zwischen Bre4-Zelt und Bre1-Zelt:
    - OBO auf Materialcontainer im Backstage von Bre4
    - 2x Mesh AC am Mast bei Z3
        - Hinweis: an Z3 ist kein Strom
    - 2x 50m LAN (parallel) von B80 zu Z3 (Wasserseite)
    - an A208 (neben Burgerhaus) 1 OBO unterm Stromkasten
        - falls möglich: OBO lieber ins Zelt stellen
    - 1x LAN von 173 zu A208

- zwischen Bre1 und BreNext:
    - 2x Mesh AC am Zaun von Bre1-Backstage (per PoE-LAN von 252)

- BreNext-Bühne:
    - 1x 50m LAN von 252 zu A210
        - vorher messen/schätzen, ob das lang genug ist!

- zwichen BreNext und Wohnzimmer (also im Biodorf-Bereich):
    - 2x Mesh AC (in der Nähe von 32)
    - evtl. zusätzlich 2x Mesh AC (von FrankT und Ollibaba) ebenfalls in der Nähe von 32
    - S16-Switch bei 32
    - PoE-Injektor (für S16-Switch) bei 193
    - 1x 50m LAN von 193 zu 32

## Fehler/Learnings
- Lange LWL-Kabel an falsch herum eingesetzt
    - 300m lieber über Breminale-Gelände
    - 200m lieber rüber zur Himmlischen Wiese
    - Nachtrag: das sollten wir nochmal überdenken; von dem 300m-Kabel war auf der HiWie weniger als 100m übrig
- Kabel von Bauwagen runter vorher planen
    - richtigen Längen bis zum Stromkasten
    - entsprechend der verfügbaren Geräte
    - Dickere Wasserleitung als Durchführung, gern auch ein 2.5m Stück statt 3x1m
- ab Aufbau (besonders zu Beginn) jemand am Pad/Orga-Überblick
- Kabel eher an Stromleitungen als an Wasserleitungen, weil die manchmal ausgetauscht werden müssen (kaputt gefahren)
- 20cm Kabelbinder sind zu Kurz für die Stromleitungen (30cm wäre entspannt, 25cm reicht vermutlich)
- Die dünnen 50m-Kabel (mit rotem Clip) taugen nichts für (passives=AC Mesh) PoE. Die mit blauem Clip gehen.
- (kein (großes) Clientnetz an einen OpenWRT-Switch Interface -> MAC Table wird sehr voll?)
- Boxen von allen Seiten (sehr groß!) beschriften
- 40MHz-Channel machen Probleme (genauer Liste mit Channelbreite zusammenstellen)
- Backbone aus Glasfaser, ohne FF-Router als Bestandteil des Backbone
    - idealerweise 1x LWL passiv durchgeschaltet, und 1x LWL über Switches geführt (wo dann Knoten drankönnen)
    - LWL sorgt für Potentialtrennung
    - Ringe und Ersatzstrecken (Richtfunk) sind gut, um den Rest des Netzes angebunden zu halten, selbst wenn irgendwo was ausfällt
- von vornherein Probleme mit Strom vermeiden, falls z.B. Schwankungen im Netz durch Bühnenequipment zu erwarten sind:
    - nicht mehrere Knoten per Kabelpeitsche an einem Netzteil betreiben; die Kabelpeitsche kann die Stromversorgung evtl. verschlechtern, und dann bekommt man mysteriöse Probleme
    - PoE-Injektoren nicht mit langem Kupferkabel anschließen, weil man dann evtl. Potentialprobleme zwischen Switch und Injektor bekommt -> [mysteriöse](https://www.youtube.com/watch?v=jTBzYwiF4FE) Probleme
- groben Netz-Aufbau (Backbone, Ersatzstrecken) planen, bevor erste Kabel gelegt werden
- Flipchart ist eine gute Sache, ToDo Liste auch.
- Großer Plan ist eine sehr gute Sache
- Kabel, GF, Boxen einzeichnen auch.
- Vorschlag: Bühnentechniker befragen, wie die ihre Bühnenelektronik vor den Stromproblemen schützen (vermutlich einfach, indem Sie teure Hardware nutzen, die das von sich aus kann.)
    - Hinweise von einem Techniker (von ollibaba befragt): sternförmige Strom-Verkabelung (damit alle Geräte das gleiche Potential haben) bzw. LWL als Datenleitung zwischen verschiedenen Strom"sternen"; Power Conditioner oder kleine USVs für die Geräte (um Spannungsabfälle aufzufangen)
- Idee: Glühlampe (LED-Lampe) mit Stecker zum Steckdosen Testen und als Arbeitsleuchte an Stromkästen. z.b Brennenstuhl Kabellampe ca.10 Euronen.

## Notizen von ollibaba
- Kabel K0032 und (vllt.) K0054 prüfen (da kommt evtl. kein guter Link zustande)

## Fundsachen
### Ollibaba hat gefunden
* weiße Tragetasche
* schwarze Tragetasche mit pinkem Aufdruck
* schwarzer Hoodie
* WLAN-Walle-T-Shirt
* runde Frühstücksdose (Benni?)
* ~~2 Paar Arbeitshandschuhe (1xYannik! 1xFrankT)~~
* Sonnenbrille (Jack+Jones, schwarzes Plastik)
* ~~1 USB-Seriell-Wandler (Jan-Eric)~~
* 1 USB-Seriell-Wandler (Julian?)
* ~~kleines Breadboard mit Kabeln (Louis? Jau!)~~
* Tütchen mit Schrauben/Schlauchschellen/Draht... (FrankH?)

* einige FFHB-Sachen
    * ~~2 grüne Seitenschneider~~
    * 1 Stromkabel (keine Inventarnummer, aber FFHB-Aufkleber; wurde von den Wasserleuten gefunden)

### Yannik hat gefunden 
* ~~Eiswürfel-Schale (18 Eiswürfel, Form : Diamant) (ollibaba)~~

### Ollibaba vermisst
* ~~silber-farbenes Cuttermesser (Frank_H)~~
* Gaffa-Tape, ist innen mit "OG" beschriftet
* 1-2 Eddings, sind evtl. mit "OG" beschriftet
* graues 2m-Patchkabel, müsste mit meinem Namen beschriftet sein
* Klebeband-Abroller (mit mattem Scotch-Tape)

### Frank_H
Fehlende Inventarnummer:
* B0041-01_(N00xx) Node-ID: e894f6f30019 = N0018?
* B0041-02_(N00xx) Node-ID: e8de2758ebe4 = N0019?
* LAN Kabel K0053 Schrott = deinventarisieren.
