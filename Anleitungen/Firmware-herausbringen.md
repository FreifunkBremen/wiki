# neue Firmware herausbringen
Wenn eine neue offizielle Firmware herausgebracht wird, sollten folgende Schritte durchlaufen und abgearbeitet werden.
[[_TOC_]]
### Änderungen an Firmware auf der Mailingliste oder einem Treffen besprechen und informieren
### [Tag/Release im Repository anlegen](Firmware-Release-anlegen)
### Firmware bauen
### Changelog aktualisieren
Im [Firmware-Changelog](http://wiki.bremen.freifunk.net/Firmware/Changelog) sollte ein neuer Absatz für die neue Version angelegt werden, der die wichtigsten Änderungen auflistet.

### Firmware testen
#### Testing
Auf dem [Treffen vom 06.05.2016](http://wiki.bremen.freifunk.net/Treffen/2016_05_06#protokoll_firmware) wurde festgelegt, dass die Anforderungen zum Releasen einer neuen Firmware auf dem Testing-Branch, so simpel wie möglich sein sollten. So soll ermöglicht werden, dass neue Änderungen schnell getestet werden können und der Aufwand für die Verantwortlichen möglichst gering bleibt.

Deshalb müssen keine expliziten Tests durchgeführt werden, werden aber immer begrüßt. Den Freifunkern, welche Zugriff auf den Downloadserver haben, wird ein gewisses Maß an Vertrauen entgegengebracht.

Jeder der seinen Knoten auf den Testing-Updatebranch einstellt, sollte sich bewusst sei, dass es sich um evtl. nicht fertige und fehlerbehaftete Software handelt.

#### Stable
Um eine Firmware mit seiner Signatur als Stable zu markieren, sollten ein paar wenige grundlegende Tests, auf mindestens einem Knoten, getätigt werden:

- Tests:
    - SSID `bremen.freifunk.net` sichtbar?
    - kann man sich verbinden?
    - bekommt man eine IP?
    - kann eine Verbindung zu einem Gateway aufgenommen werden?
    - sind Geräte/Dienste im Freifunk aufrufbar?
    - sind Inhalte aus dem Internet aufrufbar?
    - meshed der Knoten mit einem anderen?
    - [wurde ein Standard-SSH-Key in die Firmware integriert?](http://wiki.bremen.freifunk.net/Anleitungen/SSH-Node-Verwaltung#m%C3%B6glichkeiten-per-konsole_ssh-key-auf-node-hinzuf%C3%BCgen-oder-entfernen)
- erwünschte Tests:
    - Knoten taucht in der Knotenkarte auf, mit min. einem Client 

Die neue Firmware sollte mindestens auf folgenden Modellen getestet werden, bevor sie online geht:
* WR841N(D) v9
* WDR3600 oder WDR4300
* beliebiges Ubiquity-Gerät (z.B. Nanostation)

Da die meisten dieser Tests durch die Community-Teilnehmer mit Geräten auf dem Testing-Updatebranch automatisch durchgeführt werden, reicht es aus 3 Wochen nach dem Release davon auszugehen, dass die Firmware stabel ist, falls keine Fehlerberichte erhalten wurden.

### [[Firmware signieren|Firmware-signieren]]
### Firmware auf Download-Server hinterlegen
### Blogpost herausbringen
Nicht nur die Freifunker auf der Liste, sondern auch die Öffentlichkeit und alle Interessierten sollten wissen, dass es eine neue Firmware gibt. Ein neuer Blogpost wird automatisch über Twitter und Facebook geteilt, sowie an die Mailingliste geschickt, wodurch es überflüssig ist, sie erneut zu informieren.