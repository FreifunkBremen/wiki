**[RaspBerry-PiShrink](https://github.com/Drewsif/PiShrink)**

## Inhalt:
[[_TOC_]]

Wer öfter mit einem Raspberry arbeitet, kennt das Problem, schnell kaputtgespielt und kein passendes Backup-Image zur Hand.
Deshalb erstellen wir nach der Installation auch ein Backup-Image.
Mit dem Befehl dd erstellen wir ein Abbild der Micro-SD. Und da kommt die Frage auf, jedesmal ein Image in Größe der Micro-SD
und wie kommt das Image auf eine andere Micro-SD mit anderer Größe?
Vorab, es geht und es gibt mehrere Wege.

Ich möchte hier ein "Aber" oder einen anderen Standpunkt anmerken.
Bei den Freifunkern wird mit Images gearbeitet, die fest auf den Routerspeicher eingestellt sind.
Natürlich gibt es Ausnahmen, da einige Router einen großen Speicher haben oder durch Flash/Micro-SD Karten flexibel sind. Die Images sind nur so groß, wie sie benötigt werden.
Das ist auch beim Raspi der Fall. Da ziehe ich ein 256Mb Image auf eine 256Gb SD-Karte und habe 256Gb-256Mb Platz verschwendet.
Kein Problem Image ist schnell an die SD-Karte angepasst, ! bis ein Update erscheint und durch das Update ist unser Image wieder in den alten Grenzen.
Da hilft uns ein anderer Weg weiter, der freie Platz wird partitioniert und gemountet. Kann durch ein upgrade ebenfalls zerstört werden, ist jedoch mit Bordmitteln schnell gefixt.
Wer also mit festen Images konfrontiert wird, sollte auch andere Optionen in Betracht ziehen.


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

http://www.netzmafia.de/skripten/hardware/RasPi/SD_Karte_verkleinern.html

https://github.com/Drewsif/PiShrink

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**