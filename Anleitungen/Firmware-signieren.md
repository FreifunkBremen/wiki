# Firmware signieren (technisch)
Das Signieren der Firmware ist nötig, damit der Autoupdater auf den Knoten die neue Firmware akzeptiert. So ist sichergestellt, dass nur befugte Personen eine neue Firmware bereitstellen können.  
Im Endeffekt wird aber gar nicht die Firmware signiert, sondern das dazugehörige Manifest, in welchem der Branch, das Startdatum zum Ausrollen, der Zeitraum über den das Ausrollen gestreckt werden soll, sowie Links mit Hash zu den Firmware-Images hinterlegt sind.

Aktuell sind für den Testing-Branch eine und für den Stable-Branch zwei gültige Signaturen nötig.  
Welche Signatur akzeptiert wird, ist fest in der Firmware verbaut (konfiguriert in der [site.conf](https://github.com/FreifunkBremen/gluon-site-ffhb/blob/master/site.conf) im Abschnitt "autoupdater"). Falls in neuen Versionen Schlüssel von neuen Personen dazukommen und diese verwendet werden, kann es sein, dass ein Gerät mit älterer Firmware die neue Firmware nicht installiert, da es die Signatur nicht verifizieren kann.

## Manifest-Dateien
Für eine neue Testing-Firmware wird die Datei [firmware/testing/sysupgrade/testing.manifest](https://downloads.bremen.freifunk.net/firmware/testing/sysupgrade/testing.manifest) signiert.

Für eine Stable-Firmware wird die Datei [firmware/testing/sysupgrade/stable.manifest](https://downloads.bremen.freifunk.net/firmware/testing/sysupgrade/stable.manifest) signiert, und später wird dann der "stable"-Link unter [firmware/](https://downloads.bremen.freifunk.net/firmware/) umgesetzt, so dass die alte Testing-Version dann als Stable gefunden wird.

## Technische Voraussetzungen
* ecdsautils  
  https://github.com/tcatm/ecdsautils
  * libuecc  
    http://git.universe-factory.net/libuecc

Wie diese installiert werden, kann hier nachgelesen werden: https://wiki.freifunk.net/ECDSA_Util

Manche Linux-Distros bieten die ecdsautils auch schon als Paket an, z.B. ist die Installation unter Debian und Ubuntu dadurch einfach:
```
sudo apt-get install ecdsautils
```

## Signieren
Zum Signieren benutzen wir die `sign.sh` im Verzeichnis `contrib` des [Gluon-Repositories](https://github.com/freifunk-gluon/gluon).  
Wenn man das [Repository für die Bremer Firmware](https://github.com/FreifunkBremen/gluon-site-ffhb) gecloned hat und sich darin befindet, lässt sie sich mit `gluon/contrib/sign.sh` aufrufen.

Die `sign.sh` wird wie folgt verwendet: `sign.sh <secret> <manifest>`

Beispiel:
```
$ gluon/contrib/sign.sh ~/.ecdsakey gluon/images/sysupgrade/stable.manifest
```
Der Grund, warum das `sign.sh`-Skript zu verwenden besser ist, als nur das `ecdsasign`-Programm, ist wie folgt:  
Das Skript sorgt dafür, dass nur die wichtigen Elemente im Manifest signiert werden und die Signatur sinnvoll hinzugefügt wird. Ohne diese Vorkehrung würde eine zweite Signatur, mit dem selben Key, anders aussehen, da sie die bereits hinterlegte mitsignieren würde.