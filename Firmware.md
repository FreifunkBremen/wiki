## Benutzung

**ACHTUNG: Die Firmware ist noch im Entwicklungsstadium, Benutzung auf eigene Gefahr und nur von technisch versierten Benutzern!**

Jede Nacht werden bei Änderungen [Nightlies](https://wellenfunk.de/firmware/nightly/) gebaut, die man sich runterladen und flashen kann. Falls der Auto-Updater funktioniert (sollte er eigentlich) werden sie (früher oder später) auch automatisch auf den Router geladen, falls man vorher schon ne Nightly benutzt hat.

### Ersteinrichtung

Wenn man die Firmware das erste Mal auf einem Router installiert, muss man sich hinterher per Kabel mit einem beliebigen LAN-Port des Routers verbinden und auf seinem Rechner DHCP anmachen oder aber manuell eine Adresse aus dem Bereich 192.168.1.0/24 zuweisen und anschließend die auf [192.168.1.1](http://192.168.1.1/) im Browser zugreifen.

Dort beantwortet man ein paar grundlegende Fragen und bestätigt einmal. Dann zeigt der Browser ggf. den VPN-Key an, während der Router neustartet. Um diesen auf den VPN-Server zu übertragen, verbindet man sich wieder mit dem Internet (nicht über den Freifunk-Router!) und klickt dann auf den Link, der im Text über dem Schlüssel im Browser hoffentlich noch offen ist.

Danach läuft der Router im normalen Betrieb total abgeschottet: Weder per SSH noch per HTTP ist ein Zugriff möglich. Um die getroffenen Einstellungen nachträglich zu ändern, drückt man den Knopf des Routers 3-5 Sekunden lang. Er startet dann neu und ist wieder im Config-Modus, in dem man übrigens immer per telnet auf den Router kommt. Setzt man dort ein Passwort, kann man auch im normalen Betrieb per SSH auf den Router.

### Auto-Update

Wenn man bei der Erstinstallation das automatische Update aktiviert hat, prüft der Router einmal pro Stunde mit einer gewissen Wahrscheinlichkeit, ob ein neues Update verfügbar ist. Die Wahrscheinlichkeit dient der Entlastung des Servers, damit er nicht alle Anfragen aller Router auf einmal verarbeiten muss. Falls es dann eine neue Version gibt, wird diese installiert.

In späteren Phasen (testing und stable im Gegensatz zu nightly) müssen die Images erst von einem oder mehreren Entwicklern signiert werden, bevor die Router sie automatisch installieren.

## Entwicklung

Unsere Firmware basiert auf [gluon](https://github.com/freifunk-gluon/gluon), einem allgemein gehaltenem Framework der Lübecker. In unserem [github-Account](https://github.com/FreifunkBremen/) gibt es Forks falls wir etwas zu Patchen gefunden haben und vor allem die benötigte [site-Config](https://github.com/FreifunkBremen/gluon-site-ffhb).