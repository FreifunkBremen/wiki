**[RaspBerry-PiShrink](https://github.com/Drewsif/PiShrink)**

## Inhalt:
[[_TOC_]]

Wer öfter mit einem Raspberry arbeitet, kennt das Problem, der ist schnell mal kaputtgespielt.

Hier geht es darum, ein komprimiertes Backupimage zu erstellen.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

#### Raspberry Pi Images schrumpfen

Nehmen wir an, man hat einen Raspberry Pi mit einer SD-Karte mit 256 GB komplett eingerichtet und will ein Image erstellen um dies auf andere Raspberry Pi zu installieren. 
Die meisten Nutzer werden hierfür Befehle wie 
~~~
dd if=/dev/mmcblk0 of=/home/username/raspberry.img bs=4M
~~~ 
nutzen. Das ist einfach, hat den Nachteil, dass die
Image-Datei ist 256 GB groß ist, egal wie viel Speicherplatz tatsächlich genutzt wird. Auch wenn Speicherplatz nicht mehr sehr teuer ist verschwendet man diesen in dem Fall. 
Man müsste das Image also schrumpfen. Was manuell durchaus machbar ist. Oder man nutzt PiShrink.

Damit lassen sich mittels dd erstellt Image-Dateien auf die tatsächlich genutzte Größe schrumpfen. Also nicht belegter Platz wird entfernt.
Hierfür reicht der einfach Befehl pishrink.sh rasberry.img aus.

Erstelle man nun mittels dd den Inhalt des geschrumpften Image auf eine andere SD-Karte und bootet von dieser, passen sich die Partitionen automatisch an die größe der SD-Karte an, 
so dass der gesamte Speicherplatz zur Verfügung steht. Hierfür baut PiShrink einen entsprechenden Befehl in die Image-Datei ein.
Berichte zu PiShrink finden sich zu genüge, einfach mal Nachlesen.

Einige Links zum Thema:

[http://www.netzmafia.de/skripten/hardware/RasPi/SD_Karte_verkleinern.html](http://www.netzmafia.de/skripten/hardware/RasPi/SD_Karte_verkleinern.html)

[https://github.com/Drewsif/PiShrink](https://github.com/Drewsif/PiShrink)

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**