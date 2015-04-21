# Fragen fürs Treffen
* Pläne
  * Kabelspinne (mit Klassifizierung der Kabel)(Karte zum Planen)
  * Zelte
  * alles
* Anbindung
  * bereits vor Ort?
  * Ideen für Ansprechpartner?
  * 
* Aufbau
  * inwiefern werden Kabel verlegt?
  * Platz für Stand oder NOC?
  * sind Masten vorhanden? oder dürfen wir einen eigenen Mast aufstellen? (Zelte bewegen sich bei Wind)
  * wo können INDOOR Nodes unterbringen (damit wir uns die Gehäuse sparen)
* Promotion / Publicity
  * Aufsteller
  * Stand (bei NOC?)
  * welche Ankündigungsmöglichkeiten hat die Breminale (für Freifunk)?
* Dienste
  * Breminale-App Aktualisierung
  * Breminale-Web-Site
  
### Leitgedanken
* keine festen Zusagen
* nichts (außen) selbst verlegen


# Team
Schreibt euch hier gerne rein, dann sehen alle wer dabei ist. Kontakt-Möglichkeit ist natürlich optional:
* SimJoSt - http://about.me/SimJoSt
* geno - geno@fireorbit.de (Mail, JID und als genofire im IRC)
* nukeUS (ff@nukeUS.de, IRC)
* anon6789
* Eike (ffhb-breminale at kexs.info)

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
  * 30-50 x TL-WDR3600 [Digineo GmbH](http://www.digineo.de) - Kontakt: Julian

  * 20x WDR4300, 10x 3600, 2x 3500 (süß :), dutzende PlasteRouter (2.4GHz, 1-3 Antennen), 2x PicoStation 2HP, NSM2, NSM5, 3x NanoBridge 2.4 GHz, Parabol 6° (FF-Firmware läuft direkt darauf) (nukeUS)

  * 3 x Uniquity AP (Nebirosh)

## Verkabelung
Vorschlag (Julian):
* Nodes (WDR3600) in Abständen von 50-100 Metern installieren und untereinander verkabeln
* Kabel sollte robust sein und für spätere Projekte wiederverwendet werden können. Bis 50m vorkonfektioniert, über 50m selbst crimpen.
* Kein Meshing auf den Nodes, aber [Multicast-Filter](https://github.com/freifunk-gluon/packages/tree/master/gluon/gluon-ebtables-filter-multicast/files/lib/gluon/ebtables)
* Zetraler Router für DHCP, VPN und Load-Balancing
* Switch-Konfiguration des WDR3600: Alle Ports ins gleiche VLAN, oder zwei VLANs (management + Freifunk)


Vorschlag (Eike):
* Das Netzwerkkabel sollte von den Personen mitverlegt werden die die Stände mit Strom verkabeln. Es wird sicher einen Plan geben was wo hinkommt auf der Breminale. Da könnten wir entsprechend markieren wo Access-Points hinsollen. Kabel dann am besten von der Rolle und wir müssen da Stecker oder Dosen anbringen.

Vorschlag (nukeUS):
* Nodes (wenn nicht outdoor, dann in stabilen Tüten [mit AbstandsHaltern aus Pappe oder so damit der Node Luft zum Atmen hat] oder in sonstwas für Boxen) auf min. 3-4 m hohen Stangen (Baustahl) oder Rohren (hab ich ca 5 Stk) entlang des UferWeges auf der Seite zur Weser UND (mit Versatz) auf der Linie wo die DeichSchräge beginnt (Knick). So würden die Kabel beim Abbau (zB der Zelte) nicht stören. Man könnte den ein oder anderen Node aber auch in den höchsten Punkt von den Zelten hängen.

* Kabel 5-10cm tief im ErdReich, in einen (mit einem Spaten gemachten) Schlitz, verlegen. Entlang der Stangen (senkrecht) die Kabel zB mit PappRohren (StoffHandel entsorgt viele, habe nur 15 Stk, a 1,5m) schützen.

* Sternförmige Verkabelung wäre wohl technisch am besten, aber pragmatisch gesehen müssen wir die LAN-Ports bridgen, oder lieber auf unsere FF-FW verzichten und Open- oder DD- WRT oder die origiale FW nutzen und alle Nodes hintereinanderhängen, oder?.
