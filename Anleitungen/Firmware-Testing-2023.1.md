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
Nachtrag: das Gerät hatte gebootet aber das alte Image war wieder aktiv. Ein erneuter Versuch zeigte folgende Fehlermeldung.


root@ffhb-f09fc20f8752-UBNT-ERX-SFP:/tmp# sysupgrade gluon-ffhb-2023.1+bremen1-ubiquiti-edgerouter-x-sfp-sysupgrade.bin
Sat Sep 16 23:42:50 CEST 2023 upgrade: The device is supported, but the config is incompatible to the new image (1.1->1.0). Please upgrade without keeping config (sysupgrade -n).
Image check failed.

Also hier muß denn wohl die Konfig manuell neu eingegeben werden. oder Backup erstellen.

*Lösung* dieses Verhalten hört sich danach an, das ein Update auf 2021 vorher nicht durchgeführt wurde ... Das würde ich unter "wrong usage" abstempeln (oder so). Doch cool zu wissen, das dort eine überprüfung stattfindet (vielleicht können wir so uralte versionen auf lange offline nodes doch noch updaten)



ubnt-AC-Mesh, meine hatten vorher weisses List, jetzt sind sie wieder blau wie früher.
Archer C7-v2, irgenwann hörte das Blinken auf, es war nur die Netz LED an, jetz ist die Power LED, das Sternchen an daneben blinken die 2,4 und 5 GHz Antennensymbole wieder.

Ein Archer C7-v2 wollte nicht meshen, der Upgrade erfolgte problemlos im Konfigmodus. Reset lange drüchen, dann über das Webinterface http://192.168.1.1 Image laden und alles schick.

**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**

### 2.) Überschrift 2


**[------------------------------------------------------------------------------------------------------------------------- Zurück zum Inhalt:](#inhalt)**


**Diese Anleitung ist wie immer ohne Gewähr. Für Anregungen und Tipps immer offen.**
