## Benutzung

**ACHTUNG: Die Firmware ist noch im Entwicklungsstadium, Benutzung auf eigene Gefahr und nur von technisch versierten Benutzern!**

Jede Nacht werden bei Änderungen [Nightlies](http://downloads.bremen.freifunk.net/firmware/nightly/) gebaut, die man sich runterladen und [flashen](Firmware-flashen) kann. Falls der Auto-Updater funktioniert (sollte er eigentlich) werden sie (früher oder später) auch automatisch auf den Router geladen, falls man vorher schon eine Nightly benutzt hat.

### Ersteinrichtung/Config-Mode

Wenn man die Firmware das erste Mal auf einem Router installiert, startet der Router im sog. Config-Mode, in den man den Router später auch wieder bringen kann indem man den Knopf 3-5 Sekunden lang drückt. In diesem Modus muss man sich per Kabel mit einem beliebigen LAN-Port des Routers verbinden und auf seinem Rechner DHCP anmachen oder aber manuell eine Adresse aus dem Bereich 192.168.1.0/24 zuweisen und anschließend die auf [192.168.1.1](http://192.168.1.1/) im Browser zugreifen.

Dort beantwortet man ein paar grundlegende Fragen, setzt falls gewünscht ein Passwort per Telnet und bestätigt einmal. Dann zeigt der Browser ggf. den VPN-Key an, während der Router neustartet. Um diesen auf den VPN-Server zu übertragen, verbindet man sich wieder mit dem Internet (nicht über den Freifunk-Router!) und klickt dann auf den Link, der im Text über dem Schlüssel im Browser hoffentlich noch offen ist. Außerdem muss man ein LAN-Kabel mit Internetzugang (also einem laufenden DHCP-Server) in den WAN-Port des Routers stecken, damit dieser den VPN-Server erreicht.

Danach läuft der Router im normalen Betrieb standardmäßig total abgeschottet: Weder per SSH noch per HTTP ist ein Zugriff möglich. Um die getroffenen Einstellungen nachträglich zu ändern, drückt man wie eingangs erwähnt den Knopf des Routers 3-5 Sekunden lang. Er startet dann neu und ist wieder im Config-Modus. Hat man im Config-Mode jedoch ein Passwort gesetzt, kann man im normalen Betrieb per SSH auf den Router.

### Auto-Update

Wenn man bei der Erstinstallation das automatische Update aktiviert hat, prüft der Router einmal pro Stunde mit einer gewissen Wahrscheinlichkeit, ob ein neues Update verfügbar ist. Die Wahrscheinlichkeit dient der Entlastung des Servers, damit er nicht alle Anfragen aller Router auf einmal verarbeiten muss. Falls es dann eine neue Version gibt, wird diese installiert.

In späteren Phasen (testing und stable im Gegensatz zu nightly) müssen die Images erst von einem oder mehreren Entwicklern signiert werden, bevor die Router sie automatisch installieren.

## Entwicklung

Unsere Firmware basiert auf [gluon](https://github.com/freifunk-gluon/gluon), einem allgemein gehaltenem Framework der Lübecker. In unserem [github-Account](https://github.com/FreifunkBremen/) gibt es Forks falls wir etwas zu Patchen gefunden haben und vor allem die benötigte [site-Config](https://github.com/FreifunkBremen/gluon-site-ffhb).