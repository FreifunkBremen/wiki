## Inhalt

[[_TOC_]]

### 1.) Pretest der Firmware 2023.1

Die neue Testting liegt auf dem Downloadserver unter: https://downloads.bremen.freifunk.net/firmware/all/2023.1+bremen1/sysupgrade/

Die neue Testing muss von Hand installiert werden.
1.) Herunterladen der Firmware vom Server (Also die, die auf meinen Router passt)
2.) SSH Verbindung zu meinem Router herstellen oder über die Oberfläche aus dem Konfigmode.
3.) SW Aktivieren
4.) freuen und mit dem neuen Router spielen.

Ein Upgrade auf v2023 benötigt min v2021 (aktuelle Stable).

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 2.) Update von ubnt-erx-sfp (Solved: wrong usage)

sysupgrade-ubnt-erx-sfp kein passendes Image da neuer Name gluon-ffhb-2023.1+bremen1-ubiquiti-edgerouter-x-sfp-sysupgrade.bin statt
gluon-ffhb-2021.1.2+bremen1-ubnt-erx-sfp-sysupgrade.bin mit neuer Versionsnummer. Image wird nicht akzeptiert.

Der Upgradekandidat stand auf 2019, der sysupgrade auf 2021 war problemlos. Erst jetzt funktionierte der upgrade auf 2023.

*Lösung* dieses Verhalten hört sich danach an, das ein Update auf 2021 vorher nicht durchgeführt wurde ... Das würde ich unter "wrong usage" abstempeln (oder so). Doch cool zu wissen, das dort eine überprüfung stattfindet (vielleicht können wir so uralte versionen auf lange offline nodes doch noch updaten)

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 2.) Überschrift 2


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


**Diese Anleitung ist wie immer ohne Gewähr. Für Anregungen und Tipps immer offen.**
