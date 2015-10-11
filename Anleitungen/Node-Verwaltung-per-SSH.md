# Node-Verwaltung per SSH
## Vorbereitung
### Erklärung von SSH
### Hinterlegen des SSH-Key im Node im Config-Modus über die Weboberfläche

## Möglichkeiten per Konsole
Alle folgenden Erklärungen und Befehle setzen voraus, dass bereits eine SSH-Verbindung zu dem gewünschten Node besteht.

### Autoupdater aufrufen
Mit dem Befehl `autoupdater` lässt sich der Autoupdater manuell außerhalb der regulären Tasks aufrufen. Er funktioniert dann ganz normal und wird, wenn ein Update vorhanden ist, mit der gleichen, vom Server dem Knoten zugeteilten, Wahrscheinlichkeit updaten.  
Um ein Update zu erzwingen kann an den Befehl `-f` angehängt werden.  
Falls für einen einzelnen Autoupdater-Aufruf ein anderer Branch gewählt werden möchte kann `-b $BRANCHNAME` an den Befehl gehängt werden.

### SSH-Key auf Node hinzufügen oder entfernen
Die Datei in der die erlaubten SSH-PublicKeys liegen, befindet sich in `/etc/dropbear/authorized_keys`. Zum Bearbeiten muss diese einfach in dem Editor der Wahl geöffnet werden.  
Beispiel: `vim /etc/dropbear/authorized_keys`
Nun kann ein weiterer Key in eine neue Zeile eingefügt werden oder ein bereits bestehender gelöscht werden.
__Tipp: Es empfiehlt sich eine leere Zeile nach dem letzten Key zu lassen, um nicht jedes Mal ans Ende der Keys springen zu müssen.__
Nach dem Speichern kann die Verbindung geschlossen werden und man kann sich mit dem neuen Key verbinden.

### Node zurücksetzten
Wenn man mal etwas kaputt-konfiguriert hat lässt sich der Zustand "frisch-geflash" wie folgt wiederherstellen.

1. Der Befehl `firstboot` setzt alle Konfigurationen zurück. 
2. Anschließend startet man mit dem Befehl `reboot` neu. 
 
Der Node befindet sich jetzt im wieder im Config-Mode, wie beim ersten start.