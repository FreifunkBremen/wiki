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

* IPv4-Netz: 10.169.128.0/19 ist noch frei
* IPv6-Netz: kommt von LWLCOM, wenn wir kein VPN machen
* DHCPv4-Server: ISC-DCHPD oder Dnsmasq? Lease Time: 1 Stunde?
* DNS-Resolver? (Unbound?)
* radvd
* Wie Verbindung zu VPN-Servern?

### Node-Konfiguration

* Drei Varianten für das Switch:
 * Batman auf einzelne Ports
 * Software-Bridge mit STP
 * kein STP und kein Batman
* maximal 10 dBm Sendeleistung (Empfehlung von morpheus)
* 2.4 GHz-Kanäle: 1,5,9,13
* 5 GHz-Kanäle: 100-140
* Standard-Freifunk-Firmware
* Meshing über WLAN abgeschaltet

### Verkabelung
Sobald am Mi 08.07. die Verlegung der Stromkabel erfolgt, können wir starten die Netzwerkkabel an ihnen entlang zu legen und mit Kabelbindern festzumachen. Brilliant wäre es am Do 09.07. zum Ende des Tages fertig zu sein, damit wir am Fr 10.07. uns nicht in die Quere kommen mit den "Zeltaufbauern".

Vorschlag (Julian):
* Nodes (WDR3600 oder WDR4300) in Abständen von 50-100 Metern installieren, untereinander verkabeln und auf die verfügbaren WLAN-Kanäle verteilen.
* Kabel sollte robust sein und für spätere Projekte wiederverwendet werden können.
* Zentraler Router für DHCP, DNS, VPN, Load-Balancing und Traffic-Shaping
* Switch-Konfiguration des WDR{3600,4300}: Alle Ports ins gleiche VLAN, oder zwei VLANs (management + Freifunk)
* Kein Meshing, Monitoring evtl. mit Alfred - muss auch ohne Internet funktionieren.


Vorschlag (Eike):
* Das Netzwerkkabel sollte von den Personen mitverlegt werden die die Stände mit Strom verkabeln. Es wird sicher einen Plan geben was wo hinkommt auf der Breminale. Da könnten wir entsprechend markieren wo Access-Points hinsollen. Kabel dann am besten von der Rolle und wir müssen da Stecker oder Dosen anbringen.

Vorschlag (nukeUS):
* Nodes (wenn nicht outdoor, dann in BrotDosen oder sonstwas für Boxen) auf vorhandenen Masten entlang des UferWeges auf der Seite zur Weser UND (mit Versatz) auf der Linie wo die DeichSchräge beginnt (Knick). So würden die Kabel beim Abbau (zB der Zelte) nicht stören. Man könnte den ein oder anderen Node aber auch in den höchsten Punkt von den Zelten hängen.

### Strukturübersicht (nicht aktuell)
Hier eine kleine [(Google-) Karte](https://www.google.de/maps/@53.0708917,8.8166142,16z/data=!3m1!4b1!4m2!6m1!1szLIdiavRRcUY.kHkfMt2Tp8Dk?hl=de) [[Detailiert](https://www.google.com/maps/d/edit?mid=zLIdiavRRcUY.kHkfMt2Tp8Dk)], für den mögliche Aufbau.

Diese sollte nachher genutzt werden um die Geräte nachzuverfolgen, damit nichts verloren geht.
