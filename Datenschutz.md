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
| Kontaktdaten (freiwillig)  | Person       | ✔           | ✔          | 30 Minuten³   | ✘          |
| Koordinaten (freiwillig)   | Person       | ✔           | ✔          | 30 Minuten³   | ✘          |
| Nutzungsstatistiken        | Knoten⁴      | ✔           | ✔          | unbegrenzt    | ✘          |

³ Diese Daten werden auf dem Knoten dauerhaft gespeichert und von diesem regelmäßig im Netz bekannt gegeben. Unsere Server halten die Daten (beispielsweise nach Abschalten des Knotens) noch für 30 Minuten vor, bevor sie vergessen werden.

⁴ Die Nutzungsstatistiken sind eindeutig dem Knoten zugeordnet. Falls also Kontaktdaten und/oder Koordinaten zum Knoten bekannt sind, sind diese Daten auf den Aufsteller des Knotens beziehbar, nicht jedoch auf einzelne Benutzer dieses Knotens.

### Sonstiges

| Daten                      | Bezugsart    | Gespeichert | Öffentlich | Speicherdauer | …im Backup |
|----------------------------|--------------|-------------|------------|---------------|------------|
| Webseitenbesuche           | keine⁵       | ✔           | ✘          | 1 Monat       | +3 Tage    |
| Mails an die Mailingliste  | Person       | ✔           | ✔⁶         | 1 Monat       | +3 Tage    |
| Änderungsverlauf im Wiki   | keine⁵       | ✔           | ✔          | unbegrenzt    | unbegrenzt |

⁵ "keine" heißt hier, dass zur Speicherung von Informationen der Verweis auf eindeutige Identifikationsnummern (z.B. IP-Adressen, Session Daten) komplett bei der Erhebung oder kurze Zeit später entfernt oder stark verkürzt wird. Bei IPv4-Adressen bedeutet das konkret, dass die letzten beiden Bytes mit Nullen ersetzt werden.

⁶ im [Archiv der Mailingliste](https://planetcyborg.de/mailman/private/ff-bremen/) (nur für Mitglieder zugänglich)

## Einschränkungen und künstliche Limitierungen
Um die Verlangsamung des Gesamtnetzes zu verhindern blockieren die VPN-Server Filesharing-Diensten den Zugang ins Internet. Die Limitierung in Form von Durchsatz, Verfügbarkeit, Latenz sind ausschließlich durch Rahmenbedingungen des Netzwerkes, deren Ressourcen und der aktuellen Nutzung begrenzt.

## Server Standorte
Die gesamte Server-Infrastruktur befindet sich in deutschen Rechenzentren.
