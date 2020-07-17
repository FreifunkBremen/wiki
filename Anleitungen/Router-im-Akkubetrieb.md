### Inhaltsverzeichnis:

- [Akkubetrieb_TP-Link_WR841n](#inhaltsverzeichnis_akkubetrieb_tp-link_wr841n)
- [Akkubetrieb TP-Link Archer C7](#inhaltsverzeichnis_akkubetrieb_tp-link_archer_c7)

----


###Akkubetrieb_TP-Link_WR841n 

Wer seinen Router durch zusätzliche Akkus schützen möchte,
findet im Netz viele Varianten. 

Ich hatt nun folgende Überlegung,
die Akkus sollten im Routergehäuse platziert werden,
ebenso der Laderegler. Der Router soll weiterhin über 
den Schalter ausschaltbar sein. Die Akkus werden geladen, 
wenn vom Netzteil Strom geliefert wird (bzw. wenn Spannung 
anliegt.) Wird das Netzteil bei eingeschaltetem Router abgezogen,
startet der Akkubetrieb.

Zwei Schwierigkeiten sind zu Beachten. Der Router lässt sich 
freiwillig nicht öffnen, es braucht schon etwas Gewalt. Bitte nicht
mit scharfkantigen Gerätschaften (Spachtel, Messer..) hantieren.
Verletzungsgefahr. Die zu beschaffenden Teile müssen die Erde
umrunden und das dauert. 2-3 Monate durchhalten ist angesagt.

Getestet ist das Vorhaben bisher an einem WR841n v.8, der mit 9 Volt
betrieben wird. Bei 12 Volt Geräten werden entsprechend 3 Akkus und 
ein Laderegler für 3 Akkus benötigt. Die Laderegler (PCB protection Board)
können belibig in Abhängigkeit der Akkus variert werden.

###Material: 
2 Akkus vom Typ 18650 (die sind viel in Laptops verbaut) ~~Neupreis ca. 1Euro
[Beispiellink eBay](https://www.ebay.de/itm/8X-18650-3-7V-12000mAh-Akku-Micro-Varta-Accu-Li-ion-Battery-for-LED-Torch-DR/253378430047?hash=item3afe88045f:g:uKkAAOSwRLZaYdfk)~~ **Fake-Akkus**

1 Laderegler, PCB protection Board für 2 Akkus (2S 18650 PCB Board)
[Beispiellink eBay](https://www.ebay.de/itm/2S-8A-7-4V-8-4V-Lithium-Cell-Li-ion-BMS-Battery-18650-Protection-PCB-Board/142381524809?hash=item212699a749:g:13oAAOSwlndZFoEa)

1 * Akku 18650 3200mah ca. 20€ [Reichelt.de](https://www.reichelt.de/industriezelle-li-ion-18650-3-7-v-3200-mah-button-top-nc-nl188-p151103.html?r=1)


###Zubehör: (bei einem Freifunker oder Hackerspace eures Vertrauens, werdet ihr fündig)
etwas Heißkleber oder Baukleber etc.
Isolierband, damit die Anschlusskabel mechanisch gesichert werden.
Lötkolben, Lötzinn, etwas Kupferdraht, Seitenschneider.

Wenn das Routerboard frei liegt, [siehe Bild OpenWRT forum](http://i49.tinypic.com/144070p.jpg)
sieht man auf der Unterseite (im Bild oben rechts) die Kontakte für den EIN/AUS-Schalter und der Netzbuchse. Am Platinenrand ist der Minuspol/Masse/Ground, zur Platineninnenseite der Pluspol/Power.

Den Verdrahtungsplan kann ich hier nur schriftlich hinterlegen, ist aber ganz einfach.

Den Minuspol/Ground verbinden wir mit PCB P-, den Pluspol/Power verbinden wir mit PCB P+. Also unser PCB Board wird mit den Anschlüssen P+ und P- mit der Netzgerätebuchse verbunden.
Die beiden Akkus verbinden wir mit mit PCB B+,BM,B-.
Akku 1, Pluspol mit PCB B+, Minuspol mit PCB BM.
Akku 2, Pluspol mit PCB BM, Minuspol mit PCB B-.

Wenn wir die Akkus in einer Richtung hintereinanderlegen, dann ist die Mitte an PCB BM angeschlossen, Der Pluspol des Akku 1 an PCB B+ und der Minus von Akku2 an PCB B.-

Es ist hilfreich, zunächst alle Drähte an das PCB Board zu löten um dann die Kabellängen anzupassen. Auf vielen PCB Board sind an den Lötstellen kleine Metallplättchen vorhanden. Das sind Schweisspunkte für Akkus mit Metalllaschen zur industriellen Fertigung. Diese können beim Auflöten des Kabels leicht verrutschen. Wenn der Lötvorgang schief geht, können die Plätchen auch entfernt werden. Die sind zum Anlöten überflüssig. 

Sind die Kabel an den Akkus angelötet, werden diese mit Isolierband fixiert, damit diese durch mechanische Bewegung nicht abbrechen.
Jetzt alles in das Routergehäuse kleben. Fixpunkte reichen aus.

Testen: Netzteil anschliessen, die Akkus werden geladen. Mein Netzteil war etwa 1 Stunde lang Handwarm. Router einschalten, Lampen blinken. Netzteil abziehen, Router läuft immer noch :-)
Wer mag, kann den Router nun wieder zusammenbauen.


Laufzeit: WR841N V8 mit LEDs und 2*12000mAh 

####Testlauf 1: 3h Ladezeit, Router lief ca. 2h (das war wenig).

####Testlauf 2: 14h Ladezeit, Router lief ca. 2h (auch das war wenig).

![WR841N Akkupack](https://cloud.ffhb.de/index.php/s/uqOQd5TvHPhzyFy/download)

![WR841N mit Akku](https://cloud.ffhb.de/index.php/s/dcOuyUp9BKxElBd/download)

**Nach dem Test der 12000mah Akkus stellte sich heraus, das es chinesische Fake-Akkus sind. Für den Akkubetrieb bitte vernünftige Akkus kaufen.**



###Akkubetrieb TP-Link Archer C7

in Arbeit.
