# Team
Schreibt euch hier gerne rein, dann sehen alle wer dabei ist. Kontakt-Möglichkeit ist natürlich optional:
* SimJoSt - http://about.me/SimJoSt
* geno - geno@fireorbit.de (Mail, JID und als genofire im IRC)
* nukeUS (ff@nukeUS.de, IRC)
* anon6789
* Eike (ffhb-breminale at kexs.info)
* Julian (corny im IRC)

## Finanzierung der nötigen Hardware
### Förderung
#### O2 ThinkBig Upgrade (1000 Euro)
Durch die erfolgreiche Umsetzung eines O2 ThinkBig Basic Projektes, wie z. B. dieses [Freifunk für Findorff](http://www.think-big.org/projekt/freifunk-fuer-findorff), ist es möglich ein Folgeprojekt mir einer höheren Fördersumme als 400 Euro bewilligt zu bekommen.

Kontakt: [SimJoSt](http://www.about.me/SimJoSt)

### Sponsoren
Hat jemand irgendwelche Ideen?

* [Digineo GmbH](http://www.digineo.de) - Kontakt: Julian
  * einen Server
  * WDR3600 soviele wie wir brauchen (Leihgabe)

### Privatpersonen
Es wird auf die Unterstützung von Bewohnern am Osterdeich gehofft. Dafür müsste noch einiges an Werbung gemacht werden.

Außerdem wären Leihgeräte, vor allem Außenstationen, sehr erwünscht.

## Kontakt zur Breminale
* Sternkultur
  * Telefon: +49 421 500 504
  * E-Mail: info@sternkultur.de
* Max Maurer - Geschäftsführer Sternkultur UG
  * E-Mail: maurer@sternkultur.de

## Promotion
### Aufsteller
Der Gruppenkonsens ist, dass Aufsteller an allen Ecken eine stärkere Werbewirkung haben würden, als ein Stand. Außerdem müssten diese eh aufgestellt werden, um auf das freie WLAN aufmerksam zu machen.

### Stand

Man könnte eine handvoll verschiedene NodeModelle verkaufen. (nuki)


# Aufbau Plan

## Offene Fragen

* Freifunk Firmware oder andere? z.B. mesht die Freifunkfirmware was nicht soll?
* "Magic-Box" die den Traffic auf verschiedene Internetzugänge verteilt und ausfälle abfängt.
* Wasserfeste Boxen für WDR-4300 und WDR-3600 ?

# Strukturübersicht
Hier eine kleine [(Google-) Karte](https://www.google.de/maps/@53.0708917,8.8166142,16z/data=!3m1!4b1!4m2!6m1!1szLIdiavRRcUY.kHkfMt2Tp8Dk?hl=de) [[Detailiert](https://www.google.com/maps/d/edit?mid=zLIdiavRRcUY.kHkfMt2Tp8Dk)], für den mögliche Aufbau.

Diese sollte nachher genutzt werden um die Geräte nachzuverfolgen, damit nichts verloren geht.

## Anbindung
* Ideen für Frage nach Uplink:
  * Privat:
      * Oberweserstr.(Lars ehem. Lehrer)
      * Freifunker in Reederstraße
  * Firmen/öffentlich:
      * Brekom
      * LWLCom
      * Hochschule Werderstraße / Olbersplanetarium
      * Kunsthalle Bremen
      * Theater am Goetheplatz
      * Stadtbibliothek
      * Gerhard-Marks-Haus
      * Willhelm-Wagenfeld-Haus
      * Villa Ichon
      * Gesamtschule Mitte an der Brokstraße
      * Bürgerhaus Weserterrassen
      * Cafe Sand
      * Umgedrehte Kommode (wird wohl nix)
  * Dedizierter VPN-Server (von Julian bei Plutex)

### Hardware zur Anbindung
* VPN-Box (mortzu)
* ein Server von [Digineo GmbH](http://www.digineo.de) - Kontakt: Julian



## Nodes
  Möglichst wenig Meshing  !!
  
  Leihgaben:
  * 30-50 x TL-WDR3600 und ein Router (z.B. [APU.1D](http://www.pcengines.ch/apu1d.htm)) - [Digineo GmbH](http://www.digineo.de) / Kontakt: Julian
  * 14x WDR4300, 10x 3600, 2x 3500 (süß :), dutzende PlasteRouter (2.4GHz, 1-3 Antennen), 2x PicoStation 2HP, NSM2, NSM5, 3x NanoBridge 2.4 GHz, Parabol 6° (FF-Firmware läuft direkt darauf)
  * 10+ bald 31 x NS 5 Loco, NS2, NS2 loco, 9x NS5 (bald) (FF-Firmware läuft NICHT darauf, aber jew. 2  als Bridge ersetzen ein Kabel oder im AccessPointModus an LAN-Ports von  Nodes nutzbar) (nukeUS)

  * 3 x UniFi AP (Nebirosh)

## Verkabelung
Vorschlag (Julian):
* Nodes (WDR3600 oder WDR4300) in Abständen von 50-100 Metern installieren, untereinander verkabeln und auf die verfügbaren WLAN-Kanäle verteilen.
* Kabel sollte robust sein und für spätere Projekte wiederverwendet werden können.
* Zentraler Router für DHCP, VPN, Load-Balancing und Traffic-Shaping
* Switch-Konfiguration des WDR{3600,4300}: Alle Ports ins gleiche VLAN, oder zwei VLANs (management + Freifunk)
* Kein Meshing, Monitoring evtl. mit Alfred - muss auch ohne Internet funktionieren.


Vorschlag (Eike):
* Das Netzwerkkabel sollte von den Personen mitverlegt werden die die Stände mit Strom verkabeln. Es wird sicher einen Plan geben was wo hinkommt auf der Breminale. Da könnten wir entsprechend markieren wo Access-Points hinsollen. Kabel dann am besten von der Rolle und wir müssen da Stecker oder Dosen anbringen.

Vorschlag (nukeUS):
* Nodes (wenn nicht outdoor, dann in BrotDosen oder sonstwas für Boxen) auf vorhandenen Masten entlang des UferWeges auf der Seite zur Weser UND (mit Versatz) auf der Linie wo die DeichSchräge beginnt (Knick). So würden die Kabel beim Abbau (zB der Zelte) nicht stören. Man könnte den ein oder anderen Node aber auch in den höchsten Punkt von den Zelten hängen.



