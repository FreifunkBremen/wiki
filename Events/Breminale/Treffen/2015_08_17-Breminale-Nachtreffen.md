# Breminale Nachtreffen Tagesordnung

## Rückblick
### Erfahrungswerte
* Aufbau/Abbau
* System/Netz
  * Kanäle
  * Switching
* Promotion
* Fianzen

## Ausblick
### Fragen
* nochmal machen?
  * warum?

### Vorgehensweise
* System/Netz
* Organisation
  * Aufbau/Abbau
* Stand
* Promotion
* Finanzen

# Protokoll
## Rückblick
### Erfahrungswerte
* Aufbau/Abbau
  * nächstes Jahr anders
  * weg von den Kästen
  * Arbeitsaufteilung
      * nicht idlend am Stand rumpimmeln
      * entweder Arbeit oder auf der Breminale
      * Dudle für Bedarfe
      * was ist zu tun?
          * Engelsystem (CCC)
          * Aufgaben Post-its?
      * Kommunikation
          * Funkgeräte vom CCC leihen?
          * Threema Gruppe? (irgendwas mit Push was gut funtioniert)
  * Nodes
      * welcher war fertig? (= welcher macht das Netz nicht kaputt)
      * nicht in die Buden (Aufwand, schwierigere Wartung/Installation, Haftung)
      * Regenschirme haben gefehlt
      * Kabel waren durch fehlende Beschriftung nicht identifzierbar
  * Inventur vor Ort: https://planetcyborg.de/pads/p/freifunk-bremen-breminale2015-abbau
* Stand
  * nicht mehr 3 Meter Bretter (viele Gründe)
* System/Netz
  * Kanäle
      * 2,4Ghz voll (obwohl 0db), 5Ghz ging
      * Modus auf Amerika damit DFS und TPC weg
      * 200 Milliwatt
  * Switching
      * Hardwareswitch wurde verwendet, gute Performance, viele Unanehmlichkeiten
      * Ring nur nachdem Spanning-Tree an war
      * neue Clients haben lange gebraucht sich beim Monitoring zu melden
      * SSID wurde trotz fehlender Verbindung ausgestraht (später gepatched)
      * Ansible hat Daten nicht aus dem Monitoring genommen (später gepatched)
      * radvd und DHCP auf Edge-Router war doof (Lease wurden über die Breminale erhalten (bis Montag))
      * Management-VPN auf dem Edge-Router war doof
      * Switch und Router haben sich nicht gut Verhalten bei Stromausfall
      * Datenschutz: Adresen, Hersteler und Gerätenamen im Edge-Dump
* Promotion
  * Leute dachten...
      * WLAN nur am Stand
      * Leute wissen nicht was Freifunk ist
  * zu wenig Promotioneffekt für ein Promotionprojekt
      * QR-Code wurde wenig gescanned
      * Website fühlt sich großteilig überflüssig an
* Finanzierung
  * sehr gut!
  * Finanzierung generell einmalig

### Ausblick
### Fragen
* nochmal?
  * 7 ja, 1 enthalten
  * warum?
      * neutral: Promotioneffekt erfüllt, Freifunk kein Dienstleister
      * Promotion, Guerilla macht Spaß
      * Klassenfahrt-mäßig
      * Spaß
      * Promotioneffekt NICHT erfüllt; aufpassen, dass Freifunk nicht AUSSIEHT wir Dienstleister
      * Breminale ist free und die Veranstalter sind auch so drauf; weil wir Bock drauf haben
      * VIP-Pässe

### Vorgehensweise
* Aufbau/Abbau
  * Ablauf
      * nicht eine Woche früher anfangen, zu viele Dependencies
      * alles Material von Anfang an da
  * Arbeitsaufteilung
      * klarere Aufgaben für Zeitpunkte
      * arbeiten oder weggehen
      * es muss klar sein (dokumentiert werden) was zu tun ist
      * unabhängig von Buden und Elektrikern
      * mehr Training, damit jeder alles kann
      * Teams
  * Kommunikation
      * Funkgeräte
      * Rollen für Aufgaben/Leute (Funkgeräte)
      * Karte/Live-Tracking erübrigt sich durch Funkgeräte
  * Nodes
      * Position
          * am Deich Outdoorboxen an die Stromkästen
          * möglichst auf Brusthöhe, nicht höher als Kopf
      * Beschriftung
          * MAC-Adresse
          * Barcodes
      * Vorbereitung
          * Firmware vorher fertig
          * Firmware vorher testen
          * Firmware vorher geflashed
          * sichern und beschriften
      * REGENSCHIRME!
  * Stand
      * LAGER!
          * Zahlenschloss? = für alle zugänglich
      * wie genau, später
      * Stand wahrscheinlich wieder möglich am Fahnenmast
      * Bauwagen vielleicht von Walter
      * NOC und Stand seperiert
* System/Netz
  * Uplink
      * als Verein möglich in IPv4-Netz zu bekommen mit 65 Tausend Adressen
      * an Max Vorraussetzung für Uplink-Provider geben, damit vernünftiges Angebot
          * LWLcom würde sponsern
  * Kanäle
      * 2,4Ghz 0db
      * EINE SSID
          * aus Prinzip
          * Nutzen im Rest der Stadt
          * Verwirrung sonst
      * da wo 2,4Ghz überlastet ist und nicht geht, einfach aus
  * Kanal-Monitoring
      * extra Nodes (Probenodes), die die Verbindung testen (Kür)
  * Switching
      * Batman
      * fast Standardfirmware
      * mehr Redundanzen
          * Richtfunk vom Uplink zum Stand?
          * LWL-Kabel von Fähre bis Fahnenmast entlang der Lichterkette
* Promotion
  * Flyer (vielleicht nochmal generell überarbeitet)
  * Banner an jeden Stromkasten? (oder großer Sticker oder "gekleisterte" Plakate)
  * mehr Freifunk erklären **---WIE??---**
      * klar zeigen wie Freifunk in Bremen bereits ausgebaut ist
      * Läufer?
* Verpflegung ist erwünscht
  * Max fragen
      * frei bei Ständen
      * Zelt-Backstage?
  * selbst organisiert?
* überschüssiges Geld
  * erstmal bekommen
  * abrechnen
  * dann nochmal checken
* Tests
  * gleicher 5Ghz-Kanal (für Mesh)
* Services
  * Heatmap an Nutzern