## Ubuntu auf eine RspBerry installieren

(27.8.2021 F_H) Die folgenden Spielereien dienen der Unterhaltung und Bildung. 
Der Artikel beschreibt einen Versuch, Ubuntu auf einem Raspberry zu Installieren.
Und **Achtung**. Es ist ein **Fehlschlag**.

## Inhalt
[[_TOC_]]


Hier sind also nur ein paar _Stolpersteine_ erwähnt, die unserer `Aufmerksamkeit` bedürfen! Es kann verallgemeinert gesagt werden: Ubuntu und Raspberry kann funktionieren, ist jedoch relativ schlecht dokumentiert. Für normale Installationen gibt es ein Prima Wiki und entsprechende Foren, für den Raspberry ist es das auf Debian basierte Raspbian.
Die Probleme meiner Ubuntu Installation konnten für den Raspbian nicht gelöst oder genauer beschrieben werden.



Eine wichtige Quelle ist: https://www.raspberrypi.org/documentation/


### Vorbereitung
teil: bei Netzteilen < 5,1V ist ein Raspi Hack erforderlich [(s.u.)](#netzteil)
- Gehäuse: von Formschön bis Wasserdicht alles möglich.


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Pi Imager

Die weiteren Konfigurationen im Terminal mit sudo `raspi-config` vornehmen.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### Erstinstallation Hinweise
Image auf Micro-SD Karte schreiben. -> 2 Partitionen /boot & /rootfs & freier Platz je nach SD Größe.
2 Varianten: mit gParted das rootfs vergrößern oder neue Partition anlegen, die später gemounted wird. Beide Varianten haben ihre Vor- und Nachteile. Die bessere Lösung ist die neue Partition einzuhängen. Zum Spielen und Programme installieren ist die Variante 1 besser, da die Partition mit /rootfs im Neuzustand bereits fast voll ist.
Wenn die SD Karte gerade noch im Lesegerät steckt, gleich die Einstellugen für Netzteil, Monitor und serielle Konsole in die `/boot/config.txt` eintragen, leere Datei ssh anlegen (aktiviert den SSH Zugang).

Natürlich können die Grudeinstellungen auch in der Image-Datei vorgenommen werden. Unter Windows evtl. mit dem Tool https://www.winimage.com/ das Image Bearbeiten.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**
