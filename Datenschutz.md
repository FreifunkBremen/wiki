Wie bei jedem Informationsverarbeitungssystem fallen auch in unserem Netzwerk und der dazugehörenden Infrastruktur Verbindungs- und Metadaten an.
Auf dieser Seite wird dargelegt welche Daten welchen Dienstes wie lange gespeichert wird.

## Datenerhebung und Verarbeitung

| Typ           | Anonymisiert | Speicherzeit auf Server | Speicherzeit im Backup |
|---------------|--------------|-------------------------|------------------------|
| Webserver     | ja           | 1 Monat                 | Serverzeit + 3 Tage    |
| Traffic       | TODO         | TODO                    | -    |
| Mailingliste                    | nein         | 1 Monat                       | Serverzeit + 3 Tage    |
| E-Mail-Server | ja         | 1 Monat                 | Serverzeit + 8 Tage    |
| Wiki Historie | TODO | TODO | - |
| DHCP-Leases | TODO | TODO | TODO |
| MAC und IP-Adressen für BATMAN | TODO  | TODO | TODO |

Anonymisiert heißt, dass zur Speicherung von Informationen der Verweis auf eindeutige Identifikationsnummern (z.B. IP-Adressen, Session Daten) komplett bei der Erhebung oder kurze Zeit später entfernt oder stark verkürzt wird. Bei IP-Adressen bedeutet das, dass die letzten beiden Bytes mit Nullen ersetzt werden.

## Auswertung
Zur Überwachung und zur Reflexion von umgesetzten Konzepten und Konfigurationen unseres Netzwerkes, werden von uns folgende Daten ausgewertet:

* Dauerhafte Speicherung von E-Mails der Mailingliste im [[Archiv|https://planetcyborg.de/mailman/private/ff-bremen/]]. Dieses ist nur für Mitglieder der Liste verfügbar.
* Anzahl [[aktiver Nodes|http://bremen.freifunk.net/map/geomap.html]] und Vermashung innerhalb des Netzes

## Einschränkungen und künstliche Limitierungen
Um die Verlangsamung des Gesamtnetzes zu verhindern blockieren die VPN-Server Filesharing-Diensten den Zugang ins Internet. Die Limitierung in Form von Durchsatz, Verfügbarkeit, Latenz sind ausschließlich durch Rahmenbedingungen des Netzwerkes, deren Ressourcen und der aktuellen Nutzung begrenzt.

## Server Standorte
Die gesamte Server-Infrastruktur befindet sich in deutschen Rechenzentren.
