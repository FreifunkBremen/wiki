# SSH-Node-Verwaltung

## Vorbereitung

### Was ist SSH?

> Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP. Die IANA hat dem Protokoll den TCP-Port 22 zugeordnet.

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)

__Linux__

1. [Schlüssel erzeugen](https://help.github.com/articles/generating-ssh-keys/#step-2-generate-a-new-ssh-key)
1. [Schlüssel dem ssh-agent bekanntmachen](https://help.github.com/articles/generating-ssh-keys/#step-3-add-your-key-to-the-ssh-agent)
 

__Windows__
Putty, puttygen und pageant helfen einem hier weiter.

### Wie hinterlege ich SSH-Schlüssel im Node im Config-Modus über die Weboberfläche?

1. Klicke rechts oben auf Expert-Mode
2. Wähle als nächstes den Reiter "Remote Access" aus
3. kopiere den öffentlichen Teil deines SSH-Schlüssels in das Fenster. 
4. klicke unten auf "Submit"
5. Du hast nun erfolgreich den Schlüssel hinterlegt und kannst in Zukunft im laufenden Betrieb auf den Router zugreifen (von überall, solange du im Freifunk-Netz eingeloggt bist.)
 
 
## Möglichkeiten per Konsole
Alle folgenden Erklärungen und Befehle setzen voraus, dass bereits eine SSH-Verbindung zu dem gewünschten Node besteht.

Die folgende Wiki-Seite von gluon (unserer Firmware-Basis) enthält die meisten und wichtigsten Befehle: https://github.com/freifunk-gluon/gluon/wiki/Commandline-administration  
Diese Wiki-Seite versteht sich als Ergänzung der dort erklärten Befehle.

### Firmware automatisch per Autoupdater aktualisieren
Mit dem Befehl `autoupdater` lässt sich der Autoupdater manuell außerhalb der regulären Tasks aufrufen. Er funktioniert dann ganz normal und wird, wenn ein Update vorhanden ist, mit der gleichen, vom Server dem Knoten zugeteilten, Wahrscheinlichkeit updaten.  
Um ein Update zu erzwingen kann an den Befehl `-f` angehängt werden.  
Falls für einen einzelnen Autoupdater-Aufruf ein anderer Branch gewählt werden möchte kann `-b $BRANCHNAME` an den Befehl gehängt werden.

### Firmware manuell per Kommandozeile aktualisieren
Als erstes muss das Firmware-Image auf den Knoten geladen werden.
##### 1a. wget-Variante (remote Image)
Wechsle in das temporäre Verzeichnis des Knoten (`cd /tmp/`) und lade das Image herunter mit `wget [FIRMWAREURL]`.

##### 1b. scp-Variante (local Image)
Übertrage das lokale Image per scp in das `/tmp/`-Verzeichnis des Knoten, indem folgender Befehl auf dem eigenen Rechner ausgeführt wird:  
`scp [FIRMWAREDATEI] root@[ [IPv6-ADRESS] ]:/tmp/`

##### 2. sysupgrade ausführen
Führe folgende Befehle angepasst aus:
```
echo 3 > /proc/sys/vm/drop_caches
sysupgrade [FIRMWAREFILE]
```

### SSH-Key auf Node hinzufügen oder entfernen
Die Datei in der die erlaubten SSH-PublicKeys liegen, befindet sich in `/etc/dropbear/authorized_keys`. Zum Bearbeiten muss diese einfach in dem Editor der Wahl geöffnet werden.  
Beispiel: `vim /etc/dropbear/authorized_keys`
Nun kann ein weiterer Key in eine neue Zeile eingefügt werden oder ein bereits bestehender gelöscht werden.  
Nach dem Speichern kann man die Verbindung schließen und sich mit dem neuen Key verbinden.

### Node zurücksetzen
Wenn man mal etwas kaputt-konfiguriert hat lässt sich der Zustand "frisch-geflash" wie folgt wiederherstellen.

1. Der Befehl `firstboot` setzt alle Konfigurationen zurück. 
2. Anschließend startet man mit dem Befehl `reboot` neu. 
 
Der Node befindet sich jetzt im wieder im Config-Mode, wie beim ersten Start.