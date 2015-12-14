# Node-Verwaltung per SSH

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

_TODO: Informationen hinzufügen._

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
##### wget-Variante (remote Image)
Wechsle in das temporäre Verzeichnis des Knoten (`cd /tmp/`) und lade das Image herunter mit `wget [FIRMWAREURL]`.

##### scp-Variante (local Image)
Übertrage das lokale Image per scp in das `/tmp/`-Verzeichnis des Knoten:  
`scp [FIRMWAREDATEI] root@[ [IPv6-ADRESS] ]:/tmp/`

##### sysupgrade ausführen
Führe folgende Befehle angepasst aus:
```
echo 3 > /proc/sys/vm/drop_caches
sysupgrade [FIRMWAREFILE]
```

### SSH-Key auf Node hinzufügen oder entfernen
Die Datei in der die erlaubten SSH-PublicKeys liegen, befindet sich in `/etc/dropbear/authorized_keys`. Zum Bearbeiten muss diese einfach in dem Editor der Wahl geöffnet werden.  
Beispiel: `vim /etc/dropbear/authorized_keys`
Nun kann ein weiterer Key in eine neue Zeile eingefügt werden oder ein bereits bestehender gelöscht werden.
__Tipp: Es empfiehlt sich eine leere Zeile nach dem letzten Key zu lassen, um nicht jedes Mal ans Ende der Keys springen zu müssen.__
Nach dem Speichern kann die Verbindung geschlossen werden und man kann sich mit dem neuen Key verbinden.

### Node zurücksetzen
Wenn man mal etwas kaputt-konfiguriert hat lässt sich der Zustand "frisch-geflash" wie folgt wiederherstellen.

1. Der Befehl `firstboot` setzt alle Konfigurationen zurück. 
2. Anschließend startet man mit dem Befehl `reboot` neu. 
 
Der Node befindet sich jetzt im wieder im Config-Mode, wie beim ersten Start.


### PoE-Passthrough für CPE210/510 - permantent und rebootfest
Um PoE-Passthrough auf einem Gerät permanent zu aktivieren, unabhängig von Neustarts, muss ein kleines Skript im Node hinterlegt werden.

Bei bestehender SSH-Verbindung wechsle man in das Verzeichnis `cd /etc/init.d/`.

Dort wird per wget das Skript geladen: `wget http://simjost.andromeda.hostedinspace.de/poe`.  
Falls die Datei nicht verfügbar sein sollte, dann erstellt sie direkt mit:
```
cat poe
#!/bin/sh /etc/rc.common
# Enables PoE Passthrough on TL-CPE2XX/CPE5XX
# http://wiki.openwrt.org/toh/tp-link/tl-cpe210#poe_passthrough

START=10
STOP=15

start() {
  echo 20  > /sys/class/gpio/export
  echo out > /sys/class/gpio/gpio20/direction
  echo 1   > /sys/class/gpio/gpio20/value
}

stop() {
  echo 0   > /sys/class/gpio/gpio20/value
}

```

Damit dieses auführbar ist, müssen noch die Berechtigungen geändert werden: `chmod +x poe`.

Führe die folgenden Befehle aus um das Skript dauerhaft zu aktivieren und einmalig manuell zu starten:
```
/etc/init.d/poe enable
/etc/init.d/poe start
```