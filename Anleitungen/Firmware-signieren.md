# Firmware signieren
Das signieren der Firmware ist nötig, damit der autoupdater auf den Knoten die neue Firmware akzeptiert. So sichergestellt, dass nur befugt Personen eine neue Firmware aufspielen.  
Im Endeffekt wird aber gar nicht die Firmware signiert, sondern das dazugehörige Manifest, in welchem der Branch, das Startdatum zum Ausrollen, der Zeitraum über den das Ausrollen gestreckt werden soll, sowie Links mit Hash zu den Firmware-Images hinterlegt sind.

Aktuell sind für den Testing Branch eine und für den Stable Branch 2 gültige Signaturen nötig.  
Welche Signatur akzeptiert wird, ist fest in der Firmware verbaut. Fals in neuen Versionen Schlüssel von neuen Personen dazukommen und diese verwendet werden, kann es sein, dass ein Gerät mit älterer Firmware, die neue Firmware nicht installiert, da es die Signatur nicht verifizieren kann.

## nötige Tests
Um eine Firmware mit seiner Signatur als veröffentlichungs-würdig zu markieren, sollten ein paar wenige grundlegende Tests, auf mindestens einem Knoten, getätigt werden, bevor sie auf dem Testing Branch im größeren, verteilten Test sich beweisen muss:


- SSID `bremen.freifunk.net` sichtbar?
- kann man sich verbinden?
- bekommt man eine IP?
- kann eine Verbindung zu einem Gateway aufgenommen werden?
- sind Geräte/Dienste im Freifunk aufrufbar?
- sind Inhalte aus dem Internet aufrufbar?
- wurde ein Standard-SSH-Key in die Firmware integriert?

Diese Ergbenisse, sollten mit dem getesteten Knoten, als Antwort auf die Signing-Anfrage, mit Signatur, bei Erfolg, zurückgeschickt werden.

Zusätzlich, solle man sich ein mal mit den Änderungen zur letzten Firmware vertraut machen, entweder durch die in der Singing-Anfrage bereitgestellte Zusammenfassung, in den [Tags/Releases bei Github](https://github.com/FreifunkBremen/gluon-site-ffhb/releases) oder im [[Changelog|/Firmware/Changelog]], falls es bereits für die Version einen Eintrag gibt.


## technische Vorraussetzungen
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