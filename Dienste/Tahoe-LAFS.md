# Tahoe-LAFS

## Idee

Tahoe-LAFS stellt ein verteiltes, zuverlässiges und verschlüsseltes Dateisystem bereit.

## Umsetzung

Im Netzwerk laufen einige Knoten, die Speicherplatz zur Verfügung stellen und beliebige Daten speichern und bereitstellen. Über Tahoe-LAFS-Clients können nun Daten in diese Wolke geschoben werden. Diese werden dabei auf dem lokalen Client verschlüsselt und redundant im Netzwerk ablegt.

## Vorteile

Durch die Redundanz können auf Tahoe-LAFS-Knoten ausfallen und trotzdem bedeutet das nicht direkt Datenverlust. Standardmäßig benötigt man ca. 3 von 10 Teilen einer Datei, damit diese dann wieder korrekt zusammen gesetzt werden kann.

Durch das verschlüsselte Ablegen der Daten ist sichergestellt, dass die Betreiber der Knoten selbst nicht wissen, was sie da speichern und nicht darauf zugreifen können.

## Benutzung

Auch zum Erweitern der Speicherkapazität dieser Cloud muss man einen eigene Tahoe-LAFS-Knoten betreiben - und es wäre schön, dass wer viel hochlädt, dies auch tut und mindestens genauso viel wieder zurück gibt.

## Notwendige Software und Einstellungen

Zum Betrieb eines Tahoe-LAFS-Knotens muss von die Datei https://tahoe-lafs.org/source/tahoe-lafs/releases/allmydata-tahoe-1.10.0.zip herunter geladen werden, wenn die aktuelle Version 1.10 nicht im jeweiligen Repository der Distribution. Diese muss dann entpackt werden. Mit python2 setup.py build && sudo python2 setup.py install bauen und installieren.

Vor dem ersten Start wird ein Tahoe-LAFS-Knoten mit bin/tahoe create-node oder mit bin/tahoe create-client ein reiner Client (ohne eigenen Storage) erzeugt. Dabei wird ein .tahoe-Ordner im home-Verzeichnis angelegt. In dessen tahoe.cfg-Datei muss dann noch unter introducer.furl ein Link zu unserer Wolke eingefügt werden:

introducer.furl = pb://rzovwxeiykc6f6usyhqphpyn4nik5nzt@introducer.tahoe-lafs.services.ffhb:44411/introducer

Mit bin/tahoe start wird der lokale Knoten dann gestartet.

## Verwendung

Wenn der lokale Knoten läuft, kann man dessen Web-interface mit einem beliebigen Browser über http://localhost:3456 erreichen. In diesem ist die Bedienung recht intuitiv.

## Weitere Infos

Unter https://tahoe-lafs.org sind nähere Informationen verfügbar.