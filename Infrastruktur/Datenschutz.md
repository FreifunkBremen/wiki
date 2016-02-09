# Datenschutz

Wie bei jedem Informationsverarbeitungssystem fallen auch in unserem Netzwerk und der dazugehörenden Infrastruktur Verbindungs- und Metadaten an.
Auf dieser Seite wird dargelegt welche Daten welchen Dienstes wie lange gespeichert wird.

## Datenerhebung

### "Bezugsart"

Daten lassen unterschiedlich genau auf Dinge beziehen. Viele der für den Betrieb des Netzwerks nötigen Daten lassen sich beispielsweise eindeutig auf das verwendete Endgerät beziehen, welches aber erst einmal keine Rückschlüsse auf die Person an diesem Gerät zulässt. E-Mailadressen und Geodaten hingegen lassen direkt mehr oder minder genaue Rückschlüsse auf die Person zu.

Wir versuchen den Grad der Sensibilität der Daten durch diese "Bezugsart" zu verdeutlichen.

### Als Nutzer des Freifunk-WLANs

| Daten                      | Bezugsart    | Gespeichert | Öffentlich | Speicherdauer | …im Backup |
|----------------------------|--------------|-------------|------------|---------------|------------|
| Datenverkehr               | Gerät/Person | ✘           | ✘¹         |               |            |
| Zuordnung Gerät↔IP-Adresse | Gerät        | ✔           | ✘¹         | 2 Stunden     | ✘          |
| Verbundener Knoten²        | Gerät        | ✘           | ✘¹         |               |            |

¹ Während die gespeicherten Daten nicht öffentlich einsehbar sind, muss diese Information (teilweise) zum technischen Betrieb des Netzwerks *innerhalb desselben* propagiert werden. Unsererseits wird diese Information nicht erhoben oder weitergeleitet, jedoch könnte ein Angreife die Information im Netzwerk selbst erheben.

² Wir weisen hier darauf hin, dass der Aufsteller eines Knotens dessen Koordinaten veröffentlich haben kann (s.u.) und somit inner halb des Freifunk-Netzes eine grobe Ortung möglich sein kann.

### Als Aufsteller eines Knotens

| Daten                      | Bezugsart    | Gespeichert | Öffentlich | Speicherdauer | …im Backup |
|----------------------------|--------------|-------------|------------|---------------|------------|
| Kontaktdaten (freiwillig)  | Person       | ✔           | ✔          | 7 Tage³       | ✘          |
| Koordinaten (freiwillig)   | Person       | ✔           | ✔          | 7 Tage³       | ✘          |
| Nutzungsstatistiken        | Knoten⁴      | ✔           | ✔          | unbegrenzt    | ✘          |

³ Diese Daten werden auf dem Knoten dauerhaft gespeichert und von diesem regelmäßig im Netz bekannt gegeben. Unsere Server halten die Daten (beispielsweise nach Abschalten des Knotens) noch für 30 Minuten vor, bevor sie vergessen werden.

⁴ Die Nutzungsstatistiken sind eindeutig dem Knoten zugeordnet. Falls also Kontaktdaten und/oder Koordinaten zum Knoten bekannt sind, sind diese Daten auf den Aufsteller des Knotens beziehbar, nicht jedoch auf einzelne Benutzer dieses Knotens.

### Sonstiges

| Daten                      | Bezugsart    | Gespeichert | Öffentlich | Speicherdauer | …im Backup |
|----------------------------|--------------|-------------|------------|---------------|------------|
| Webseitenbesuche           | keine⁵       | ✔           | ✘          | 1 Monat       | +3 Tage    |
| Mails an die Mailingliste  | Person       | ✔           | ✔⁶         | unbegrenzt    | +3 Tage    |
| Änderungsverlauf im Wiki   | keine⁵       | ✔           | ✔          | unbegrenzt    | unbegrenzt |

⁵ "keine" heißt hier, dass zur Speicherung von Informationen der Verweis auf eindeutige Identifikationsnummern (z.B. IP-Adressen, Session Daten) komplett bei der Erhebung oder kurze Zeit später entfernt oder stark verkürzt wird. Bei IPv4-Adressen bedeutet das konkret, dass sie durch Nullen ersetzt werden.

⁶ im [Archiv der Mailingliste](https://planetcyborg.de/mailman/private/ff-bremen/) (nur für Mitglieder zugänglich)

## Datenverarbeitung

Es findet keine automatisierte Verarbeitung der Daten, beispielsweise zum Zweck von Profilbildung, statt. Viele der knotenbezogenen Daten inkl. Nutzungsstatistiken werden in graphischer Form aufgearbeitet und ebenso wie die Rohdaten als [Karte](http://bremen.freifunk.net/map/geomap.html) oder in [Graphen](http://bremen.freifunk.net/map/node.html?id=c6:b6:a5:52:3a:9a) der Öffentlichkeit zur Verfügung gestellt.

## Schutz gegen unbefugte Zugriffe

Solange auf einem Freifunk-Router kein Passwort oder einen SSH-Key installiert ist, gibt es keine Möglichkeit, per Netzwerk an diesen Einstellungen zu ändern.

Über entsprechende Routing-Regeln ist das Freifunk-Netz vom privaten Netz getrennt.

Geräte im Bremer Freifunk-Netz sind per IPv4 aus allen Freifunk-Netzen (per Intercity-VPN), sowie per IPv6 im gesamten Internet erreichbar.
Es obliegt der Verantwortung jedes Nutzers, die Dienste auf seinen Endgeräten entsprechend zu sichern (etwa durch eine Firewall).
Freifunk ist nicht sicherer/unsicherer als das Internet.

## Einschränkungen und künstliche Limitierungen
Um die Verlangsamung des Gesamtnetzes zu verhindern blockieren die VPN-Server Filesharing-Diensten den Zugang ins Internet. Die Limitierung in Form von Durchsatz, Verfügbarkeit, Latenz sind ausschließlich durch Rahmenbedingungen des Netzwerkes, deren Ressourcen und der aktuellen Nutzung begrenzt.

## Server Standorte
Die gesamte Server-Infrastruktur befindet sich in deutschen Rechenzentren.
