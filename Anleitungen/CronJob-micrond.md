## Cronjob vs. micron.d /usr/lib/micron.d

In Gluon hat der bisher bekannte Cronjob ausgedient. Als Ersatz wurde **micrond** in Gluon implementiert.
Aber keine Sorge, die Änderungen sind minimal, kein edit crontab.

Für jeden Cron-micrond-Job wird eine eigene Steuerdatei angelegt. Wird dort keine Befehlssequenz hinterlegt, kann auch ein Programm oder Script aufgerufen werden.
Für einen Scriptaufruf ist ein extra Verzeichnis vorgesehen, wo nur der micrond als Systemuser Zugriff hat. Zum Testen kann/muss das Script dann aber unter /tmp ausprobiert werden.

### Beispiel einer Steuerdatei.
Im Verzeichnis `/usr/lib/micron.d/` soll eine Steuerdatei für den Linkcheck angelegt werden. Das Script Linkcheck prüft die Meshverbindungen des Routers im angegebenem Zeitintervall und startet den Router ggf. neu.
Mit  **vi / nano** die Datei "linkcheck" anlegen, der Inhalt ist
~~~
*/15 * * * * /lib/gluon/linkcheck/linkcheck.sh
~~~
Am Anfang die bekannten 5 Sternenchen mit der Zeitangabe, wie aus Cron bekannt. Hier */15 gleich alle 15 Minuten eine Aktion ausführen. Die Aktion ist hier, die Datei linkcheck.sh starten.

Hier sehen wir schon die nächste Neuerung. Im Verzeichnis `/lib/gluon/` wird ein weiteres Verzeichnis für unser Script angelegt.
Es soll der einfachheit halber wie unser Sript `linkcheck` heissen. In diesem Verzeichnis legen wir unser Script ab/an und ändern die Rechte auf Ausführbar.

Damit die Änderungen in micrond übernommen werden, ist ein `/etc/init.d/micrond restart` unbedingt erforderlich.

**Das ist schon alles.**

**Anderes Beispiel:** Ich möchte Zeitgesteruert, alle 2h den respond neu Starten, wenn dieser nicht mehr läuft. Das geht dann wie folgt.

Im Verzeichnis `/usr/lib/micron.d/` lege ich die Datei repondd2h an und schreibe folgendes hinein.

~~~
0 */2 * * * if ! [ $(pgrep autoupdater) ] ; then if ! [ $(pgrep respondd) ]; then /etc/init.d/gluon-respondd restart ;fi;fi
~~~
Zeitsteuerung alle 2h, prüfe obe der Autoupdater gerade läuft, wenn nein, prüfe ob respondd noch läuft, wenn nein, restart respondd

Alles schön in einer Zeile,  `/etc/init.d/micrond restart`  nicht vergessen.

---

Was mir aufgefallen war.
Als root darf ich die Datei linkcheck.sh nicht ausführen. Wie es als systemuser geht weis ich gerade nicht, deshalb kopiere ich sie tempörär nach /tmp und schon funktionierte es. Zur Kontrolle eigener Scripte, finde ich eine Info im Syslog nicht verkehrt. Dort kann ich dann mit logread sehen, ob mein Script ausgeführt wurde.

~~~
root@ffhb:~# ./lib/gluon/linkcheck/linkcheck.sh
-ash: ./lib/gluon/linkcheck/linkcheck.sh: not found
root@ffhb:~# cd /lib/gluon/linkcheck/
root@ffhb:/lib/gluon/linkcheck# ls
linkcheck.sh
root@ffhb:/lib/gluon/linkcheck# linkcheck.sh
-ash: linkcheck.sh: not found
~~~

Das Shellscript funktionierte bei mir nur, wenn in der ersten Zeile **#!/bin/sh** ohne Leerzeichen steht und die zweite Zeile nicht leer ist.

Mit einer kopierten Datei können die Zeilenumbrüche Probleme bereiten, immer im unix Format speichern.

Bitte gerne hier um weitere Beispiele Ergänzen.

