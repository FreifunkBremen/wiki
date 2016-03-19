**Wir bauen uns ein Image für den Offloader Fujitsu-Siemens Futro S550-2**

In den Freifunk-Foren werden viele interessante Themen um den Futro besprochen.
Um die benötigten Informationen nicht überall zusammensuchen zu müssen, hier
eine kleine Zusammenfassung für das Bremer Futro-Image.

1. Abschnitt: Die Hardware.

Fujitsu Siemens Futro S550-2.
Erste Informationen sind unter [https://forum.freifunk.net/t/f-a-q-zum-offloader-fujitsu-siemens-futro-s550/8294](https://forum.freifunk.net/t/f-a-q-zum-offloader-fujitsu-siemens-futro-s550/8294) zu finden.

Gerät öffnen: (Nur wenn eine 2te Netzwerkkarte eingebaut werden soll)
! Elektrostatische Aufladung kann das Gerät zerstören, unbedingt für ausreichnde Erdung sorgen.

Gerät auf die Seite legen, die Rückseite zu uns. Die **zwei **Schrauben **links **lösen. Die Schraube rechts bleibt im Gerät.
Für die Schrauben gibt es kein vernünftig passendes Werkzeug, also ausprobieren, welches am besten passt. Schrauben entfernen. Gehäusedeckel mit Frontblende ca. 1cm in Richtung Frontblende schieben. Leichte Schläge mit der Hand helfen beim lösen. Gehäusedeckel mit Frontblende nach oben abnehmen. Der Metallsteg in der Mitte bleibt festgeschraubt. An der Frontseite ist der Metallsteg nur eingesteckt. Um die Risercard einzusetzen, wird der Metallsteg angehoben, damit mehr Platz zum Einsetzen ist.
Netzwerkkarte mit kurzem Slotblech (1/2 Bauhöhe) einsetzten. Bei Netzwerkkarten mit langem Slotblech, dieses Kürzen und umbiegen. Das Slotblech wird später nur eingeklemmt. Bedingung für Karten mit langem Slotblech, diese müssen mit 3,3V funktionieren. 5V Karten sollen nicht funktionieren (bisher nicht getestet.)
Soll das Image per USB-Stick aufgespielt werden, kann das Gehäuse jetzt wieder zusammengebaut werden. Metallbügel auf richtigen Sitz kontrollieren und Gehäusedeckel einsetzten. Vor dem Zuschrauben, den Sitz der Netzwerkkarte kontrollieren und ggf. justieren, damit die LAN Buchse zugänglich ist. Das Gerät ist nun fertig, und das Image kann eingespielt werden kann.

2. Image einspielen.

Um ein Image aufzuspielen, gibt es mehrere Methoden. Die schnellste und eleganteste ist das Aufspielen mit einem USB-Stick. Einen USB-Stick mit folgendem Bootimage verwenden:
[https://forum.freifunk.net/t/einfache-loesung-um-einen-futro-s550-offloader-zu-flashen-windows-linux-os-x/8988](https://forum.freifunk.net/t/einfache-loesung-um-einen-futro-s550-offloader-zu-flashen-windows-linux-os-x/8988)
Ladet Euch das Gluon2Futro-USB-Stick-Image von GitHub herunter, und transferiert es auf einen USB-Stick ( mit 'dd' oder 'Win32 Disk Imager' oder 'Rufus'). Auf dem USB-Stick befindet sich danach ein Mini Linux auf einer FAT32 Partition. Der USB-Stick muss mind. 64MB groß sein. Alle bisher gespeicherte Daten auf dem USB-Stick gehen verloren!

Dann einfach euer gewünschtes Gluon-x86-Factory-Image (die gepackte Version *.img.gz) auf den vorbereiteten USB-Stick kopieren (das geht mit jedem Win/Linux/Mac PC per Datei-Manager des jeweiligen Betriebsystems). Wenn jetzt der Futro mit diesem USB-Stick gebootet wird, so wird das Gluon-x86-Image vollautomatisch auf die interne CF-Karte des Futros übertragen.

Es gibt nach ca. 20-60 Sekunden auf jeden Fall eine akustische Rückmeldung:
Alles okay = 5 x Piepen
Fehler = 10 Sekunden wildes Gepiepse

Bei dieser Aktion ist eine PS/2 Tastatur und ein Monitor mit DVI Stecker / Kabel erforderlich. Futro einschalten und mit F2 in das Setup. Bootreihenfolge auf den Stick einstellen und neu starten. Die Option F12 Bootreihenfolge einstellen, funktionierte bei mir nicht. Hin und wieder klappt das kopieren des Images nicht, dann einfach den Vorgang wiederholen. Der Futro bootet vom Stick und nach 10 Sekungen ist das Image eingespelt. Der Futro schaltet sich ab, jetzt den USB Stick entfernen. Falls Ihr ein Gluon-X86-Factory-Image mit CF-Karten-Unterstützung (in **v2016.1.2 **bereits enthalten) geflasht habt, so ist euer Futro S550 nach einem Neustart im Konfigurationsmodus und somit über http://192.168.1.1 zu erreichen.

P.S.
Wichtig ist, dass sich nur ein Gluon-x86-Image (die gepackte Version *.img.gz) auf dem vorbereiteten USB-Stick befindet!
Detaillierte Informationen findet Ihr auf [https://github.com/oszilloskop/Gluon2Futro32](https://github.com/oszilloskop/Gluon2Futro32)

P.S.S.
Bitte bootet keinen PC mit diesem USB-Stick. Eure Daten sind dann hinüber. Das Image wird ohne Nachfrage installiert.

Eine andere Methode ist das Einspielen mit einem CF-Cardreader. Bei dieser Aktion kann auch das Image, das auf der zweiten Partition auf der CF-Karte ist, mit Gpartet vergrössert werden. Das Filesystem ist auf 128Mb eingestellt. Bei grösseren Partitionen ist noch eine Datenträgerprüfung durchzuführen, damit das Filesystem die ganze Partition verwendet. Notwendig ist die Vergrösserung nicht, von dem 50 Mb Image ist nur die Hälfte belegt. Genug Platz für weitere Installationen. In dem restlichen Bereich kann auch eine zusätzliche Partition erstellt
werden, die dann später gemountet wird.
Im nächsten Kapitel bauen wir das Image selber.


