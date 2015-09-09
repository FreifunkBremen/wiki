# Node-Verwaltung per SSH
## Vorbereitung
### Erklärung von SSH
### Hinterlegen des SSH-Key im Node im Config-Modus über die Weboberfläche

## Möglichkeiten per SSH
Alle folgenden Erklärungen und Befehle setzen voraus, dass bereits eine SSH-Verbindung zu dem gewünschten Node besteht.
### SSH-Key auf Node hinzufügen oder entfernen
Die Datei in der die erlaubten SSH-PublicKeys liegen, befindet sich in `/etc/dropbear/authorized_keys`. Zum Bearbeiten muss diese einfach in dem Editor der Wahl geöffnet werden.  
Beispiel: `vim /etc/dropbear/authorized_keys`
Nun kann ein weiterer Key in eine neue Zeile eingefügt werden oder ein bereits bestehender gelöscht werden.
###### Tipp: Es empfiehlt sich eine leere Zeile nach dem letzten Key zu lassen, um nicht jedes Mal ans Ende der Keys springen zu müssen.
Nach dem Speichern kann die Verbindung geschlossen werden und man kann sich mit dem neuen Key verbinden.