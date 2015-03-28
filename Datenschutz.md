Wie auf jedem Informationsverarbeitungssystem, fallen auch im Freifunk-Netzwerk und der weiteren Infrastruktur, zum Betrieb mehr oder weniger erforderliche, Verbindungs- und Metadaten an. Dieser Umstand kann dazu führen, das durch personenbezogener Daten, Kommunikation auf eine oder mehrere Personen zurückverfolgt und damit die Privatsphäre der Kommunikationspartner verletzt werden könnte. 

Wir möchten daher auf dieser Seite so transparent wie nur möglich sein und offenlegen in welchem Umfang wir welche Daten vorhalten oder auswerten.

## Datenerhebung und Verarbeitung

Folgende ''uns bekannte'' Daten werden auf Freifunk-KBU Systeme erhoben und unterliegen folgende Aufbewahrungsfristen:

| Typ           | Anonymisiert | Speicherzeit auf Server | Speicherzeit im Backup |
|---------------|--------------|-------------------------|------------------------|
| Webserver     | ja           | 1 Monat                 | Serverzeit + 8 Tage    |
| Traffic Daten | ja           | ∞                       | Serverzeit + 8 Tage    |
| Mailingliste                    | nein         | ∞                       | Serverzeit + 8 Tage    |
| E-Mail Logs (warn, info, error) | nein         | 1 Monat                 | Serverzeit + 8 Tage    |
| Wiki Historie | nein | ∞ | Serverzeit + 8 Tage |
| Logins | nein  | 1 Monat | Serverzeit + 8 Tage |
| Webcache | ja | - | - |- |
| DHCP-Leases | TODO | TODO | TODO |
| MAC und IP-Adressen für BATMAN | TODO  | TODO | TODO |

Anonymisiert heißt, dass zur Speicherung von Informationen der Verweis auf eindeutige Identifikationsnummern (z.B. IP-Adressen, Session Daten) komplett bei der Erhebung oder kurze Zeit später entfernt oder stark verkürzt wird. Bei IP-Adressen bedeutet das, dass die letzten beiden Bytes mit Nullen ersetzt werden.

== Auswertung ==

Zur Überwachung und zur Reflexion von umgesetzten Konzepten und Konfigurationen unseres Netzwerkes, werden von uns folgende Daten ausgewertet:

* Dauerhafte Speicherung von E-Mails der [[Mailingliste]] und öffentlicher Zugang zu dem [http://lists.kbu.freifunk.net/pipermail/freifunk-bonn/ Archiv] der Liste
* anonymisierte Webseiten Zugriffe und graphische Auswertung mit awstats
* anonymisiertes [[Statistik:kbu internet|Trafficaufkommen]] innerhalb des Freifunk-KBU Netzwerkes und in andere mit angeschlossene Netze
* Latenzzeiten [[Statistik:ping kbu|innerhalb]] des Freifunk-KBU Netzwerkes und in [[Statistik:ping internet|andere]] mit angeschlossene Netze
* Anzahl [[Statistik#Node_.C3.9Cbersicht|aktiver Nodes]] und Vermashung innerhalb des Netzes

== Einschränkungen und künstliche Limitierungen ==

Grundsätzlich ist innerhalb des Freifunknetzes-KBU, sowohl die Kommunikation innerhalb, als auch mit externen Netzen, wie das Internet, uneingeschränkt möglich und in keiner Form künstlich limitiert. Die Limitierung in Form von Durchsatz, Verfügbarkeit, Latenz sind ausschließlich durch Rahmenbedingungen des Netzwerkes, deren Ressourcen und der aktuellen Nutzung begrenzt.

== Server Standorte ==

Sämtliche Server Infrastruktur, die wir für das Freifunk-KBU Netz benötigen, steht in deutschen Rechenzentren.
