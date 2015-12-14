# Firmware signieren
Das signieren der Firmware ist nötig, damit der autoupdater auf den Knoten die neue Firmware akzeptiert. So sichergestellt, dass nur befugt Personen eine neue Firmware aufspielen.  
Im Endeffekt wird aber gar nicht die Firmware signiert, sondern das dazugehörige Manifest, in welchem der Branch, das Startdatum zum Ausrollen, der Zeitraum über den das Ausrollen gestreckt werden soll, sowie Links mit Hash zu den Firmware-Images hinterlegt sind.

Aktuell sind für den Testing Branch eine und für den Stable Branch 2 gültige Signaturen nötig.  
Welche Signatur akzeptiert wird, ist fest in der Firmware verbaut. Fals in neuen Versionen Schlüssel von neuen Personen dazukommen und diese verwendet werden, kann es sein, dass ein Gerät mit älterer Firmware, die neue Firmware nicht installiert, da es die Signatur nicht verifizieren kann.

## Vorraussetzungen
* ecdsautils
  https://github.com/tcatm/ecdsautils
  * libuecc
    http://git.universe-factory.net/libuecc

Wie diese installiert werden, kann hier nachgelesen werden: https://wiki.freifunk.net/ECDSA_Util

## Signieren
Zum Signieren benutzen wird die `sign.sh` im Verzeichnis `contrib` des Gluon-Repositories.  
Wenn man das Repository für die Bremer Firmware gecloned hat und sich darin befindet, lässt sie sich mit `gluon/contrib/sign.sh` aufrufen.

Die `sign.sh` wird wie folgt verwendet: `sign.sh <secret> <manifest>`

Beispiel:
```
$ gluon/contrib/sign.sh ~/.ecdsakey gluon/images/sysupgrade/stable.manifest
```
Der Grund warum das `sign.sh`-Skript zu verwenden besser ist, als nur das `ecdsasign`-Programm, ist wie folgt:  
Das Skript sorgt dafür, dass nur die wichtigen Elemente im Manifest signiert werden und die Signatur sinnvoll hinzugefügt wird. Ohne diese Vorkehrung, würde eine 2. Signatur, mit dem selben Key, anders aussehen, da sie die bereits hinterlegte mitsignieren würde.