# Treffen 09.09.2016 - Arbeitstreffen Website

**Termin:** Freitag, 09.09.2016, 19:30 Uhr 

**Ort:** Hackerspace Bremen e.V. ([Anfahrt](https://www.hackerspace-bremen.de/anfahrt/))

## Tagesordnung
### Status Quo
- unsere Website
    - fühlt sich an
    - sieht aus
- andere Websites
    - http://www.wlan-walle.de/
    - https://freifunk-rhein-neckar.de/
    - https://simjost.github.io/neue-Freifunk-Website/
    - https://regensburg.freifunk.net/
    - https://weimarnetz.de/

### wo wollen wir hin?
- was soll die Website
    - machen
    - können
    - vermitteln
- wie soll die Website das erreichen
    - visuell
        - parallax backgrounds https://codyhouse.co/demo/alternate-fixed-scroll-background/index.html
    - inhaltlich
    - Umfang
- simpleres Interface für Firmware-Download
    - https://forum.freifunk.net/t/freifunk-hennef-firmware-downloader/12966

### Plan für das Erreichen der Ziele
- technisch
- personell
- zeitlich

### Treffen abschließen
* Aufräumen!
  * Müll weg
  * Kabel zurück
* Info zu Treffen aktualisieren
  * Protokoll aus Pad ins Wiki kopieren
  * [Treffen auf Wiki-Homepage anpassen](Home)
  * Topic im IRC anpassen


## Protokoll

### Anwesende
- SimJoSt - Protokollant
- Frank
- Jan-Philipp
- Oliver - Protokollant
- Timlukas
- Yannik

### Status Quo
#### Design
- gut
    - Logos
    - Was ist Freifunk?
    - Navigation
- schlecht
    - Platz zwischen Logos verschenkt
    - vier Blöcke unter "Was ist Freifunk" unübersichtlich, wie freifunk.net
    - Mobil zu viel Platz Seiten
    - Mitmachen Aufruf fehlt
    - ohne Farb-Hntergründe keine gute Übersicht
    - Kontakt-Übersicht nicht gut
    - Lesbarkeit weil zu lange oder zu kurze Zeilen
    - Links/Buttons im Fließtext
    - Navigation zu klein im Verhältnis
    - (kein Dropdown)
- Gutes von anderen Seiten
    - Uni Bremen  
      Navigation für unterschiedliche Personen/Perspektiven/Interessen

#### Inhalte
- schlecht
    - veraltet
    - nicht vollständig
    - nicht zu finden
- fehlen
    - Verein
    - Kalender

### wo wollen wir hin?
- Website einfacher bearbeiten
    - Vorschlag eigenes Gitlab; Bearbeiten-Button führt zu anonymen pull request Funktion (Machbarkeit prüfen)
- Website soll unterschiedliche Inhalte für unterschiedliche Personen darstellen

### Plan
#### Navigation
- Startseite
    - Was ist Freifunk?
    - Hilfe / Kontakt (+Kontaktformular) / Treffen
    - Karte
    - Projekte (Walle, Geflüchtete, Events/Breminale, Referenzen)
    - News / Twitter
    - Sponsoren / Partner
    - Kalender
- Einsteiger
    - Anleitungen
    - Firmware
    - Referenzen (Erfahrungsberichte)
    - Hardware / Abholstandorte
    - FAQ
    - Dienste
- Engagierte
    - Mailingliste
    - Firmware
    - Wiki
    - Technik
    - Informaterial
    - Verein / Organisation / Struktur
- Unterstützer
    - Spenden / Sponsoren / Partner werden
        - Server stellen, Router verkaufen, Infos verbreiten, Dachflächen
    - Infomaterial
- Footer
    - Impressum
    - Kontakt
    - Lizenz
    - Edit this page

#### Umsetzung
*vieles Technisches bleibt leider an jplitza hängen*
- jplitza macht grobes Redesign
    - Homepage in HTML, CSS und JavaScript schreiben
    - in Template für Jekyll kippen
- Inhalte werden von beliebigen Leuten bereits vorbereitet und im Website Repo hinterlegt
- Entscheidung: keine Inhalte von externen Servern einbinden (Twitter/Kalender wird serverseitig aufbereitet, auch JQuery/Fonts müssen von *bremen.freifunk.net kommen)

#### Nice To Have
Das hier sind Sachen, die nicht unbedingt wichtig sind für die Seite, aber trotzdem schön wären:

* Hintergrund des Links zur Karte auf der Startseite
* Hinweis, wenn der Besucher gerade im Freifunk-Netz ist
* dynamische Services-Seite mit Online/Offline-Status und Sortierung
* Bilder in Blogpost schön einbinden
* Twitter-Cards (für den Blog)

#### Design-Notizen
* generell an https://regensburg.freifunk.net/ orientieren (Danke fuer das Kompliment. Gruss aus Regensburg)
* "Sticky Header" - Nav-Leiste soll immer oben zu sehen sein (in verkleinerter Form)
* Idee: Knoten-Karte auf Startseite, in schlanker Form: statt Meshviewer einen Screenshot vom Meshviewer (evtl. als SVG)
** Kartenbild ist dann ein Link auf den Meshviewer
    * Kartenbild müsste nur selten aktualisiert werden (wöchentlich oder so), weil es nur repräsentativ sein soll (keine exakte Knotenkarte)
* Nav-Leiste besteht aus einem Menü
    * auf Desktop: Hover über Menüitem klappt das Menü auf
    * auf Mobile: Antippen klappt das Menü auf
* mobile Seite:
    * Menü wie bei Regensburg
    * Kür: zur Seite wischen, um das Menü einzublenden
* gute Typografie (s. practicaltypography.com)
* wär hilfreich: im Menü den Eintrag für die aktuelle Seite highlighten
* Vorschlag für alternatives Menü:
    * zweizeilig
    * erste Zeile enthält "für Interessierte, für Einsteiger, für Eingagierte, für Unterstützer"; beim Hovern wird die Zeile darunter umgeschaltet
    * zweite Zeile ist dynamisch, enthält die Unterpunkte
    * jeder Ober-Menüpunkt hat eine eigene Farbe
    * Untermenü wird entsprechend umgefärbt
    * beim Runterscrollen bleibt nur die untere Zeile stehen, sobald das Menü aus der Seite rausscrollen würde
    * wenn man ein bißchen hochscrollt, wird auch die obere Menüzeile wieder eingeblendet
    * beim Runterscrollen wird ein kleines Freifunk-Logo vor der Menüleiste eingeblendet
* nebenbei: Blogpost besser stylen
    * Bilder schöner einbinden
    * z.B. Bilder flächig als Hintergrund, oder flächig hinter der Überschrift
    * siehe z.B. https://jplitza.de/blog/2016/01/07/Teufelsberg.html, wo Bilder tw. an der Seite dargestellt werden
