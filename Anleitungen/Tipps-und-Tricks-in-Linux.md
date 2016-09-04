## Tipps und Tricks in Linux

Als Freifunker kommen wir nicht um Linux herum. Mit dem Umstieg auf Windows 10 ändert sich so einiges in der gewohnten Bedienung. Bis wir die Einstellungen so hingefummelt haben, dass wir wieder vernünftig Arbeiten können, schauen wir doch lieber gleich einmal auf Linux.
Das wollten wir doch schon immer mal ausprobieren. Schnell sehen wir, das fast nichts so funktioniert, wie wir es aus der Windowswelt her kennen. Das macht nichts, denn auch an Windows haben wir jahrelang rumkonfiguriert bis es funktioniert.

Unter Linux kürzen wir dieses ab. Alle wichtigen Informationen bekommen wir aus https://wiki.ubuntuusers.de.
Damit uns Linux nicht frustriert, hier ein paar hilfreiche Tipps und Tricks.

Die folgen Tipps vereinfachen uns den Umgang mit Linux, was aber auch zur Folge hat, das wir ein bischen Winblöd werden.

## Inhalt:


[Alias](#inhalt_alias)

[SSH Login auf einem Router vereinfachen.](#inhalt_ssh-login-auf-einem-router-vereinfachen)

[Icons auf dem Desktop](#inhalt_icons-auf-dem-desktop)

[Klassische Startleiste](#inhalt_klassische-startleiste)

[IP v6 Adresse des angeschlossenen Routers](#inhalt_IP-v6-Adresse-des-angeschlossenen-Routers)

----


###Alias
Sich wiederholende Befehlsfolgen oder häufig benutze komplizierte Eingaben, verpacken wir als Alias.
https://wiki.ubuntuusers.de/alias/
Damit diese Alias Namen permanent sind, geben wir dieses direkt in ~/.bash_aliases ein. Diese Datei liegt versteckt in unserem Homeverzeichnich.

Beispiel: Bessere Lesbarkeit durch farbliche Ausgabe der Dateien über 'ls'

alias ls='ls --color=auto'
Nach dem Speichern und öffnen einer neuen Konsole (Terminalfenster) ist die Ausgabe mit 'ls' nun farblich dargestellt.


###SSH Login auf einem Router vereinfachen.
Siehe auch: http://wiki.bremen.freifunk.net/Anleitungen/SSH-Node-Verwaltung.

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

*Alternative Lösung:*
Wir legen im Ordner '~/.ssh/' eine Textdatei namens config an. In diese Datei kopieren wir folgende Zeilen.
~~~
#ssh (secure shell) configuration file
Host router1
    HostName ipv6-Adresse
    Port 22
    User root
    IdentityFile ~/.ssh/ffhb
~~~
Auf der Konsole mit 'SSH router1' sind wir sofort auf unserem Router.
Siehe: https://wiki.ubuntuusers.de/SSH/ oder 'man ssh_config'
~~~
Lokaler Benutzer: ~/.ssh/config
Systemweite Einstellung:  /etc/ssh/ssh_config
~~~

*Der Linuxprofi kopiert den Schlüssel wie folgt auf den Router:*
~~~
cat ~/.ssh/ffhb.pub | ssh root@fe80::6a72:51ff:fe04:f52e%en1 'cat >> /etc/dropbear/authorized_keys'
~~~
ffhb.pub war der öffentliche Schlüssel, den wir weiter oben generiert haben. Damit der Befehl auch tatsächlich auf dem Router ausgeführt wird, muss noch ein leztes Mal das Passwort eingegeben werden, aber anschließend nutzen alle Logins den Schlüssel. 

###Icons auf dem Desktop
Mit Icons auf dem Desktop sollte man Sparsam sein. Wer Icons auf dem Desktop haben möchte, kann wie folgt vorgehen. Bei Ubuntu liegt am linken Rand der Starter. Das erste Icon oben ist die Suchfunktion. Alle dort angezeigten Icons können direkt auf den Desktop gezogen werden.

###Klassische Startleiste
Nicht alle erfreuen sich an dem neuen Starter. Einfach über das Softwarecenter nach ClassicMenue Indicator' oder 'Startleiste' suchen, installieren, freuen.

###IP v6 Adresse des angeschlossenen Routers
Ist ja kein Problem, kann ich mal schnell googln. 1*10^6 Ergebnisse die nicht an eine Lücke in meinen Grundlagen denken. %en0 ist eth0, das sind Bezeichner für ein Interface aber nicht der Name.
Router IPv6 finden (MacOS und Linux)

Zuerst müssen wir die IPv6 Adresse des Routers finden. Dazu einfach im Terminal eingeben (sofern per WLAN mit Freifunknetz verbunden): (Vorweg: *%en1* ist das Interface, über das verbunden werden soll. Hier Ethernet 1....kann auch 0 oder 2 ... oder ein ganz anderes Interface sein. Im Zweifel "ifconfig" oder "ip addr show" eingeben und die Bezeichnung der Interfaces checken). Mein Interface ist z.B *enp0s25*

ping6 ff02::1%en1 gibt sonst ein "unknown Host" aus. Ausserdem wollen wir nicht alle Adressen aus dem Netz haben sondern die Ausgabe auf den ersten angeschlossenen Router begrenzen. Deshalb folgede Befehlszeile verwenden.
~~~
ping6 -c3 ff02::2%enp0s25 | grep -v DUP | grep fe80
~~~
Da ich mir das nicht merken kann, mach ich ein Alias davon. Beispiel Routerip oder kurz 'rip'.
~~~
alias rip='ping6 -c3 ff02::2%enp0s25 | grep -v DUP | grep fe80'
~~~
~~~
ffhb@FFHB:~$ rip
64 bytes from fe80::76ea:3aff:fee4:7374: icmp_seq=1 ttl=64 time=0.688 ms
64 bytes from fe80::76ea:3aff:fee4:7374: icmp_seq=2 ttl=64 time=0.782 ms
64 bytes from fe80::76ea:3aff:fee4:7374: icmp_seq=3 ttl=64 time=0.586 ms
ffhb@FFHB:~$
~~~


