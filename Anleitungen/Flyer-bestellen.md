# FFHB-Flyer bestellen
Wenn wir neue Flyer gedruckt haben wollen, kann dafür das PDF von https://github.com/FreifunkBremen/flyer/blob/short/flyer_short.pdf benutzt werden.

Der Druck sollte mit folgenden Einstellungen passieren (diese Einstellungen sind so bei Flyeralarm zu finden, aber sollten sich auch auf andere Druckereien übertragen lassen):
* Ausführung: DIN-Format
* Format: "DIN lang" (9,8 x 21 cm) (das PDF hat 10 x 21,2 cm; die 2 mm werden beim Drucken als Beschnitt gebraucht)
* Material: 250g-Papier, Bilderdruck, glänzend
* keine Veredelung
* Farbigkeit: 4/4 farbig (also beide Seiten in Farbe gedruckt, mit CMYK)
* Basis-Datencheck (das eingecheckte PDF ist bereits druckfertig)
* Digitalproof: nein; Ecken abrunden: nein; Perforation: nein; Bündelung: nein

Bei flyeralarm.de findet sich der Flyer unter Shop -> Druckprodukte -> Flyer -> "Flyer Klassiker".

1000 Flyer mit 250g-Papier ergeben einen Karton mit DIN-A4-Grundfläche und ca. 5 kg Gewicht.

## Flyer-Design verändern
Die Originaldatei liegt unter https://github.com/FreifunkBremen/flyer/blob/short/flyer_short.indd (als Adobe Indesign-Datei). Daraus wurde ein PDF erzeugt, welches ebenfalls eingecheckt wurde; dadurch können auch Leute den Flyer ansehen und drucken, die Indesign nicht zur Verfügung haben.

Wenn der Flyer verändert wurde, sollten die veränderte Originaldatei sowie die daraus erzeugte PDF-Datei wieder eingecheckt werden. Die PDF-Datei muss zum Drucken im [CMYK-Farbraum](https://de.wikipedia.org/wiki/CMYK-Farbmodell) vorliegen. Unter Linux kann man das z.B. mit [folgendem Befehl](https://superuser.com/a/370990) rausfinden:

`identify -verbose flyer_short.pdf | grep Colorspace`

Wenn `Colorspace: CMYK` ausgegeben wird, liegt das PDF im korrekten Farbraum vor.