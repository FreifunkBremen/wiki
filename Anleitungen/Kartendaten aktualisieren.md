Unsere [Freifunkkarte](https://map.bremen.freifunk.net/) nutzt standardmäßig Kartenbilder, die von unserem eigenen Karten-Server ([[https://tiles.bremen.freifunk.net/]]) bereitgestellt werden. Um die Kartenbilder (die "Kacheln") zu erzeugen, nutzen wir die Software [Tessera](https://github.com/mojodna/tessera). Damit werden Vektor-Kartendaten vom [OpenStreetMap-Projekt (OSM)](https://www.openstreetmap.org/) auf dem Server in PNGs gerendert und an den Browser ausgeliefert.

Die Vektor-Kartendaten liegen auf dem Server in einer großen ["mbtiles"](https://github.com/mapbox/mbtiles-spec)-Datei. Wenn wir neuere Kartendaten anzeigen wollen, muss diese Datei gegen eine neue Datei ausgetauscht werden. Leider gibt es inzwischen die OSM-Daten nicht mehr kostenlos im mbtiles-Format, sondern nur im .osm.pbf-Format. Ursprünglich wurden die mbtiles-Dateien kostenlos auf [[https://openmaptiles.org/]] angeboten; aber dort gibt die aktuellen Daten nur noch gegen Gebühr.

Dieser Artikel beschreibt, wie man eine neue mbtiles-Datei aus den aktuellen rohen OSM-Daten erzeugen kann.


## Technische Details (für Interessierte)

* OSM-Daten werden öffentlich bereitgestellt im .osm.pbf-Format; das sind Vektordaten in einer Protobuf-Formatierung. Das OSM-Projekt stellt die kompletten rohen Daten in diesem Format bereit.
* ["mbtiles"-Dateien](https://github.com/mapbox/mbtiles-spec) sind sqlite-Dateien, die intern Vektor- oder Pixeldaten enthalten können. Wir benutzen nur [Vektordaten](https://github.com/mapbox/vector-tile-spec/) (weil die deutlich kleiner sind).
* unsere mbtiles-Vektor-Dateien enthalten nicht exakt die gleichen Daten, wie sie das OSM-Projekt bereitstellt; sondern:
	* das sehr komplexe Datenschema von OSM wird in ein einfacheres Datenschema umgewandelt, damit die Daten später einfacher darzustellen sind
	* unwichtige Daten (die wir sowieso nicht darstellen wollen) werden rausgefiltert
	* die Daten werden in Kacheln aufgeteilt, damit es später einfacher wird, Daten bestimmter Gegenden zu laden
* für die Konvertierung von .osm.pbf in .mbtiles gibt es mehrere Wege
	* wir benutzen hier die [Tilemaker-Software](https://github.com/systemed/tilemaker), weil die das alles in einem Schritt erledigt und einfach zu benutzen ist. Dafür benötigen wir aber einen starken Rechner mit viel RAM ([geschätzt](https://wheregroup.com/blog/tilemaker-am-limit/): die Dateigröße der .osm.pbf-Datei mal 12; bzw. mit Auslagerung auf SSD ca. Faktor 6).
	* alternativ gibt es auch eine Anleitung unter [[https://openmaptiles.org/docs/generate/generate-openmaptiles/]], die aber aufwändiger ist (dafür kommt die evtl. auch mit einem schwächeren Rechner aus)
* die Umwandlung in das einfachere Datenschema machen wir mithilfe von zwei Config-Dateien, die bei der Tilemaker-Software mitgeliefert werden ([config-openmaptiles.json](https://github.com/systemed/tilemaker/blob/master/resources/config-openmaptiles.json) und [process-openmaptiles.lua](https://github.com/systemed/tilemaker/blob/master/resources/process-openmaptiles.lua))
	* man kann hier auch eigene Configs verwenden, um ein eigenes Datenschema zu erhalten
	* das Datenschema muss aber später auch von dem Kartenrenderer bzw. dem Styling-System unterstützt werden; wir benutzen den Karten-Stil von [[https://github.com/FreifunkBremen/mapbox-studio-osm-bright.tm2]], der (nach einigen Anpassungen) zu der verwendeten openmaptiles-Config passt
	* und wir benutzen zusätzlich (für die Karte außerhalb von Deutschland) noch die Dateien von [[https://archive.org/details/osm-vector-mbtiles]], die ebenfalls dieses Datenschema verwenden; das passt also zum Glück zusammen.


## Anleitung

Diese Schritte müssen auf einem System ausgeführt werden, das genug Festplattenplatz (40 GB?) und RAM (ca. 30 GB) hat. Ich hab in dieser Anleitung mal angenommen, dass die ganze Prozedur auf unserem Jenkins-Server ausgeführt wird, als User "jenkins", im Verzeichnis ~/tiles/ .

* Software runterladen: [[https://github.com/systemed/tilemaker/releases/download/v2.0.0/tilemaker-ubuntu-16.04.zip]] und auspacken
* aktuelle Kartendaten für Deutschland runterladen, von [[https://download.geofabrik.de/europe/germany-latest.osm.pbf]]
	* für Tests kann man auch z.B. [[https://download.geofabrik.de/europe/germany/bremen-latest.osm.pbf]] runterladen; dann braucht man nur ca. 100 MB RAM
* [[https://archive.org/download/osm-vector-mbtiles/planet/2019-09-planet-10.mbtiles]] runterladen
	* das werden wir als niedrig aufgelöste Karte für die Welt außerhalb Deutschlands verwenden (das sind zwar etwas alte Daten; aber da stehen eh keine Knoten, und wir sparen dadurch viel Platz).
	* Hinweis: der Download von archive.org ist recht langsam
* Planet-Datei kopieren: `cp 2019-09-planet-10.mbtiles germany.mbtiles`
	* wir werden die Deutschland-Daten dann in die kopierte Datei dazuschreiben
* im Tilemaker-Verzeichnis ausführen: `./build/tilemaker --input germany-latest.osm.pbf --output germany.mbtiles --merge --store ./tmp/ --config resources/config-openmaptiles.json --process resources/process-openmaptiles.lua`
    * Hinweis: die kopierte `germany.mbtiles` muss so platziert sein, dass dieser Befehl dort hinein schreibt. Tilemaker soll keine neue `germany.mbtiles` anlegen!
    * in `./tmp/` werden dann temporäre Dateien für die Konvertierung abgelegt (ca. 30 GB). Das ist nur mit einer SSD sinnvoll! Die `--store`-Option kann auch weggelassen werden, aber dann benötigt der Prozess ca. 48 GB RAM.
* die fertige `germany.mbtiles` kann jetzt auf den Tileserver nach /home/tiles/germany.mbtiles kopiert werden
* auf dem Tileserver muss noch Tessera neugestartet werden:
	* `su - tiles`
	* `systemctl --user restart tessera.service`
