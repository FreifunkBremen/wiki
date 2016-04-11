## Antennenbau für Freifunkrouter

Bitte auch folgende Seite Beachten: [https://wiki.freifunk.net/WLAN-Antennen](https://wiki.freifunk.net/WLAN-Antennen)

Für Antennen im Aussenbereich ist Blitzschutz erforderlich.

**Weiterführende Literatur:**

[1] Rothammels Antennenbuch, Dipl.-Ing. Alois Krischke

[2] Mobile Antenna Systems Handbook, K. Fujimoto, J.R. James

[3] ABB Merkblatt Blitzschutz von Antennen-Systemen in und auf Gebäuden

[4] Ausschuss Blitzschutz und Blitzforschung (ABB) des VDE

[5] Kapitel 18 des "ARRL Antenna Book" (Mehr Information als Rothammel)


###1. Kapitel  **2,4 Ghz Antennen**


Zunächst ein paar Zahlen, die wir benötigen:
Der 2,4 GHz W-Lan Bereich besteht aus 14 Kanälen mit je 25 MHz Bandbreite, also einem Bereich von gesammt 350 MHz Bandbreite. Wir wollen als Mittenfrequenz den Freifunk-Kanal 6 verwenden, Mittenfrequenz 2437 MHz. Das entspricht folgenden Wellenlängen. Lambda L = 123 mm, 3/4 L = 92,26 mm, 1/2 L = 61,51 mm, 1/4 L = 30,75 mm. Drahtdurchmesser eines 2,5 mm^2 Cu Drahtes = 1,79 mm, Innendurchmesser der benötigten 1/4 L Wicklung = 8 mm.



**Vorhandene Antennen**
Der klassische W-Lan Dipol hat 2,1 dB Gewinn, die Duoband-Antennen 3 dB bei 2,4 GHz und 5 dB bei 5 GHz. Bei den Duoband-Antennen wird gerne der theoretische maximale Gewinn für alles angegeben.

![WLAN Dipol](http://martybugs.net/wireless/images/ducky_element_tn.jpg)

Normale WLAN-Antenne 2,4 Ghz
Weitere Infos unter: [http://martybugs.net/wireless/rubberducky.cgi](http://martybugs.net/wireless/rubberducky.cgi)

Die einfachen Antennen bestehen aus einem Stück Koaxkabel. Die Schirmung wird an der Spitze um 1/4 Wellenlänge entfernt, ca. 3 cm. An dieser Stelle wird eine Hülse, ebenfalls 1/4 Wellenlänge angecrimpt. Antenne fertig. Jeder Stecker verbrauch 1 dB, ein Stecker ist auf dem Routerboard und einer ist für die Antennenverschraubung der Aussenantenne. Im Wiki des OpenWrt [https://wiki.openwrt.org/toh/start](https://wiki.openwrt.org/toh/start) sind für die Hardwaremodelle Bilder hinterlegt. Dort sind auch die Antennenanschlüsse beschrieben.

**Selbstbauprojekt 2,4Ghz Collinear Antenne**

Im Netz gibt es viele tolle Bastelanleitungen für 2,4 Ghz Antennen.
Hier eine Zusammenfassung für die Collinear Antenne, damit der Nachbau klappt. Wir verwenden einen R-SMA Stecker.


Bei der industriellen Produktion von Antennen, wird aus Kostengründen auf wichtige Komponenten verzichtet. Die Antenne als unsymmetrisches Element soll bei unserer Antenne mit einem Symmetrierglied in Form eines Topfkreises angepasst werden. Klingt nach viel Aufwand, ist es aber nicht und es wird sich bezahlt machen. Hier geht es nicht nur darum die Fehlanpassung der Antenne auszugleichen, sondern die sich ergebenen mechanischen Vorteile zu nutzen. Die Antennenlänge kann schon an die 62 cm Länge heranreichen und die soll direkt auf dem R-SMA Stecker angelötet werden. Der Pin ist 1,3 mm dick und der Antennendraht ca. 1,8 mm (2,5 mm^2 Cu). Das bricht sofort wieder auseinander. Aus diesem Grund wird ein Topfkreis in Form einer Metallhülse an den Stecker gelötet. In dieser Hülse von 1/4 Lambda wird ein Stück Dielektrikum aus eine Antennenkabel eingeführt, dass die Antenne stützen wird. An dieser Hülse kann ebenfalls das Antennengehäuse (Radom), z.B Kabelleerrohr, befestigt werden. Metallröhrchen 30 mm Länge 6-8 mm Durchmesser an den Stecker löten. Bei Crimp-Steckern ist eine Crimphülse dabei. Diese Hülse in 30 mm wäre perfekt.

![Topfkreis am Stecker](http://www.lincomatic.com/wireless/gnetlowpwr/decoupler_detail_diag.jpg)

Antennengewinn ca. 5-6 dB => 2 Windungen, Drahtlänge = 448 mm, Antennenlänge 355,5 mm 

Antennengewinn ca. 8 dB => 5 Windungen, Drahtlänge = 808 mm, Antennenlänge 623 mm

Zunächst die Variante 1 aus einem Stück CU Draht 2,5 mm^2
Kurze Antenne mit 5-6 dB.

![Antenne](http://martybugs.net/wireless/images/collinear_bare_tn.jpg)
![Antenne](http://martybugs.net/wireless/images/collinear_loop_tn.jpg)
![Antenne](http://martybugs.net/wireless/images/collinear_loop2_tn.jpg)

Drahtlänge mindestens 448 mm. Im Abstand 91 / 30,75 / 89 mm / 30,75 / 86 mm Markierungen anbringen. In der Mitte der kurzen Abschnitte einen 8 mm Kern zum Biegen auflegen und eine volle Windung erstellen.

![Collienar](http://martybugs.net/wireless/images/collinear_copper.jpg)

Die beiden Markierungen liegen danach an der Windung übereinander. An diesen Markierungen nun den Draht abwinkeln. Die Antenne gerade biegen und so weit auseinander ziehen, dass der Abstand zwischen den Windungen 92,2 mm beträgt.

Von der oberen letzten Windung bis zur Antennenspitze ist es etwas kürzer als 3/4 L. (ca. 3 mm) Auf das untere Ende der Antenne das Innenleben unseres Antennenkabels schieben. Prüfen, das es in die angelötete Hülse passt und den Antenndraht stabil halten kann. Den Mittelanschluss unseres Steckers an die Antenne löten. Antenne mit Mittelpin und Kunststoffhülse in den Stecker schieben und einrasten. Isolierband welches auf den Antennendraht bis zum Hülseninnendurchmesser aufgewickelt wird, geht auch.

Wird ein Kunststoffrohr über die Antenne geschoben, das untere Ende der Antenne leicht S-Förmig biegen, dann passt der Radom über die Hülse. Das obere Ende mit einer Verschlusskappe abdichten. Das untere Ende des Rohres unter Hitze verkleinern und verkleben. Alternativ kann die Hülse mit Heißkleber nach der Antennenmontage befüllt werden. Evtl die Hülse mit Isolierband umwickeln, damit das PG Rohr passt, sieht nicht schön aus. Besser ist eine schraubbare Buchse, wie sie für Kabeleinführungen verwendet wird. Kreative Bastellösungen wären auch ein 8 mm Kern in der Antenne, der Stab kann auch unten in die Hülse gesteckt werden. Dazu ist der Stab unten mit einer Säge einzukerben, damit der Antennendraht vom Rand in die Mitte laufen kann.

Lange Antenne mit 8 dB Gewinn.
Drahtlänge mindestens 808 mm. Aufbau wie die kurze Antenne. In der Mitte werden 3 weitere Abschnitte 30,75 / 89 mm eingefügt. Auch hier beträgt der Mittenabstand zwischen den Windungen 92,2 mm. Das sind 3/4 Lambda. Die fertige Antennenlänge ist 623 mm.

![more gain](http://martybugs.net/wireless/images/collinear_longer_dimensions.png)

Die Sendeleistung auf dem Router kann nun auf 25 mW (8 dB Antenne) bzw. 50 mW (5 dB Antenne) reduziert werden.
Zur Erinnerung, 20 dB maximum - Gewinn + Dämpfung 2 dB (es sind 2 Steckverbindungen) = 14 dB bzw. 17 dB Senderleistung.

Ohne Radom (PG Rohr / GFK Rohr) sollten die Antennen am Router hängen, mit PG Rohr als Radom können gut PG Klippschellen zur Befestigung verwendet werden.


**## Variante 2** Antenne aus  CU Draht Abschnitten mit kleiner Spule aus 1,5 mm^2 und Messingröhrchen.

![Teile](http://www.lincomatic.com/wireless/gnetlowpwr/Full_assy_measurments.jpg)

Das erste Messingröhrchen vom Stecker bis zur ersten Spule. Die Länge ist unkritisch, sollte aber L/2 haben. Herausragender Lötschluss 1 mm + 91 mm.

![Komplette Antenne](http://www.lincomatic.com/wireless/gnetlowpwr/complete_at_angle.jpg)

Kommen wir zum ersten Problem: Unsere Horizontlinie von der alles gemessen wird, ist die Gehäusekannte unseres Steckers. Über diese Gehäusekannte ragt unser Lötanschluss heraus, in diesen Lötanschluss stecken wir das erste Stäbchen. Welche Länge kommt heraus? Wie schon erwähnt, ist es unkritisch, wenn das Röhrchen zu lang/kurz ist. Stäbchen in/an den Steckersnschluss anlöten und von der Horizont Linie bis Stäbchenende sind es 3/4 L. Dann stülpen wir die Hülse über den Stecker. Ist der Lötrand 1mm, dann ist die Hülsenlänge L/4 + 1mm. Das ist alles Abhängig vom Hersteller und verwendetem Stecker/Buchse. Der Topfkreis soll durch einen Kunststoffeinsatz in der Mitte unsere Antenne stützen, damit durch mechanische Bewegung der Mittelpin nicht abbricht. Wird kein passender Isosator/ Kabelinnenleben gefunden, kann auch Heißkleber verwendet werden.

Das zweite Problem, die Spule.
Die Windungslänge sollte L/4 betragen.
Dies entspricht ca. eine Durchmesser von ca. 10 mm. Damit die Spule in ein Rohr unserer Wahl passt, wird der Aussendurchmesser entsprechend angepasst und die Anzahl Windungen erhöht. Wichtig ist nur, dass der für die Spule 
verbrauchte Draht L/4 ist. Damit die Spule die Antenne trägt und das Konstrukt nicht umknickt können bei einem 1 mm Cu Draht 4 Windungen mit 6 mm Durchmesser gewählt werden. Andere Berechnungen sind ebenfalls möglich.

Das dritte Problem, die Stäbchen.
Stäbchen brauche ich eigendlich keine, die Antenne kann aus einem Stück Draht gefertigt werden. Es ist aber leichter, wenn die Antenne aus Einzelteilen gefertigt wird.  Um das gut löten zu können, nehemn wir Messingrohr aus dem Baumarkt. Der verwendete Spulendraht muss in die Messingröhrchen passen, sonst gibt es keine weiteren Bedingungen. Die Länge der Röhrchen? Etwas kürzer als 3/4 L - Spulenlänge. Damit der Zusammenbau gut gelingt und genug Platz für den Lötkolben zwischen Spule und Röhrchen ist, legen wir die Länge der Röhrchen auf L/2-5mm fest. So einfach ist das. Messingrohr gibt es in 3 oder 4 mm Durchmesser im Baumarkt.

Das vierte Problem, die Spitze.
Die letzte Spule und das letzte Stäbchen sind etwas kürze als 3/4 L zu bauen. Dadurch wird die Resonanzstelle der Antenne etwas breiter und die Antenne wirkt elektrisch stabiler. Also die Spitze um 2-3 mm kürzen.

Damit die Antenne in dem späterem Schutzrohr nicht klappert, können auf die Messingröhren Stützscheiben aus Kuststoff angebracht werden. Auf dem langen Drahtabschnitt geht es auch, fall die Gefahr des Verrutschens besteht. Kleine Schaumgummizylinder ankleben.

Die Spulen werden um eine 4 mm Spaxschraube oder Ähnliches mit geradem Kern gewickelt. 4 Windungen, Aussendurchmesser 6 mm, 10 mm Draht unten, 30 mm Draht oben. Die Spule selbst ist ca. 20 mm lang. Die Spulensteigung ist ca. 3,5 mm. Die Messingröhrchen haben eine Länge von 56,5 mm.


Weiter Bilder unter: [http://iw3b.info/427/tutorials/homemade-16db-omnidirectional-antenna/](http://iw3b.info/427/tutorials/homemade-16db-omnidirectional-antenna/)

Zusammenbau: Der Stecker mit Hülse und Stäbchen 92 mm wird zuerst montiert. Die Antenne wird hier zum Schluss angelötet. Ein Antennenelement: Spule mit 10 mm Anschluss zeigt nach links. An das lange Ende der Spule auf der rechten Seite wird nun ein Messingröhrchen angelötet. Abstand com rechten Spulenknick bis zum Röhrchen 22 mm. Sind alle Elemente so zusammengelötet, werden die Elemente selbst miteinander verbunden. Das 10 mm Ende der Spule ragt noch 5 mm aus dem Rörchen heraus. Vom beginn einer Spule zur nächsten Spule sind es 92,26 mm. Das sind wieder die 3/4 Lambda. Vom begin der letzten Spule bis zur Spitze sollen es 98 mm sein, die Spitze wird ja um 2 - 3 mm gekürzt. Jetzt die Antenne an das Fußstück löten, mit dem Schutzrohr verbinden und fertig.


Wird die Antenne mit 4 Elementen aufgebaut, entspricht dies einem Gewinn von 5 dB, jedes weitere Element sorgt für 1 dB mehr. Ab 9 dB Gewinn ist der Öffnungswinkel schon sehr schmal (< 15 °) und eine Länge von 1150 mm erreicht.  Weitere Elemente verstärken jetzt nur noch um 0,5 dB. Kosten der Antenne. R-SMA Stecker, ca. 1,15 €, 1m 1*1,5 mm^2 Kabel ca. 1 €, Messingrohr 2,60 €, dünnes PG Rohr mit Verschlusskappe ca. 2 €. Zusammen ca. 6,75 €. Fertige Antennen mit ca. 6dB sind zu diesem Preis bereits zu bekommen.



###2. Kapitel Ausblick auf 5 Ghz.


Die Berechnungen sind gleich der 2,4 GHz Antennen. Alles wird kleiner.
Dieses kann aber nur durchgeführt werden, wenn der Router seperate 5 GHz Antennen hat.
 
Am Beispiel der TP-Archer C7 AC1750 Rev 1.1. 3 externe abnehmbare Antennen in Streifenleitertechnik für 5 GHz,  3 interne Antennen in Streifenleitertechnik (Metallprofil als kleine U Winkel im Gehäuserand) für den 2,4 GHz Bereich. Das 5 GHz Modul ist in einem Sockel Huckepack aufgesteckt und hat zusätzliche Steckverbinder. Der Archer C7 Rev 1.0 hat 2 externe Antennen, alle Funkmodule sind aufgelötet. Jedes Modul hat eine Antenne.

Es kann sich also lohnen, bei schlechter 5 GHz Versorgung eine neue Antenne herzustellen.

###3. Kapitel Ausblick auf Kombiantennen 2,4 GHz und 5 Ghz

Eine Kombination beider Antennentypen in nur einer Antenne bringt nicht die Verstärkung wie bei getrennten Antennen. Die Antennen haben zwei Resonanzpunkte für die beiden Frequenzbereiche und müssen mehrmals gestockt werden. Betrachtet man das Innenleben einer normalen Dualbandantenne, schauen uns zwei Antennen entgegen. Dieser Sonderfall ist eher selten anzutreffen. Die Antennen müssen sehr präzise gebaut werden. Bei Selbstbauantennen ist eine Abstimmung mittels Messtechnik zu Empfehlen.

###Anhang:
**Blitzschutz von Antennensystemen**
Für  den  Schutz  von  Antennen  gegen  Blitzentladungen  und  statische  atmosphärische Entladungen auf Dächern oder Masten gibt es eine einschlägige Normenreihe; diese wird unter VDE 0185 [1] bis [3] behandelt. Das Antennensystem  muss  -  gemäß  der  Definition  dieser  Normenreihe  - einem Blitz- Stoßstrom von 100 kA (Stirnzeit T1 = 10 ms, Rücken-Halbwertzeit T2 = 350 ms)  entsprechend  der  Schutzklasse  III,  definiert  in  der  Normenreihe  VDE 0185 [4] bzw. [5], standhalten. Zwingend notwendig dabei ist auch die Einbeziehung des Antennen-Systems in den Potenzialausgleich des  Gebäudes. Zur Vermeidung der Beschädigung von Access Points, Rechnern oder Netzwerken  durch Blitzschlag  oder  statischen  Entladungen  sollten  Überspannungsschutz-Komponenten    eingesetzt    werden.    Die    Einkopplung    von Überspannungen  kann  galvanisch,  induktiv  oder  kapazitiv  erfolgen;  durch geeignete  Sperren  ist  die  Abblockung  oder  Ableitung  von  Einkopplungen möglich. In der Praxis findet man oft eine Kombination aus beiden Methoden. 
