# Varianten
## Branches
Branches definieren unterschiedliche Zustände innerhalb einer Software.

### Stable
Diese Software wird als stabil und funktionierend gewertet und wurde vorher auf Fehler getestet. Für die größte Einfachheit und Fehlerfreiheit, sollte dieser Branch verwendet werden.

### Testing
Testing-Software ist der letzte Schritt vor der generellen Veröffentlichung. Meist von einer größeren Anzahl von Benutzern betrieben werden so die letzten Fehler ermittelt und geschaut, ob die Firmware auch für den Stable-Branch genutzt werden kann. Meist finden sich hier die neusten Funktionen, Sicherheits- und Stabilitätsupdates ohne, dass man große Sorgen um schwerwiegende Fehler haben muss.

Unsere Testing-Builds basieren immer auf Gluon-Releases.

### Nightly
Nightly, (automatisch) nächtlich erstellte, Software ist sehr nah an experimenteller Software. Sie dient zum ersten breiten Testen von neuen Funktionen und hilft beim Ausmerzen von Fehlern. Wer die Arbeit der Entwickler unterstützen möchte, kann diese Variante wählen und regelmäßig Feedback geben.  
Nightly-Firware-Builds werden von Freifunk Bremen im Moment **nicht** genutzt. Der Aufwand war für den Nutzen zu groß. Im Nightly-Verzeichnis liegen Symbol-Links auf den Testing-Branch.

### Experimental/exp
Diese Software ist **hoch experimentell**! Sie ist **nicht** für den normalen Betrieb gedacht. Diese Variante wird meist nur zum direkten Testen von gerade entwickelten Änderungen (bleeding edge) verwendet. Sie wird von jedem Entwickler selbst kompiliert.


## Factory vs. Sysupgrade
Von jeder kompilierten Version der Firmware gibt es ein Factory- und ein Sysupgrade-Image.

### Factory
Diese Image muss verwendet werden, wenn auf dem Knoten noch die originale Hersteller-Firmware (Stock-Firmware) ist. Sie nimmt die erstmalige Installation von OpenWRT mit Gluon und den Community-spezifischen Einstellungen vor.

### Sysupgrade
Dieses Image ist für das Updaten von Geräten gedacht, welche bereits mit dem Factory-Image bespielt wurden. Es ist spezifisch für das Update innerhalb von OpenWRT gedacht und kann nicht anders verwendet werden. Dieses Image wird vom Autoupder verwendet.