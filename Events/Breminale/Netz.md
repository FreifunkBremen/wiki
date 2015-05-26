## Ziele

### Allgemein

Jeder Besucher der Breminale sollte über unser Netz einen möglichst performanten Zugang zum Internet erhalten, sowie auf Dienste von uns zugreifen können. Am besten:

* Ausreichend Access-Points für alle Besucher (10-20k) auf dem gesamten Gelände (25.000 m²).
* Unbegrenzte Bandbreite und geringe Latenz ins Internet.
* Egal was ausfällt, der Rest sollte weiter funktionieren.

Welche Ziele wir davon wie weit erreichen können, hängt ab von:
* Freiwilligen Helfern
* Leihgaben
* Finanzierung der Internet-Anbindung und benötigter Materialien ([[Events/Breminale/Finanzierungen]])

### Wir wünschen uns

* Möglichst viele Helfer
* Uplinks: Mehrere Glasfaser mit Gbit oder VDSL-Leitungen
* VPN-Server: Mindestens zwei mit ausreichender Anbindung und Leistung
* Zentraler Router auf dem Gelände. Ein Ersatzgerät wäre gut.
* Switches: Gbit-Switches wo möglich.
* Access-Points: Möglichst Dual-Band.
* Kabel und sonstiges Material
* Evtl. Richtfunk-Antennen

Genauere Auflistung von Material und Stückzahlen:
[[Events/Breminale/notwendiges-Material]]

## Umsetzung

### Haftung

Es gibt zwei Varianten, wovon die Variante ohne VPN performanter und weniger störanfällig ist:

1. Sternkultur ist Anschlussinhaber, Traffic wird über VPN von Mortzu getunnelt
2. Digineo GmbH ist Anschlussinhaber, Traffic geht direkt raus

### Komponenten (haben wir sicher)

* Gbit-Fiber und Transceiver (SFP) von LWLCOM
* Zentraler Router und Switch (Julian), Backup: ?
* Kleine Debian-Kiste für Monitoring und andere Dienste (Julian), Backup?
* WDR3600/WDR4300 als Nodes (Julian und nukeUS)

### Router-Konfiguration

* IPv4-Netz: 10.169.128.0/19?
* IPv6-Netz: kommt von LWLCOM, wenn wir kein VPN machen
* DHCPv4-Server: ISC-DCHPD oder Dnsmasq?
  * Lease Time: 1 Stunde?
* radvd
* DNS-Resolver? (Unbound?)
* Wie Verbindung zu VPN-Servern?

### Node-Konfiguration

* Drei Varianten für das Switch:
 * Batman auf einzelne Ports
 * Software-Bridge mit STP
 * kein STP und kein Batman
* maximal 10 dBm Sendeleistung (Empfehlung von morpheus)
* 2.4 GHz-Kanäle: 1,5,9,13
* 5 GHz-Kanäle: 100-140
