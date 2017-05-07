# Archivierte Version vom Orga-Pad 2016

(kopiert von https://pads.hackerspace-bremen.de/p/ffhb-breminale-2016)

Freifunk Bremen auf der Breminale 2016

IRC: irc://irc.hackint.net/#ffhb_events
JOINEN

Wiki-Seite: http://wiki.bremen.freifunk.net/Events/Breminale/2016/Alles <-- WICHTIGE INFOS AN EINEM ORT (bitte dort sammeln und aktuell halten)

Termine
* Vergangene Termine unten im Archiv
* Breminale-Beginn: Mi, 13.7., nachmittags
* Breminale-Ende: So, 17.7., nachts
* Aufbau-Termine (  siehe unten
* Abbau am So. (17.07.) abends und Mo. (18.07.)
* After Breminale für Helfer im Licht/Luft-Bad neben dem Cafe-Sand. Mi. 20.7.2016 20:00 Uhr.

Nachbereitung
* Inventur
* Rechnungen
* Lagerorte
* Materialaufbewahrung z.B. Kabel Fasern https://www.amazon.de/Megaspule-Gleitgriffschale-Kabeltrommel-Schlauchtrommel-Seiltrommel/dp/B015E3P8FO/ref=pd_bxgy_60_2?ie=UTF8&psc=1&refRID=GVXV1KCRHW996A8GVEX2

Personen während des Events:
Anwesenheits-Dudle: https://dudle.hackerspace-bremen.de/FFHB-Breminale-Anwesenheit/

Termine Aufbau/Todo:
Alte Karte: https://www.google.com/maps/d/viewer?mid=1ePMbTgT5_khZI3DS5QFdv0tevOU
Geojson: https://github.com/FreifunkBremen/internal-maps/blob/master/breminale.geojson
* 2016-07-09: Kartieren (Stromkästen und erste Stände mit Namen) [geno,eyk ]
* 2016-07-10: Glasfaser zur Wiese und zum Baucontainer (2 Leute) [oliver, jens, l3akage, chrische ]
* 2016-07-11: Kupfer Hauptnetz [oliver, geno ab 17h, jens nachmittags, frank 17h, l3akage, chrische, morpheus ]
* 2016-07-12: Hauptnetz auflegen (Kupfer + 2. Glassfaser backup) [ oliver, geno ab 17h, jens nachmittags, frank 17h, l3akage, chrische, morpheus ]
* 2016-07-12: NOC+Routing [ oliver, geno ab 17h, jens nachmittags, frank 17h, l3akage, chrische, morpheus ]
* 2016-07-13: Nodes im Hauptnetz verteilen [ oliver, geno ab 17h, jens nachmittags, frank 17h, l3akage, chrische, morpheus ]
* 2016-07-13: Nebennetz verlegen [ oliver, geno ab 17h, jens nachmittags, frank 17h, l3akage, chrische, morpheus ]
* 2016-07-14: Nebenetz mit Nodes füllen [ oliver, geno ab 17h, jens nachmittags, frank 17h, l3akage, chrische, morpheus ]

Organisation
* Lager / Bauwagen oben am Deich beim Deichgraf
* Stand jetzt: kein Stand - Max sagt spontan möglich, er hat Tische und Bierbänke für einen Tagesstand

* Finanzen (Was kann wofür verwendet werden)
Ausgaben: https://docs.google.com/spreadsheets/d/1mH9ZZ-kR_Yqp2SETsaSJQfc0MYYyVs4lhM_QErSMUX8/

* Inventar bestellt / geliefert:
* 6x Outdoor-Boxen 
* 6x POE Adapter für Boxen ( Active POE => Knoten )
* 8x https://www.amazon.de/DeTeWe-Outdoor-8000-Quad-Funkger  [4x bleiben bei Digineo]
* 700m LWL Kabel von Fiberstore zur Verwendung, 10x 50m, 2x 100m
* 1x Kabeltrommel
* 4x 7er Steckerleiste => 8 Euro
* Kabelbinder ( Digineo ) bestellen
* 5x große POE Peitsche ( Digineo ) + Netzteile
* 4x https://www.gravidus.de/documents/image/25/2570/Rollenbox-Rollkiste-Rollbox-Aufbewahrungsbox-Trans_3.jpg / https://www.gravidus.de/documents/image/25/2570/Rollenbox-Rollkiste-Rollbox-Aufbewahrungsbox-Trans_2.jpg (Maße 60x38x32cm)
* 20x http://www.ebay.de/itm/130940952917
* 2x Isolierband
* 4x Panzertape

NOC-Konfiguration

Gestrichen = FERTIG
Rest = TODO

* Firmware Software(Normale Software)

    * Kein Batman

    * extra 5ghz ssids für NOC um an die knoten unproblematisch zu kommen

    * breminale firmware wie im letzten jahr

    * SSIDs:

    * 5 GHz bremen.freifunk.net

    * 2.4 GHz: freifunk.net

    * Sendeleistung default: 0db

    * vlan config anpassen (wie im letzten Jahr)

    * ssh key (wie im letzten Jahr)

    * first start (wie im letzten Jahr)

    * 5ghz outdoor channels patching wird getestet (morpheus) -> soll geno machen (da er nodes hat):)

    * broadcast multicast etc. von den clients muss gefiltered werden 

    * max assoc auf den zellen

    * client isolation aktivierenwir 

    * greifen die multicast filter von gluon wegen dem interface namen bat0? -> https://github.com/freifunk-gluon/gluon/tree/master/package/gluon-ebtables-filter-multicast/files/lib/gluon/ebtables

    * Ja, wir haben ne eigene Variante davon: https://github.com/FreifunkBremen/ffhb-packages/tree/breminale2016/ffhb/ffhb-breminale/files/lib/gluon/ebtables

    * Watchdog in die Firmware: Node sollte keine Freifunk-SSID ausstrahlen, wenn er kein Netz hat (und am besten sogar eine spezielle Debug-SSID (MAC / Node-ID als SSID ausstrahlen)

    * Watchdog: management-SSID bei Nicht-Erreichbarkeit des Gateways deaktivieren und MAC-SSID aktivieren

    * alle SSIDs bis auf die Debug-SSID müssen beim ersten start deaktiviert sein, der watchdog aktiviert diese dann


     IPs, VLANs, LWL unter https://docs.google.com/spreadsheets/d/1mTcofRJkzV9i8lFnq1nwvowXUyyG6k7pJ3c0_TOzc4s/edit#gid=0
     Observium: https://observium.breminale.ffhb.de/ readonly / breminale#2016



Knoten:

    * Deichseite wie im letzten Jahr

    * Zelte wie im letzten Jahr (Hauptbühnen)


Monitoring Software:

    * Macht Geno, im Grunde schon gut - Wünsche hier:

    * GPS Tagging

    * Knoten-Gruppen (mit benutzerdefinierten Namen), z.B. um einen Stapel von Knoten zusammenzufassen

    * Icinga-/Nagios-Config generieren (wird periodisch per wget abgerufen, in Icinga eingepflegt, und erlaubt separates Monitoring der Knoten)

    Welches Format? oder ihr baut selbst was, mit jq oder so: https://mgmt.ffhb.de/api/nodes

    * rot/grün-Markierungen sind schlecht für Farbenblinde -> vorschlag? (ich bin nicht farbenblind, daher kann ich keine anung) 7,7% der männl. Deutschen sehen rot/grün als Grünabstufung.

    wäre nur für eine Zertifizierung interessant. (siehe: https://en.wikipedia.org/wiki/Color_blindness ) oder ( https://de.wikiversity.org/wiki/Kurs:Barrierefreiheit_von_Internetseiten/Farbenfehlsichtigkeit#Tests_zur_Farbwahrnehmung )

    Ernsthaft, das Problem ist mir egal, ich will ne lösung -> Du sollst Farben vorschlagen

    * gute Unterstützung für übereinanderliegende Knoten

    * Karte sollte darstellen, wieviele Clients mit welcher "Position" verbunden sind (getrennt nach 2.4 und 5 GHz), damit man die örtliche Band-Auslastung sieht

    * Karte sollte auch eine reine Knoten-Ansicht haben, damit man z.B. örtliche Stromausfälle sieht

    * meshviewer.breminale.ffhb.de

    * Bugs:

    - Group kann nicht gelerrt werden. (wird zunächst nicht behoben)


    
PR / Marketing:

    * Flyer müssen bestellt werden

    * breminale.ffhb.de gibt es nicht    - ist als QR Code im Programmheft 

    Ergänzung Frank 23.6. QR-Code leitet auf breminale.ffhb.de, Seite funktioniert und ist ok.

    Ja läuft ja auch noch auf meinen Server -> steht bloß überall 2015 und müsste angepasst werden (https://github.com/FreifunkBremen/breminale.ffhb.de - geno)

    Jetzt wo das sagst, stimmt, hab ich nicht gesehen.Dennoch tolle Seite, nur geringe modifikation nötig :-))

    * (text über freifunk / wlan ) http://breminale.sternkultur.de/files/press/Breminale_Programmheft_2016.pdf

    * Aufkleber / Fliiiier ( http://data.timlukas.de/ffhb-breminale2016-flyer.pdf )

    * Zeitungsartikel 


----- ende des treffens 

Orga Vorort
NOC
- Installation Software/Konfiguration
- Installation Hardware
Person-Orga
- Boten
- Lagerwache (laufende Inventur)
- Ankunft und Verantwortung

    PR-Orga


Aufbau Plan
* Wie im letzen Jahr
* Am Deich Outdoor-Boxen
* An der Weser????

    * Wie letztes Jahr + CPEs regelmäßiger an der Lichterkette [CPE auf 2,4GHz funktioniert über den Köpfen nicht ( Band zu voll ) -- morpheus

* Drei Äste:

    * Wiese

    * Anfang (3 Meterbretter)

    * Ende der Breminale



Gespräche/Fragen (mehr oder weniger geklärt):

Simon:
* Stand?
* Möchtest du Aufgaben abgeben

Max-Gespräch:
* Wir nehmen Fahnenmast (welche größe)
* Können wir wieder Hardware im Bauwagen von euch hinstellen
* Lichterkette? jo! -SimJoSt
* Strom nach außen legen (als Steckdose oder das Ende vom Netzteil) kein Problem -SimJoSt

Julian:
* Gelder? 554,47 € + knapp 1000 € -SimJoSt
* Gehäuse vs. Outdoor-Boxen Frank baut Boxen

***Archiv***

Frank am 12.7.  Gestern war ein Artikel zur Breminale und Freifunk in der Tageszeitung, wie heissen die? ah BremerKurier
http://www.weser-kurier.de/bremen/breminale2016_artikel,-Festival-Macher-schlagen-ihre-Zirkuszelte-auf-_arid,1415137.html
Auszug:...Außerdem stellt der Anbieter Freifunk auf der Breminale 80 kostenlose  WLAN-Knoten auf, die unter freifunk.bremen.net erreichbar sind....

Frank: am 18.6.2016
    Erste Aktivitäten, suche nach Gehäusen und Anschlusskabeln durchgeführt.
    Outdoorgehäuse und Material
Bilder Link auf Winzigweich OneDrive: https://1drv.ms/f/s!AqaKqOmiM6_ojDuZ8bD9RMa07rYh hochgeladen
Gefunden bei: Hellweg Zentrum 3. Etage
Steckdosenleisen von 8-16€ Wasserdicht, Gehäuse alle mit Bügel zum Anketten.
Diesen Bügel haben die Bauhaus Leisten nicht.
https://1drv.ms/i/s!AqaKqOmiM6_ojC1DoCu3Nlemh0nt
Verlängerungskabel, gute Qualität, Stecker demontierbar. Etwas teurer als Baumarkt.
https://1drv.ms/i/s!AqaKqOmiM6_ojC5HPBrRXyfduoSH
Vollgummikupplungen, 1/2 Preis gegenüber Baumarkt.
https://1drv.ms/i/s!AqaKqOmiM6_ojDAIMs8bKiS_XBhJ
Noch ein Outdoorfähiges Verlängerungskabel, zerlegbar.
https://1drv.ms/i/s!AqaKqOmiM6_ojDFbKFw6Jg4inZvY
Gefunden bei: Bauhaus
Brauchbares Verlängerungskabel, jedoch nicht zerlegbar.
https://1drv.ms/i/s!AqaKqOmiM6_ojDLshrKoohpQA17f
Gehäuse: Für meine Vorstellung sieht das alles Übel aus.
Die Wasserdichten Elektrogehäuse kosten zwischen 50 u. 90€
Der gröste Kasten bei Bauhaus 23€, bei Amazon 20€
https://1drv.ms/i/s!AqaKqOmiM6_ojDN6ubrUIIEsBU2I
Die Qualität ist Baumarktqualität, also Chinaware.
Diese Haushaltsboxen haben noch etwas stabilität, jedoch muss der Deckel
mit Silikondichtung abgedichtet werden. Einziger Vorteil, Ineinanderstapelbar.
https://1drv.ms/i/s!AqaKqOmiM6_ojDYZb3LqoJ7uOwH5
Beim Bauhaus gab es eine kleine Auswahl an Euroboxen, die verdienen
den Namen nicht, da sie nichts mit dem Original gemeinsam haben.
https://1drv.ms/i/s!AqaKqOmiM6_ojDqEAofqW18stmV6
Die Passgenauigkeit unter aller Sau, der Deckel ohne Dichtung.
Normalerweise sehen die so aus:
http://www.auer-packaging.de/images/product_info/eurobehaelter_koffer2.jpg
http://www.auer-packaging.de/de/eurobehaelter-koffer_52.html
http://www.auer-packaging.de/de/eurobehaelter-mit-scharnierdeckel-ed4375hg_1_596.html
und mit Griff +10€ pro Kiste
http://www.auer-packaging.de/de/eurobehaelter-koffer-ed43751g_1_712.html
Fazit:
Habe mir gleich ein paar Boxen 30x40x9 zur Qualitätsprüfung bestellt :-) Ich kenne die kleinen Euroboxen
zum Versand von ESD Material, mit richtigen Scharnieren und Schlössern, richtig Wasserdicht.
Deshalb kann ich mir die Eurobox in der richtigen Qualität sehr gut als Outdoorgehäuse vorstellen.


* wieviel Geld können/wollen wir dafür ausgeben?
* harte Anforderungen:
** regendicht
** abschließbar
** ist die ganze Zeit vor Ort (11.7 bis 18.7)
** wird geliefert oder lässt sich dahin transportieren
* weiche (nice-to-have) Anforderungen:
** Strom drinnen
** Stehhöhe
* Brainstorming:
** Bauwagen mieten
** normales Auto mieten und hinstellen
** Wohnwagen
** Bauwagen
** Gartenhäuschen
** Auto-Anhänger
*** z.B. hier: http://sp-anhaenger-vermietung.de/kofferanhänger.html (120 € für 7 Tage)
** MS Treue (genofire versucht mal was)
** Feuerwehr fragen?
** Materialcontainer
* -> Jens erkundigt sich nach solchen Sachen
 
* Anforderungen:
** regendicht
** diebstahlsicher: weder Kasten noch Inhalt sollen gestohlen werden
** Strom auserhalb oder innen
** lässt WLAN gut durch
** WDR-Knoten passt unmodifiziert rein
** lässt sich an einem Mast und/oder Stromkasten diebstahlsicher befestigen

* Termine
* Kickoff: Mi, 22.06.2016, 19:00 Uhr, Hackerspace Bremen - Kreativwerkstatt
* Zweites Treffen: Di. 28.06.16, 19:00 Uhr, Embassy of Nerdistan

    Themenwunsch für 28.6.: Inventur / Zwischenlagerung Material & Geräte/ Termine & Ort für Zusammenbau SW & HW / Transport zum Bauwagen (wer hat ein Auto für den Transport?) (Getränketransport)

    Karte/Netzplan, längen wie 2015?, 28 Stromkästen an jedem eine Outdoorrouter anklemmen? (6 Boxen mit POE)

    Erprobte, gute Geräte, mit Subchannels, Akku, Headset etc.: https://www.amazon.de/DeTeWe-Outdoor-8000-Quad-Funkgerät/dp/B001CSPXQ0/

    Temporäre Lagermöglichkeit im Space erfragen?

    Gibt es Orga-Treffen von Sternkultur, an denen wir Teilnehmen können? (Wegen Kartenaktualisierung, Kontakt zur ElektrikerCrew)

* Drittes Treffen: Di. 05.07.16, 19:00 Uhr,  Hackerspace Bremen

    Die ersten zwei Outdoorboxen sind mit je 60m Lankabel versorgt und können mit Routern bestückt werden. wäre schön, wenn wir dieses am Di. 5.7. erledigen könnten

    und die bestückten Boxen für einen Testbetrieb im Space anschliessen könnten. Für die weiteren Boxen benötige ich 4 * 50m LAN-Kabel, sonst muss die Montage auf dem 4ten Treffen erfolgen.

    Foto:-) https://1drv.ms/i/s!AqaKqOmiM6_ojRdPmq5ZBsJ38OQi

* Viertes Treffen: Fr. 08.07.16, 19:00 Uhr Bauwagen am Osterdeich

***Archiv-Ende***