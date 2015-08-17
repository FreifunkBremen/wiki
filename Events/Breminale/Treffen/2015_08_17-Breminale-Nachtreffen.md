# Breminale Nachtreffen Tagesordnung

## Rückblick
### Erfahrungswerte
* Aufbau/Abbau
* System/Netz
  * Kanäle
  * Switching
* Promotioneffekt
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

# Protokoll
### Erfahrungswerte
* Aufbau
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
* 

### Ausblick
* System/Netz
* 
* Tests
  * gleicher 5Ghz-Kanal (für Mesh)