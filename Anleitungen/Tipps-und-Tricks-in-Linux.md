## Tipps und Tricks in Linux

Als Freifunker kommen wir nicht um Linux herum. Mit dem Umstieg auf Windows 10 ändert sich so einiges in der gewohnten Bedienung. Bis wir die Einstellungen so hingefummelt haben, dass wir wieder vernünftig Arbeiten können, schauen wir doch lieber gleich einmal auf Linux.
Das wollten wir doch schon immer mal ausprobieren. Schnell sehen wir, das fast nichts so funktioniert, wie wir es aus der Windowswelt her kennen. Das macht nichts, denn auch an Windows haben wir jahrelang rumkonfiguriert bis es funktioniert.

Unter Linux kürzen wir dieses ab. Alle wichtigen Informationen bekommen wir aus https://wiki.ubuntuusers.de.
Damit uns Linux nicht frustriert, hier ein paar hilfreiche Tipps und Tricks.

Die folgen Tipps vereinfachen uns den Umgang mit Linux, was aber auch zur Folge hat, das wir ein bischen Winblöd werden.

## Inhalt:


[Alias](#inhalt_alias)

[SSH Login auf einem Router vereinfachen.](#inhalt_ssh-login-auf-einem-router-vereinfachen)

[Icons auf dem Desktop](#inhalt_icons_auf_dem_desktop)

[Klassische Startleiste](#inhalt_klassische_startleiste)

----


###Alias
Sich wiederholende Befehlsfolgen oder häufig benutze komplizierte Eingaben, verpacken wir als Alias.
https://wiki.ubuntuusers.de/alias/
Damit diese Alias Namen permanent sind, geben wir dieses direkt in ~/.bash_aliases ein. Diese Datei liegt versteckt in unserem Homeverzeichnich.

Beispiel: Bessere Lesbarkeit durch farbliche Ausgabe der Dateien über 'ls'

alias ls='ls --color=auto'
Nach dem Speichern und öffnen einer neuen Konsole (Terminalfenster) ist die Ausgabe mit 'ls' nun farblich dargestellt.


###SSH Login auf einem Router vereinfachen.
Siehe auch: http://wiki.bremen.freifunk.net/Anleitungen/SSH-Node-Verwaltung
Normalerweise öffnen wir eine SSH Verbindung in der Konsole mit 'SSH root@ipv6', dann Passwort oder Passphrase.
Das möchte ich vereinfachen.
Schritt 1. SSH Key ohne Passphrase anlegen.
Konsole öffen, mit 'cd ~./ssh'ind das Verzeichnis wechseln, wo unsere Keys abgelegt werden sollen.
Schlüsselpaar generieren mit: 'ssh-keygen -t rsa', als Namen z.B. ffhb angeben. Es werden nun ein privater Schlüssel ffhb und ein öffentlicher Schlüssel ffhb.pub im Verzeichnis ./ssh angelegt.
Den öffentlichen Schlüssel kopieren wir nun auf unseren Router.
Bisher bekanntes SSH Login auf den Router, wechseln nach 'cd /etc/dropbear'. Öfnnen der Datei authorized_keys mit vi 'vi authorized_keys'
Am Ende der Datei unseren Schlüssel kopieren und Speichern. Mit 'chmod 0600 authorized_keys' die Dateirechte setzen.
Auf unserem Rechner fügen wir in die Datei '~/.bash_aliases' unser neues Alias ein.
z.B. alias router='ssh root@ipv6' und speichern.
In einer neuen Konsole bekommen wir nur durch die Eingabe von 'router' sofort eine SSH Verbindung zu unserem Router.

###Icons auf dem Desktop
Mit Icons auf dem Desktop sollte man Sparsam sein. Wer Icons auf dem Desktop haben möchte, kann wie folgt vorgehen. Bei Ubuntu liegt am linken Rand der Starter. Das erste Icon oben ist die Suchfunktion. Alle dort angezeigten Icons können direkt auf den Desktop gezogen werden.

###Klassische Startleiste
Nicht alle erfreuen sich an dem neuen Starter. Einfach über das Softwarecenter nach ClassicMenue Indicator' oder 'Startleiste' suchen, installieren, freuen.









