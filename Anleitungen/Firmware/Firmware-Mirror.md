# Firmware mirror
# Simple Lösung via Shellscript
Hier habe ich (ec8or) protokolliert, wie ich mit Hilfe von jplitza und wget einen Firmware-Mirror auf meinem Raspberry PI eingerichtet habe. Er ist nicht besonders clever, aber funktional. Ich bin keine Experte und hoffe durch diesen Artikel einen Anfang für eine gute Anleitung entstehen zu lassen. 

## Statische IP 
Al erstes muss der "Server" im Freifunk bekannt sein. Dazu habe ich mir eine IPv4 IP-Adresse im Artikel [Dienste](http://wiki.bremen.freifunk.net/Dienste/Home) reserviert und anschließend in /etc/network/interfaces hinterlegt.

```
auto eth0
iface eth0 inet static
  address 10.196.0.111
  netmask 255.255.128.0
  dns-nameservers 10.196.0.1 10.196.0.2 10.196.0.3 10.196.0.5
  gateway 10.196.0.1
```

Ein Firmware-Mirror muss aber per IPv6 erreichbar sein. Das letzte Byte der IPv6-Adresse sollte immer dem letzten Byte der Ipv4-Adresse entsprechen, in meinem Fall also **6f**. Dem entsprechen habe ich folgenden, weiteren Eintrag in der /etc/network/interfaces hinterlegt:

```
iface eth0 inet6 static
  address 2001:bf7:540::6f
  netmask 64
```

## Daten kopieren
Die Quelle für Spiegel-Server ist [http://downloads.bremen.freifunk.net/firmware/](http://downloads.bremen.freifunk.net/firmware/). Zum spiegeln habe ich folgedes "Script" erstellt. Ich protokolliere außerdem noch Start und Ende in eine Textdatei. Das hat mir das Testen erleichtert.

**Script**

```
#!/bin/bash

cd mirror-download

date > last-run.txt

wget -Nr -np -A .bin,.manifest -nH --cut-dirs=1 -X /firmware/nightly http://downloads.bremen.freifunk.net/firmware/

date >> last-run.txt

```

**Erläuterung**

* **-r** Verzeichnise rekursiv durchlaufen
* **-N** Nur neuere Dateien herunterladen
* **-np** no-parent (Nicht höher als /firmware/ gehen)
* **-A .bin,.manifest** Nur Dateien mit der Endeung **.bin,.manifest** herunterladen (muss noch Überarbeitet werden, es fehlen noch ein paar Dateien. z.B. MD5SUM, .gz, .img)
* **-nH** Kein Unterverzeichnis **downloads....** anlegen
* **--cut-dirs=1** kein Unterverzeichnis **firmware/** anlegen
* **-X ..nightly** Das Nightly-Verzeichnis ausschließen


Das Nightly-Verzeichniss wird ausgeschlossen, da es sich hierbei momentan (01.09.2015) nur ein symlink auf testing handelt. Diesen hab eich lokal angelegt um keinen unnötigen Traffic zu generieren. Sollten keine neuen Images vorhanden sein, kostet der Aufruf ca 850KB. Alle Images zusammen verbrauchen aktuell ca 850MB (01.09.2015).

Damit das Script ausgeführt werden kann, muss es natürlich zuvor mit `chmod +x script.sh` als ausführbar makiert werden.


## Cron-Jon einrichten
Damit das Script regelmäßig um 3:33Uhr ausgeführt wird, habe ich ein Eintrag in */etc/crontab* hinterlegt

33 3 * * * * username /pfad/zum/script.sh

Ob und wann ein Cronjob ausgeführt wird steht im syslog.

```
grep CRON /var/log/syslog
```

## Daten per HTTP bereitstellen
Die Knoten können die Images nur per HTTP abrufen. Da ich bisher keinen Webserver verwende, habe ich mich nach einer einfachen Lösung umgesehen und bin bei [WebFS](http://linux.bytesex.org/misc/webfs.html) gelandet. Ich habe das entsprechende [deb-Paket](https://packages.debian.org/jessie/webfs) installiert.

## Ausblick/Alternative vorgehensweise
das Herunterladen neuer Firmwaredateien ist eigentlich nur erforderlich, wenn das entsprechende Manifest geändert wurde. Man könnte also auch erst dieses herunterladen, prüfen ob es sich verändert hat und anschleißend ggf. die Images herunerladen. Im besten Fall könnte man so beim Spiegeln anhand des SHA512 und der Unterschriften aus dem Manifest überprüfen ob die Dateien korrekt sind. Damit könnte man sich davor schützen Ungültige-Daten herunterzuladen und zu verbreiten. Bei meiner Vorgehensweise würde kompromitierte Software fleißig weiterverteilt.

**Achtung**: Es tut sich was auf [github](https://github.com/FreifunkBremen/mirror) (2015-09-09).

# Erweiterte Lösung mit Python
Auf [github](https://github.com/FreifunkBremen/mirror) hatte corny ein paar python scripte gebaut die mir (ec8or) die implementierung erleichtert haben. Ich habe daraufhin einen eigenen (Branch)[https://github.com/FreifunkBremen/mirror/tree/koma] angelegt und das o.g. Shell-Script auf dem PI ersetzt.

Die Applikation hat folgende Eigenschaften:
* Sie legt einen Spiegel nur für "sysupgrade", also nur für Aktualisierungen an.
* Sie lädt stehts die neuste site.conf aus unserem Repo
* Die Signatur der Manifeste wird überprüft
* Sie lädt Images nur dann herunter, wenn sie sich geändert haben
* Die Hashes der Images werden geprüft
* Sie verfügt über einfaches logging

Inhalt:
* __mirror.py__: Steuert den Programmablauf
* __downloader.py__: Lädt Dateien herunter, prüft dabei den HTTP-Header _if-modified-since_ und lädt Dateien nur wenn dieser neuer, als der Zeitstempel eines bestehenden Images ist
* __gluon_manifest.py__: Ein Parser für *.manifest Dateien verifiziert die Signaturen
* __slpp.py__: Validator für ECDSA Signaturen, wird von gluon_manifest.py verwendet

