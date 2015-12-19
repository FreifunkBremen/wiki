# neue Firmware herausbringen
Wenn eine neue offizielle Firmware herausgebracht wird, sollten folgende Schritte durchlaufen und abgearbeitet werden.
[[_TOC_]]
### Änderungen an Firmware auf der Mailingliste oder einem Treffen besprechen und informieren
### [[Tag/Release im Repository anlegen|/Firmware/Firmware-Release-anlegen]]
### Firmware bauen
### Firmware testen
Um eine Firmware mit seiner Signatur als veröffentlichungs-würdig zu markieren, sollten ein paar wenige grundlegende Tests, auf mindestens einem Knoten, getätigt werden, bevor sie auf dem Testing Branch im größeren, verteilten Test sich beweisen muss:

- nötige Tests:
    - SSID `bremen.freifunk.net` sichtbar?
    - kann man sich verbinden?
    - bekommt man eine IP?
    - kann eine Verbindung zu einem Gateway aufgenommen werden?
    - sind Geräte/Dienste im Freifunk aufrufbar?
    - sind Inhalte aus dem Internet aufrufbar?
    - meshed der Knoten mit einem anderen?
    - wurde ein Standard-SSH-Key in die Firmware integriert?
- erwünschte Tests:
    - Knoten taucht in der Knotenkarte auf, mit min. einem Client 

Diese Ergbenisse, sollten mit dem getesteten Knoten, als Antwort auf die Signing-Anfrage, mit Signatur, bei Erfolg, zurückgeschickt werden.

Zusätzlich, solle man sich ein mal mit den Änderungen zur letzten Firmware vertraut machen, entweder durch die in der Singing-Anfrage bereitgestellte Zusammenfassung, in den [Tags/Releases bei Github](https://github.com/FreifunkBremen/gluon-site-ffhb/releases) oder im [[Changelog|/Firmware/Changelog]], falls es bereits für die Version einen Eintrag gibt.

### [[Firmware signieren|Firmware-signieren]]
### Firmware auf Download-Server hinterlegen
Die neue Firmware sollte mindestens auf folgenden Modellen getestet werden, bevor sie online geht:
* WR841N(D) v9
* WDR3600 oder WDR4300
* beliebiges Ubiquity-Gerät (z.B. Nanostation)

### Changelog aktualisieren
Im [Firmware-Changelog](http://wiki.bremen.freifunk.net/Firmware/Changelog) sollte ein neuer Absatz für die neue Version angelegt werden, der die wichtigsten Änderungen auflistet.

### Blogpost herausbringen
Nicht nur die Freifunker auf der Liste, sondern auch die Öffentlichkeit und alle Interessierten sollten wissen, dass es eine neue Firmware gibt. Ein neuer Blogpost wird automatisch über Twitter und Facebook geteilt, sowie an die Mailingliste geschickt, wodurch es überflüssig ist, sie erneut zu informieren.